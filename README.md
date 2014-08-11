Everything is OSM
=================

A super easy way to setup PostGIS with OpenStreetMap
[metro extracts](https://mapzen.com/metro-extracts/). More free time for your
OSM community!


First
-----

Install recent versions of these:

- [Vagrant](http://vagrantup.com/)
- [Virtualbox](https://www.virtualbox.org/)



Then
----

Choose which metro areas you want to use. Edit `variables.yml` so that the last
line contains a list of [metro extracts](https://mapzen.com/metro-extracts/)
that you want to include. For example:

    metro_extracts:
      - "austin"
      - "barcelona"
      - "portland"



Run:

    vagrant up


After it does its thing, a postgis database will be available at port 5432 with
osm data available for use! For example, you can use this string to connect to
the PostGIS database from Tilemill:

    dbname=osm host=localhost port=5432 user=osm password=osm


![Tilemill Screenshot](tilemill-screenshot.png)



Customize it
------------

The default database name, user, and password are "osm", but you can change them
by editing `variables.yml`.


If you want to connect to a different port than localhost:5432, just change the
value for the host parameter in the `Vagrantfile`. For example, to connect to
port 15342 instead, change this line:

  config.vm.network :forwarded_port, guest: 5432, host: 5432

to:

  config.vm.network :forwarded_port, guest: 5432, host: 15432
