# viewGeoreferencedJpg
View geo-referenced Jpeg on web.
https://gipong.github.io/view-georeferenced-jpg/

# Usage
For uploading to the website, you need to create a ZIP archive with .jpg, .jgwx(jgw) and .jpg.aux.xml in it.

After finishing the georeferencing process you will get two new files, they have file extension .jgwx and .jpg.aux.xml. These files hold the six coefficients of an affine transformation and projection information for the image. These information can help us to mapping your image to the correct location.

Test Data: [geojpg.zip](demo/geojpg.zip)

![img](demo/img.png)

# License
MIT

 
 
 最近在做一个gis web项目，项目基本使用leaflet，现在有一个需求是在地图上加载已经校准的图片(georeference)。图片是用arcgis校准的，在leaflet地图上插入一张图片很简单

var imageUrl = 'http://www.lib.utexas.edu/maps/historical/newark_nj_1922.jpg',
    imageBounds = [[40.712216, -74.22655], [40.773941, -74.12544]];
L.imageOverlay(imageUrl, imageBounds).addTo(map);

但是普通的图片(jpg、png)没有保存位置信息等，因此关键是需要通过图片计算得到真实的位置信息。用arcgis校准图片后，导出的文件（以jpg格式为例）除了图片文件，还有后缀为 .jgw的空间位置文件、后缀为jpg.aux.xml文件，这几个文件保存了图片的真实位置信息，我们的目标就是通过这两个文件换算得到真实的位置。
这是我在github上找到的一个例子：
这里写图片描述
只需要把校准文件(jpg、jgw、jpg.aux.xml)打包成一个文件即可。
