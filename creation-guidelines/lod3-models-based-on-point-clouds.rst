Tutorial LoD3 modelling
=======================

Requirements
------------

- `SketchUp Make 2017 (or newer/Pro) <https://www.sketchup.com/download/all>`_
- `CityEditor plugin <https://extensions.sketchup.com/de/content/cityeditor-2>`_

Input data
----------
Within this workflow pipeline following datasets were used:

- XYZ (simplified pointcloud =< 150 000 points to assure SketchUp efficiency)
- CityGML (selected input LoD1 to simplify modelling tasks later on)
- *possibly* already created adjacent LoD3 buildings

Data import
-----------

After installation and activation of CityEditor plugin and SketchUp the import of datasets is possible.

Select *CityEditor Importer* to run the importing window.

.. image:: resources/1.jpg
    :width: 100%

Click on the building icon at the top-right to add CityGML objects (formats like .xml, .gml, .shp, .dxf, and other avalaible). It is possible to add single files (under *File...*) or several (*Directory...*).

After successful selection buildings should be listed within the grey area of a window.

A similar operation should be done for adding point cloud. The plugin allows to add point clouds **only in .xyz or .csv format** and **number of points should be lower than 200 000** (for **best performance =<150 000** were used within this tutorial). Instead of building an icon you should choose a small squares icon, second from bottom-right. Again, there is an option to add a single object or a whole directory.

.. image:: resources/2.jpg
    :width: 100%

Click *Next*. Then, in section *Preparsing* click *Next* again to pre-validate your data. Depending on data it can take to several minutes, the process can be tracked in the process bar.
Preparsing results contain information about the model bounding box, width, height and list of errors. At this point, you can check whether your data are in a proper coordinate system and roughly estimate the position of your model.

Click *Next* to proceed.

.. image:: resources/3.jpg
    :width: 100%

*Options* window contains 3 sections: *Buildings/CityGML*, *Pointcloud* and *Expert Options*. If more types of datasets are chosen the sections expand accordingly.

Tick the *Highest available* to pick all available LoD within our dataset (in this example number 1 is sufficient for building in LoD1).

To load an appearance of buildings select *Appearance Theme* - in this example there are no textures available.

*Automatic Roof Texturing/Coloring* is set to *None*. However, it is possible to automatically colorize (*Colorize*) Roof surfaces or put a texture (*Texturiz*) based on WMS (like OSM) and buildings coordinates at the rooftop. In the creation of LoD3, it is mostly not relevant.

To import attributes of objects tick *Import Attributes*.

.. image:: resources/4.jpg
    :width: 100%

Go to the Pointcloud section now. Here you can select your preferences regarding point cloud representation - plus or cube (*Point Representation*).

Moreover, Point Size in units of a map (meters in this example - depends on the coordinate system of input data) can be set as well as colour (by Height or Natural) and Voxel Size.

Values presented in a screenshot assure good performance and minimize further simplification of point cloud by a plugin.
More about Voxel : (`Voxel on Wikipedia <https://en.wikipedia.org/wiki/Voxel>`_, `CityEditor Manual <https://www.3dis.de/files/cityeditor/downloads/CityEditor_en.pdf>`_
)


.. image:: resources/5.jpg
    :width: 100%

*Expert Options* bar is relevant only if you want to import higher detailed buildings or materials. Also, there is an option to validate GML Namespaces at this point. The default values are sufficient to proceed.

Now, you can click *Next* to continue.

.. image:: resources/6.jpg
    :width: 100%

In *Coordinates* window you can check your coordinate system (*Coordinate System* section) or integrate your data with already existing SketchUp project (*Model Integration*) and set timezone (*Timezone*). In this example, the plugin reads everything automatically.

Click *Next* to continue.

.. image:: resources/7.jpg
    :width: 100%

The next window allows us to filter out only relevant data from the whole dataset simply by *Region* or *Gridding* definition. This part also can serve as a preview of data extend thanks to the option of base map selection (*Map Source*), here OpenStreetMap selected.
Filtering at this point is not recommended - it is better to prepare data before importing it to SketchUp.

Click *Next* to continue.

.. image:: resources/8.jpg
    :width: 100%

In the following window, you can specify a saving path. You can tick the option below to save log file as text which can be found in the same folder.

Click *Next* and then *Finish* to load data.

.. image:: resources/9.jpg
    :width: 100%

Steps performed by the plugin are displayed in a window.

.. image:: resources/10.jpg
    :width: 100%


Modelling
---------

LoD1 building is imported to assure ground level. LoD1 walls and roof mostly are not relevant while creating LoD3 and thus can be erased at the beginning.

To easily operate on a building, you can explode a group(*Right Click-> Explode*). However, before doing that it is relevant to copy attributes from a model (*Right Click-> Attributes -> Copy to Clipboard*). At the end of objects modeling, they should be merged in a group and attributes can be reassigned.

