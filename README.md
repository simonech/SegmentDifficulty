# Segment Difficulty
Site that connects to Strava API and computes climbs difficulty.

It uses the following concepts:
* [Climb Difficulty](#climb-difficulty)
* [Strava API](#strava-api)
* [Encoded Polyline](#encoded-polyline)

## Climb difficulty

It's an attempt to identify with a number the difficulty of a climb.

There are various formula to compute this numbers:

### CLIMBBYBIKE-INDEX
```
(H*100/D)*2 + H^2/D + D/1000 + (T-1000)/100
```
Whereby: H = difference in height; D = distance in meters; T = top of mountain in meters.

The last part of the formula does only apply to mountains above 1000 meters.

More informations on [http://www.climbbybike.com/climb_difficulty.asp](http://www.climbbybike.com/climb_difficulty.asp)

### FIETS-index
```
[H^2 / D*10] + (T - 1000):1000 
```
Whereby: H = difference in height; D = distance in meters; T = top of mountain in meters

Developed by the Dutch cycling magazine [Fiets](http://www.fiets.nl/)

More informations on [http://www.bertevers.nl/Profiles/profiles.htm](http://www.bertevers.nl/Profiles/profiles.htm)

### Salite.ch

```
SUM(Gi*Gi*Di)
```
Whereby: Gi = grade of sector of the climb (%); Di = distance in km of the sector of the climb

More informations on [http://giriesalite.altervista.org/?p=2111](http://giriesalite.altervista.org/?p=2111)

### Gabriele Codifava

```
D = [ (d+400) / (10*d) ]* SUM [li * pi^2/10]
```

Whereby: d = overall difference in height (m); li = distance in km of the sector of the climb; Pi = grade of sector of the climb (%)

More informations on [http://digilander.libero.it/napobike/Codifava.htm](http://digilander.libero.it/napobike/Codifava.htm)


## Strava API
More information on the Strava API are available at [http://strava.github.io/api/](http://strava.github.io/api/).

A .NET implementation is avalable: [stravadotnet](https://github.com/inexcitus/stravadotnet)

##Encoded Polyline

The map of each segment is stored as encode polyline following Google Map [Encoded Polyline Algorithm Format](https://developers.google.com/maps/documentation/utilities/polylinealgorithm).

There is a [sample C# class for encoding/decoding](https://gist.github.com/shinyzhu/4617989).
