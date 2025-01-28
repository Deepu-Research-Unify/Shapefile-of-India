# Shapefile

import sys
from qgis.core import QgsApplication, QgsVectorLayer

# Set up the QGIS application
qgis_path = "C:/OSGeo4W/apps/qgis"  # Update this to the path where QGIS is installed
QgsApplication.setPrefixPath(qgis_path, True)
qgis_app = QgsApplication([], False)
qgis_app.initQgis()

# Load the shapefile
shapefile_path = "path/to/your/shapefile.shp"  # Update this to the path of your shapefile
layer = QgsVectorLayer(shapefile_path, "Shapefile Layer", "ogr")

# Check if the layer is valid
if not layer.isValid():
    print("Failed to load the layer!")
    sys.exit(1)

# Print some basic information about the shapefile
print(f"Layer name: {layer.name()}")
print(f"Number of features: {layer.featureCount()}")
print(f"CRS: {layer.crs().authid()}")

# Iterate over the features and print their attributes
for feature in layer.getFeatures():
    print(feature.attributes())

# Clean up and exit
qgis_app.exitQgis()
