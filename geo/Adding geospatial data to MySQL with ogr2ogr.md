Shape files can be loaded using the ogr2ogr CLI

ogr2ogr -f MySQL MySQL:dbname,host=localhost,user=username,password=pass,port=xxxx -a_srs "EPSG:28356" C:\projects\projects.shp -nln project_poly -update -overwrite -lco engine=MYISAM

Tables named geometry_columns and spatial_ref_system will be created if not already present

Before dropping a table with sptial data, the geometry column should be dropped.

ALTER TABLE geom DROP pt;


To create a spatial index

CREATE SPATIAL INDEX sp_index ON geom (g);
ALTER TABLE geom ADD SPATIAL INDEX(g);


DROP INDEX sp_index ON geom;
