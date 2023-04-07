# haversine formula

```c#
using System;
namespace distance_calculator.logic
{
	public class DistanceCalculator
	{
		private double _distanceInKilometers;
		public double DistanceInKilometers
		{
			get
			{ return _distanceInKilometers; }
			set
			{ _distanceInKilometers = value; } }

		public double CalculateDistance(double lat1, double long1, string name1, double lat2, double long2, string name2)
		{
            const double R = 6371e3; // radius of the earth

            double phiBRS = (Math.PI / 180) * lat1; // phi lat1
            double phiNYC = (Math.PI / 180) * lat2; // phi lat2

            double deltaPhi = (Math.PI / 180) * (lat2 - lat1); // delta phi
            double deltaLambda = (Math.PI / 180) * (long2 - long1); // delta lambda

            // calculate a
            double a = Math.Pow(Math.Sin(deltaPhi / 2.0), 2) + Math.Cos(phiBRS) * Math.Cos(phiNYC) * Math.Pow(Math.Sin(deltaLambda / 2.0), 2);

            // calculate c
            double c = 2 * Math.Atan2(Math.Sqrt(a), Math.Sqrt(1 - a));

            // calculate distance
            double d = R * c;

            // round distance and convert to kilometers
            DistanceInKilometers = Math.Round(d / 1000, 0);

            Console.WriteLine($"the distance in kilometers between {name1} and {name2} is {DistanceInKilometers}.");


            return _distanceInKilometers;
        }
	}
}
```
