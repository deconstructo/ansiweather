## Description

This is a slightly modified version of the original AnsiWeather script.


AnsiWeather is a Shell script for displaying the current weather conditions
in your terminal, with support for ANSI colors and Unicode symbols.

![AnsiWeather Screenshot][1]

Weather data comes from the `OpenWeatherMap` free weather API.



## Requirements

AnsiWeather requires the following dependencies:

- A command to fetch HTTP data such as FTP, cURL or wget
- [jq][2] (lightweight and flexible command-line JSON processor)
- [bc][3] (arbitrary precision numeric processing language), for doing float
  arithmetic



## Installation

After cloning the repository, simply invoke the script by typing:

	./ansiweather

AnsiWeather packages are available for:

- [OpenBSD][4]
- [NetBSD][5]
- [FreeBSD][6]
- [Debian][7]
- [Ubuntu][8]
- [Homebrew][9]
- [Haiku][10]
- [Gentoo][11]
- [Alpine Linux][12]



## Usage

### Synopsis

	ansiweather [-l location] [-u system] [-f days] [-F] [-a value]
 		    [-c value] [-s value] [-k key] [-i value] [-w value] 
       		    [-h value] [-H value] [-p value] [-d value] [-v]

### Options

	-l location
	        Specify location.
	
	-u system
	        Specify unit system to use ( metric or imperial ).
	
	-f days
	        Toggle forecast mode for the specified number of upcoming days.
	
	-F      Toggle forecast mode for the next five days.
	
	-a value
	        Toggle ANSI colors display ( true or false ).
	 
	-c value
	        Toggle text sky conditions display ( true or false ).
	
	-s value
	        Toggle icon sky conditions display ( true or false ).
	
	-k key  Specify OpenWeatherMap API key.
	
	-i value
	        Toggle UV Index display ( true or false ).
	
	-w value
	        Toggle wind data display ( true or false ).
	
	-h value
	        Toggle humidity data display ( true or false ).
	
	-H value
	        Toggle Feels like display ( true or false ).
	
	-p value
	        Toggle pressure data display ( true or false ).
	
	-d value
	        Toggle daylight data display ( true or false ).
	
	-v      Display version.

### Examples

Display forecast using metric units for the next five days (showing symbols
and daylight data) for Rzeszow, Poland:

	ansiweather -l "Rzeszow,PL" -u metric -s true -f 5 -d true



## Configuration

The default config file is ~/.ansiweatherrc. The environment variable
ANSIWEATHERRC can be set to override this. The following configuration
options (detailed below) are available and should be set according to
your location and preferences.

Example: `~/.ansiweatherrc`

	location:Rzeszow,PL
	fetch_cmd:ftp -V -o -
	units:metric
	show_daylight:true

The file `ansiweatherrc.example` contains all available configuration
variables.

### Location

Location format is `city,CC` where `CC` is a two-letter ISO 3166-1 alpha-2
country code. A list of country codes is available [here][13].
Alternatively, it's also possible to specify locations by their ID, a city
list is available [here][14].

In case no location is specified, AnsiWeather will fallback to the default
location.

Example: `Rzeszow,PL`

	location:Rzeszow,PL

### Fetch Command

Various tools can be used to fetch data: `curl`, `wget`, `ftp`.

Please note that `ftp` flags and options might differ among implementations
and versions, and the example provided here is known to work only on OpenBSD
and NetBSD.

Example: `curl -sf`

	fetch_cmd:curl -sf

Example: `wget -qO-`

	fetch_cmd:wget -qO-

Example: `ftp -V -o -`

	fetch_cmd:ftp -V -o -

Default: `curl -sf`

### System of Units

Both `metric` and `imperial` systems are supported.

	units:metric

Default: `metric`

### Display ANSI sequences

Toggle ANSI sequences display. Value can be either `true` (requires an ANSI
capable display) or `false`.

	ansi:true

Default: `true`

### Display symbols

Toggle Unicode symbols display. Value can be either `true` (requires a
Unicode capable display) or `false`.

	symbols:true

Default: `false`

Symbols can be configured or replaced by custom text using the following
configuration variables: `sun`, `moon`, `clouds`, `rain`, `fog`, `mist`,
`haze`, `snow`, `thunderstorm`.

### Display forecast

Show upcoming forecast for the next `N` days (for 0 <= N <= 7). `0` will
show standard output.

	forecast:5

Default: `0`

### Display wind / humidity / pressure

Toggle UV Index, wind, humidity, and/or pressure display. Values can be either
`true` or `false`.

	show_uvi:true
	show_wind:true
	show_humidity:true
	show_pressure:true

Default: `true`

### Display sunrise / sunset

Toggle daylight display. Value can be either `true` or `false`.

	show_daylight:false

Default: `false`

### Date and Time format

Configure date and time format display. See Unix date formatting docs
for details.

	dateformat:%a %b %d

Default: `%a %b %d`

	timeformat:%b %d %r

Default: `%b %d %r`

### OpenWeatherMap API key

Specify an OpenWeatherMap API key. By default AnsiWeather uses its own
key, but users can optionally get their own one by creating a free
[OpenWeatherMap account][15].

	api_key:85a4e3c55b73909f42c6a23ec35b7147



## License

AnsiWeather is released under the BSD 2-Clause license. See `LICENSE` file
for details.



## Author

AnsiWeather is developed by Frederic Cambus.

- Site: https://www.cambus.net



## Resources

GitHub: https://github.com/fcambus/ansiweather

[1]: https://www.cambus.net/files/ansiweather/ansiweather.png
[2]: https://stedolan.github.io/jq/
[3]: https://www.gnu.org/software/bc/
[4]: https://openports.pl/path/astro/ansiweather
[5]: https://pkgsrc.se/misc/ansiweather
[6]: https://www.freshports.org/misc/ansiweather
[7]: https://packages.debian.org/search?keywords=ansiweather
[8]: https://packages.ubuntu.com/search?keywords=ansiweather
[9]: https://formulae.brew.sh/formula/ansiweather
[10]: https://github.com/haikuports/haikuports/tree/master/app-misc/ansiweather
[11]: https://packages.gentoo.org/packages/app-misc/ansiweather
[12]: https://pkgs.alpinelinux.org/packages?name=ansiweather
[13]: https://www.statdns.com/cctlds/
[14]: https://bulk.openweathermap.org/sample/
[15]: https://home.openweathermap.org/users/sign_up
