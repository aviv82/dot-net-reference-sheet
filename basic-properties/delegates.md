# delegates

## class with delegate

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace linq_and_delegates_practice
{
    public class Exec
    {
        public delegate bool FindMovie(Movie movie);

        public static List<Movie> GetMovies(List<Movie> movies, FindMovie del)
        {
            List<Movie> result = new List<Movie>();

            foreach (Movie movie in movies)
            {
                if (del(movie))
                {
                    result.Add(movie);
                };
            }

            return result;
        }
    }

}
```

## implementation

```c#
// use delegates

Exec _exec = new Exec();



List<Movie> selectMoviesByYear = Exec.GetMovies(movies, delegate (Movie movie) {
    return movie.Title.Contains("g");
});

foreach (Movie movie in selectMoviesByYear)
{
    Console.WriteLine(movie.Title);
}

List<Movie> financeMovies = Finance.GetMoviesByBudget(movies, delegate (Movie movie) { return movie.GrossBudgetInMillions < 2; });

foreach (Movie movie in financeMovies)
{
    Console.WriteLine(movie.Title);
}

List<Movie> directorMovie = Finance.GetMoviesByBudget(movies, delegate (Movie mov) { return mov.Director == "Christopher Nolan"; });

foreach (Movie movie in directorMovie)
{
    Console.WriteLine(movie.Title);
}
```
