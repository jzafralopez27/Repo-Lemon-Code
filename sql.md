1 - Listar las pistas (tabla Track) con precio mayor o igual a 1€
select Track.Name from dbo.Track where UnitPrice >= 1

2 - Listar las pistas de más de 4 minutos de duración
select Track.Name from dbo.Track where Milliseconds/60000 > 4;

3 - Listar las pistas que tengan entre 2 y 3 minutos de duración
select Track.Name from dbo.Track where Milliseconds/60000 between 2 and 3;

4 - Listar las pistas que uno de sus compositores (columna Composer) sea Mercury
select Track.Name from dbo.Track where Composer like '%Mercury%';

5 - Calcular la media de duración de las pistas (Track) de la plataforma
select AVG(Milliseconds) from dbo.Track;

6 - Listar los clientes (tabla Customer) de USA, Canada y Brazil
select CustomerId,FirstName,LastName from dbo.Customer where Country like 'Brazil' or Country like 'USA' or Country like 'Canada';

7 - Listar todas las pistas del artista 'Queen' (Artist.Name = 'Queen')
select Track.Name from dbo.Track join Album on Track.AlbumId = Album.AlbumId join Artist on Album.ArtistId = Artist.ArtistId where Artist.Name = 'Queen';

8 - Listar las pistas del artista 'Queen' en las que haya participado como compositor David Bowie
select Track.Name from dbo.Track join Album on Track.AlbumId = Album.AlbumId join Artist on Album.ArtistId = Artist.ArtistId where Track.Composer like '%David Bowie%' and Track.Composer like '%Queen%';

9 - Listar las pistas de la playlist 'Heavy Metal Classic'
select Track.Name from dbo.Track join PlaylistTrack on Track.TrackId = PlaylistTrack.TrackId join Playlist on PlaylistTrack.PlaylistId = Playlist.PlaylistId where Playlist.Name = 'Heavy Metal Classic';

10 - Listar las playlist junto con el número de pistas que contienen
select Playlist.Name,COUNT(Track.Name) from dbo.Track join PlaylistTrack on Track.TrackId = PlaylistTrack.TrackId join Playlist on PlaylistTrack.PlaylistId = Playlist.PlaylistId group by Playlist.Name;

11 - Listar las playlist (sin repetir ninguna) que tienen alguna canción de AC/DC
select Playlist.Name from Playlist join PlaylistTrack on Playlist.PlaylistId = PlaylistTrack.PlaylistId join dbo.Track on PlaylistTrack.TrackId = Track.TrackId where Track.Composer = 'AC/DC' group by Playlist.Name;

12 - Listar las playlist que tienen alguna canción del artista Queen, junto con la cantidad que tienen
select Playlist.Name,COUNT(Track.Name) as Total from Playlist join PlaylistTrack on Playlist.PlaylistId = PlaylistTrack.PlaylistId join dbo.Track on PlaylistTrack.TrackId = Track.TrackId where Track.Composer = 'Queen' group by Playlist.Name;

13 - Listar las pistas que no están en ninguna playlist
select Track.Name from dbo.Track left join PlaylistTrack ON Track.TrackId = PlaylistTrack.TrackId where PlaylistTrack.PlaylistId is null group by Track.Name;

14 - Listar los artistas que no tienen album
select Artist.Name from dbo.Artist left join Album on Artist.ArtistId = Album.ArtistId where Album.AlbumId is null;

15 - Listar los artistas con el número de albums que tienen
select Artist.Name,COUNT(Album.Title) from Artist left join Album on Artist.ArtistId = Album.ArtistId group by Artist.Name;

// Opcionales //

1 - Listar las pistas ordenadas por el número de veces que aparecen en playlists de forma descendente
select Track.Name,COUNT(PlaylistTrack.PlaylistId) as Times from Track left join PlaylistTrack on Track.TrackId = PlaylistTrack.TrackId group by Track.Name order by Times desc;

2 - Listar las pistas más compradas (la tabla InvoiceLine tiene los registros de compras)
select Track.Name, SUM(InvoiceLine.Quantity) as Ventas from Track join InvoiceLine on Track.TrackId = InvoiceLine.TrackId group by Track.Name order by Ventas desc;

3 - Listar los artistas más comprados
select Artist.Name, SUM(InvoiceLine.Quantity) as Ventas from Artist join Album on Artist.ArtistId = Album.ArtistId join Track on Album.AlbumId = Track.AlbumId join InvoiceLine on Track.TrackId = InvoiceLine.TrackId group by Artist.Name order by Ventas DESC;

4 - Listar las pistas que aún no han sido compradas por nadie
select Track.Name from Track left join InvoiceLine on Track.TrackId = InvoiceLine.TrackId where InvoiceLine.InvoiceLineId is Null;

5 - Listar los artistas que aún no han vendido ninguna pista
select Artist.Name from Artist left join Album on Artist.ArtistId = Album.ArtistId left join Track on Album.AlbumId = Track.AlbumId left join InvoiceLine on Track.TrackId = InvoiceLine.TrackId where InvoiceLine.InvoiceLineId is null group by Artist.Name;

** De las consultas opcionales 4 y 5 no estoy muy seguro, sobre todo de la 5... por ejemplo, me aparece Metallica
cuando está la consulta 3 sale como de los artistas más vendidos... **
