#Install opengeo on Ubuntu on Rackspace Cloud server#


Opengeo is a bundled suite of applications for making custom maps & dpoing spatial processing. Includes

- **geoserver**: an excellent opensource map server
- **postgis**: an extension for postgresql database tohat offers advanced spatial processing & spatial data storage
- **Openlayers**: an excellent javascript framework for web mapping
- **GeoExt**: Extentsion to Ext javascript framework
- **geowebcache**: image tile cache, seed-on-demand & pre-seeding. Can also proxy map tiles from Google Maps, OSM etc)
- ... some magic & glue to bring it all together

<br/>
I've used a 512Mb server for HROK, this is enough for development, but for production servers the geoserver (java/Tomcat) and postgresql processing can be significant... drawing maps, spatial calculations etc, so I'd usually go to 2048Mb sized cloud server. 

<br/>
## Install Steps ##

<br/>
Grab the OpenGeo GPG Apt key

    wget -qO- http://apt.opengeo.org/gpg.key | apt-key add -

<br/>
Add the APT repository

    echo "deb http://apt.opengeo.org/suite/v3/ubuntu lucid main" >> /etc/apt/sources.list

<br/>
Update APT & install opengeo-suite

    apt-get update
    apt-get install opengeo-suite

<br/>
Browse to the geoserver admin to make sure it all worked

    http://xxx.xxx.xxx.xxx:8080/geoserver/index.html