.. image:: resources/11.jpg
    :width: 100%
.. image:: resources/12.jpg
    :width: 100%

Further modelling should be done with the aid of a point cloud, an external preview of a point cloud and photos or mesh from Google Earth Pro.
Not every part of a building has to be done from scratch. A wide repository is available on SketchUp Warehouse where tiny and big elements can be downloaded.

Moreover, the SketchUp community (SketchUp extensions) offers a lot of plugins tailored to the user's needs. One of the most interesting for building modelling:
- *Chris Fullmer Tools, Component Onto Faces*
- *bit tools 1001*
- *Weld*


Example for window creation
^^^^^^^^^^^^^^^^^^^^^^^^^^^

To create a detailed window you can create by yourself or use the SketchUp Warehouse. Here, I would like to present an example with a window from SketchUp Warehouse.

Go to a web page of SketchUp Warehouse and find a window by typing "window" in the command line. Remember to select the right version of SketchUp (here, SketchUp 2017).

After that, you can simply open the downloaded file and select whole object and use ctrl+c and paste it into an open building project using ctrl+v.

.. image:: resources/13.jpg
    :width: 100%

Mostly users create such objects as Components or Groups. To assure that the local axis of the imported window is in the right place you can explode window Group/Component (similar to with building in LoD1 before).
After that, you can create Component again and set the local axis - remember that window should later align with a wall or roof on which you will place it.

.. image:: resources/14.jpg
    :width: 100%

If an axis was properly assigned and a wall is created it is now possible to quickly place the window on the wall. Select the surface and then component and go to *Extensions-> Chris Fullmer Tools, Component Onto Faces*. Thanks to that window is aligned with a wall.

Now you can move and scale it with native *Move* and *Scale* tool. In order to cut an opening for a window the easiest way is to draw a polygon bounding the component and erase a face inside this polygon.

.. image:: resources/15.jpg
    :width: 100%

The current object is conformant with SketchUp and aligns the bounding surface properly. However, now it is important to make the window a semantic, CityGML Window.

To do that *Right Click-> [CityEditor.jpg GroupType ->Window*. Then you have to specify what kind of opening is that -  *Right Click-> [CityEditor.jpg Opening Boundary Surface Type ->WallSurface* and at what level of deitails *Right Click-> [CityEditor.jpg LoD -> 3* as well as *Right Click-> [CityEditor.jpg Surface Type ->lodXMultiSurface*.

That is why all groups should be also grouped within the SketchUp project(Windows, BuildingInstallations, etc.). Surfaces like walls, roofs, and ground do not have to be grouped as they can be assigned from a surface position.

.. image:: resources/16.jpg
    :width: 100%


Closing the model
^^^^^^^^^^^^^^^^^

The similar steps have to be done for each new object within SketchUp. To assure CityGML validity each surface has to be assigned to specific CityGML configuration. Useful website: `sig3d.org <http://en.wiki.quality.sig3d.org/index.php/Modeling_Guide_for_3D_Objects_-_Part_2:_Modeling_of_Buildings_(LoD1,_LoD2,_LoD3)>`_

.. image:: resources/17.jpg
    :width: 100%

Having all objects created and assigned, you can now collect them into one Building object by selecting all items and grouping them. To the group object you can add attributes (*Right Click-> Attributes -> Edit Attributes*) or paste attributes copied before from LoD1 building (*Right Click-> Attributes -> Paste Attributes*).

After that, it is important to erase all automatic IDs created within a group to avoid redundant IDs within a model and in comparison with other buildings.
T do that, go to *Attribute Manager* in the main plugin bar and click *Refresh*. You can control your added attributes and check whether the plugin has added something.

Attributes like *PolygonID* and *LinearRingID* should be erased before export into CityGML.

.. image:: resources/18.jpg
    :width: 100%


Data export
-----------

To export files, you have to select an icon with green arrow nad GML sign and select the folder to save it.

Then, the CityGML Export window is opened. You can tick here *Logging* to see logs while exporting.

.. image:: resources/20.jpg
    :width: 100%

In *CityGML Options* section you make further configuration of exported CityGML. Very important is to type in *Appearance Theme* name and remember it in case of further importing it to citydb or other environments.

As ID for specific Polygons, LinearRings were deleted we have to create them again by ticking option *Generate IDs for all elements* this assures uniqueness. Just to be sure, we can select also *Check and correct IDs* thanks to that exporting algorithm will repair issues if they will appear.

.. image:: resources/21.jpg
    :width: 100%

Within section *Coordinate System* you can check whether the coordinate system is appropriate and additionally you can apply *Yaw* (offset). In *Textures* tab you can check currently exporting materials and saving folder for those.

To continue select *Start Export*.

.. image:: resources/22.jpg
    :width: 100%
