# linq

## of type

```c#
// of type

IList values = new ArrayList();

foreach (Movie movie in movies)
{
    values.Add(movie.Year);
    values.Add(movie.RunTimeInMinutes);
}

List<string> years = values.OfType<string>().ToList();
foreach (string year in years)
{ Console.WriteLine( "year " + year); }

List<int> minutes = values .OfType<int>().ToList();

foreach (int minute in minutes)
{
    Console.WriteLine("minutes" + minute);
}
```

## group by / to lookup

```c#

// group by tolookup

var _sameDirector = movies.GroupBy(movies => movies.Director);

foreach (var movie in _sameDirector)
{
    Console.WriteLine("diretor:" + movie.Key);
    foreach (Movie movie2 in movie)
    {
        Console.WriteLine(movie2.Director + ": " + movie2.Title);
    }
}

var sameYear = movies.ToLookup(movies => movies.Year);

foreach (var movie in sameYear)
{
    Console.WriteLine("year: " + movie.Key);
    foreach (Movie movie2 in movie)
    {
        Console.WriteLine(movie2.Year + ": " + movie2.Title);
    }
}

```

## join

```c#
// join

var actor_movies = movies.Join(actors, movie=> movie.ActorId, actor=> actor.ActorId, (movie, actor) =>
new { MovieYear = movie.Year, MovieTitle = movie.Title, ActorName = actor.Name });

foreach (var actor in actor_movies)
{
    Console.WriteLine(actor.MovieTitle);
    Console.WriteLine(actor.MovieYear);
    Console.WriteLine(actor.ActorName);
}

List<ActorMovie> actorsInmovies = movies.Join(actors, movie=>movie.ActorId, actor=> actor.ActorId, (movie, actor) =>
new ActorMovie { ActorName = actor.Name, MovieTitle = movie.Title, MovieYear = movie.Year }).ToList();
foreach (var actor in actorsInmovies)
{
    Console.WriteLine(actor.MovieTitle);
    Console.WriteLine(actor.MovieYear);
    Console.WriteLine(actor.ActorName);
}
```

### resources

- [linq samples](https://github.com/dotnet/try-samples/tree/main/101-linq-samples/src)
