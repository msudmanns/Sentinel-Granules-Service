# Sentinel Granule Service

This is a web application, which returns the name of the UTM granules for sentinel 2 given a point, line or polygon. The input is a geometry defined in WKT (well-known-text). It performs a simple intersection in PostGIS.

Be careful as this web application is experimental.

# Installation

Create a spatial database in PostgreSQL and insert the table, which is defined in the *.sql file.

Copy all *.py and config files to your web server. Note: You need python 2 and a web server.

You specify in the configuration file whether it should check the given WKT strings against a set of regular expressions to limit the type of requests (e.g. for security or performance reasons). The comparison is conducted with a simple regex match. You can use this great web application to build the regex: http://pythex.org/

An emty regex setting will be treated as "no check".

# Usage

Once you have set up the web application, you can call it, e.g., using your browser with something like this:

````
https://localhost/cgi-bin/S2-granules.py?wkt='POINT (10 10)'
https://localhost/cgi-bin/S2-granules.py?wkt=POINT (10 10)
https://localhost/cgi-bin/S2-granules.py?wkt="POINT (10 10)"
````

It also works with lines and polygons:

````
https://localhost/cgi-bin/S2-granules.py?wkt='LINESTRING (10 10, 20 20)'
https://localhost/cgi-bin/S2-granules.py?wkt='POLYGON ((35 10, 45 45, 15 40, 10 20, 35 10),(20 30, 35 35, 30 20, 20 30))'

````

It will be extended with multi-geometries soon.

# Contact

Author: Martin Sudmanns

Web: http://uni-salzburg.at/zgis/sudmanns

