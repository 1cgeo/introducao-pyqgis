## Iniciando no Console
O QGIS fornece um console Python integrado para a elaboração de scripts. Ele pode ser iniciado pelo comando CTRL+ALT+P ou pelo menu Complementos -> Terminal Python.

## Criando e lendo um projeto
Para criar um projeto, é necessário usar o método “write()”.

```python
projeto= QgsProject.instance()
projeto.write('c:/Users/nome/teste.qgs')
```
Para checar se o projeto foi realmente criado, feche e abra o QGIS e digite o código para carregar o projeto.

```python
projeto= QgsProject.instance()
projeto.read('c:/Users/nome/teste.qgs')
```
**1. Adicionando camadas vetoriais**
É necessário que se faça as seguintes importações:
```python
import os 
from qgis.core import (QgsVectorLayer)
```
Em situações como essa, o programador deve especificar os indicadores da fonte de dados da camada, como, por exemplo, o nome da camada e seu diretório.
```python
pontos_layer = "c:/Users/nome/pontos.shp"
vlayer = QgsVectorLayer(pontos_layer, "pontos layer", "ogr")
if not vlayer.isValid():
    print("Layer failed to load!")
else:
    QgsProject.instance().addMapLayer(vlayer)
```
O jeito mais fácil e rápido de abrir e exibir uma camada vetorial no QGIS é através do método **addVectorLayer()**.

```python
path_para_pontos_layer = "c:/Users/nome/pontos.shp"
vlayer = iface.addVectorLayer(path_para_pontos_layer, "pontos layer", "ogr")
if not vlayer:
  print("Layer failed to load!")
```
**2. Adicionando camadas raster**
Para acessar arquivos raster, a biblioteca GDAL é usada. Ele suporta uma ampla variedade de formatos de arquivo. Caso você tenha problemas para abrir alguns arquivos, verifique se o GDAL tem suporte para o formato específico (nem todos os formatos estão disponíveis por padrão).

```python
import os 
from qgis.core import (QgsVectorLayer)
path_to_tif = "C:/Users/nome/imagem.tif"
iface.addRasterLayer(path_to_tif, "layer name you like")
if not rlayer.isValid():
    print("Layer failed to load!")
```

## Table of Contents
É possível acessar as camadas carregadas no índice para recuperar informações. Pode-se utilizar o QgsProject da seguinte forma:

```python
layers = QgsProject.instance().mapLayers()
print(layers)
```

## Trabalhando com camadas raster
Uma camada raster consiste em uma ou mais bandas raster - conhecidas como rasters de banda única e multi bandas. Uma banda representa uma matriz de valores. Uma imagem colorida (por exemplo, foto aérea) é um raster que consiste em faixas vermelhas, azuis e verdes. Abaixo, seguem comandos importantes para a manipulação de rasters:

```python
path_to_tif = "C:/Users/nome/img.tif"
rlayer = QgsRasterLayer(path_to_tif, "imagem")
```
* Obter a resolução do raster:
```python
print(rlayer.width(), rlayer.height())
--------------------------------------
800 800
```
* Obter a extensão da camada em um QgsRectangle:
```python
print(rlayer.extent())
----------------------
<QgsRectangle: 290305.20000000001164153 7471848, 291265.20000000001164153 7472808>
```
* Obter a extensão da camada através de uma string:
```python
print(rlayer.extent().toString())
---------------------------------
290305.2000000000116415,7471848.0000000000000000,291265.2000000000116415,7472808.0000000000000000
```
* Obter o tipo do raster (0 = GrayOrUndefined (single band), 1 = Palette (single band), 2 = Multiband)
```python
print(rlayer.rasterType())
--------------------------
2
```
* Obter o número de bandas do raster:
```python
print(rlayer.bandCount())
-------------------------
8
```

## Trabalhando com camadas vetoriais
**1. Recuperando informações sobre atributos**

É possível recuperar informações sobre os campos associados a uma camada vetorial chamando fields() de um QgsVectorLayer:
```python
vlayer = QgsVectorLayer(pontos_layer, "pontos layer", "ogr")
for field in vlayer.fields():
    print(field.name(), field.typeName())
```
**2. Iterando sobre camada vetorial**

A iteração sobre os recursos em uma camada vetorial é uma das tarefas mais comuns. Abaixo está um exemplo de código básico simples para executar esta tarefa e mostrando algumas informações sobre cada recurso:
```python
pontos_layer = "c:/users/nome_do_usuario/pontos.shp"
vlayer = iface.addVectorLayer(pontos_layer, "pontos layer", "ogr")
layer = iface.activeLayer()
features = layer.getFeatures()
for feature in features:
    print("Feature ID: ", feature.id())
    geom = feature.geometry()
    geomSingleType = QgsWkbTypes.isSingleType(geom.wkbType())
    if geom.type() == QgsWkbTypes.PointGeometry:
        if geomSingleType:
            x = geom.asPoint()
            print("Point: ", x)
        else:
            x = geom.asMultiPoint()
            print("MultiPoint: ", x)
    elif geom.type() == QgsWkbTypes.LineGeometry:
        if geomSingleType:
            x = geom.asPolyline()
            print("Line: ", x, "length: ", geom.length())
        else:
            x = geom.asMultiPolyline()
            print("MultiLine: ", x, "length: ", geom.length())
    elif geom.type() == QgsWkbTypes.PolygonGeometry:
        if geomSingleType:
            x = geom.asPolygon()
            print("Polygon: ", x, "Area: ", geom.area())
        else:
            x = geom.asMultiPolygon()
            print("MultiPolygon: ", x, "Area: ", geom.area())
    else:
        print("Unknown or invalid geometry")
    attrs = feature.attributes()
    print(attrs)
    break
```
**3. Seleção de recursos**

Os recursos selecionados são normalmente destacados em uma cor diferente, para chamar a atenção do usuário sobre a seleção. Às vezes, pode ser útil selecionar recursos de forma programática ou alterar a cor padrão.

* Para selecionar todos os recursos, o selectAll()  pode ser usado:

```python
pontos_layer = "c:/users/nome_do_usuario/pontos.shp"
vlayer = iface.addVectorLayer(pontos_layer, "pontos layer", "ogr")
layer = iface.activeLayer()
layer.selectAll()
```

* Para selecionar usando uma expressão, use o selectByExpression():

```python
layer = iface.activeLayer()
layer.selectByExpression('"Class"=\'B52\' and "Heading" > 10 and "Heading" <70', QgsVectorLayer.SetSelection)
```

* Para alterar a cor de seleção, você pode usar o setSelectionColor() do QgsMapCanvas mostrado no exemplo a seguir:

```python
iface.mapCanvas().setSelectionColor( QColor("red") )
```
**4. Acessando atributos**

Os atributos podem ser referidos por seus nomes: 
```python
print(feature['name'])
```
Como alternativa, os atributos podem ser referenciados por índice:
```python
print(feature[1])
```
**5. Iterando sobre recursos selecionados**

Se for preciso iterar sobre um determinado subconjunto de recursos em uma camada, como aqueles dentro de uma determinada área, será necessário adicionar um objeto QgsFeatureRequest à getFeatures() chamada, como no exemplo abaixo:
```python
areaOfInterest = QgsRectangle(450290,400520, 450750,400780)
request = QgsFeatureRequest().setFilterRect(areaOfInterest)
for feature in layer.getFeatures(request):
    pass
```
**6. Adicionar recursos**

* **Adicionar campo:**
```python
from PyQt5.QtCore import QVariant
layer_provider=layer.dataProvider()
layer_provider.addAttributes([QgsField("Length",QVariant.Double)])
layer.updateFields()
print(layer.fields().names())
```
* **Deletar campo:**
```python
layer_provider.deleteAttributes([1])
layer.updateFields()
```

**7. Modificando camadas vetoriais**

Ao editar vetores dentro do QGIS, deve-se primeiro iniciar o modo de edição para uma camada particular, então fazer algumas modificações e finalmente confirmar (ou reverter) as mudanças, conforme o exemplo abaixo:
```python
from qgis.PyQt.QtCore import QVariant

feat1 = feat2 = QgsFeature(layer.fields())
fid = 99
feat1.setId(fid)
```
* Adicionando duas feições:
```python
layer.addFeatures([feat1,feat2])
```

* Deletando feição com ID específico:
```python
layer.deleteFeature(fid)
```

* Determinando nova geometria para uma função:
```python
geometry = QgsGeometry.fromWkt("POINT(7 45)")
layer.changeGeometry(fid, geometry)
```

* Atualizando um atributo (valor dado) a partir do índice de um campo:
```python
fieldIndex =1
value ='My new name'
layer.changeAttributeValue(fid, fieldIndex, value)
```

* Adicionando um campo:
```python
layer.addAttribute(QgsField("mytext", QVariant.String))
```

* Removendo um campo: 
```python
layer.deleteAttribute(fieldIndex)
```

**8. Criando camadas vetoriais**

Existem várias maneiras de gerar um conjunto de dados de camada vetorial, dentre elas:
* A classe **QgsVectorFileWriter**: Uma classe conveniente para gravar arquivos vetoriais em disco, usando uma chamada estática **writeAsVectorFormat()** para salvar toda a camada vetorial ou criando uma instância da classe e chamadas de emissão para addFeature().
* A classe **QgsVectorLayer**: um provedor de dados que interpreta o caminho fornecido (url) da fonte de dados para se conectar e acessar os dados. Ele pode ser usado para criar camadas temporários, baseados em memória ( memory) e conectar-se a conjuntos de dados OGR ( ogr), bancos de dados ( postgres, spatialite, mysql, mssql) e mais ( wfs, gpx, delimitedtext...).


## Manipulação de geometrias
Pontos, linestrings e polígonos que representam um recurso espacial são comumente chamados de geometrias. No QGIS, eles são representados com a **QgsGeometry** class.

Às vezes, uma geometria é, na verdade, uma coleção de geometrias simples. Essa geometria é chamada de multi-part geometry. Se ele contém apenas um tipo de geometria simples, nós o chamamos de multi-point, multi-linestring ou multi-polygon. As coordenadas das geometrias podem estar em qualquer sistema de referência de coordenadas (CRS). Ao buscar recursos de uma camada, as geometrias associadas terão coordenadas no CRS da camada.

**1. Construção de geometrias**
O PyQGIS permite a construção de diversas geometrias, por exemplo:
* **Coordenadas:**
```python
gPnt = QgsGeometry.fromPointXY(QgsPointXY(1,1))
print(gPnt)
gLine = QgsGeometry.fromPolyline([QgsPoint(1,1),QgsPoint(2,2)])
print(gLine)
gPolygon = QgsGeometry.fromPolygonXY([[QgsPointXY(1,1),QgsPointXY(2,2),QgsPointXY(2,1)]])
print(gPolygon)
```
* **WKT (Well Known Text):**
```python
geom = QgsGeometry.fromWkt("POINT(3,4)")
print(geom)
```
* **WKB (Well Known Binary):**
```python
g = QgsGeometry()
wkb = bytes.fromhex("010100000000000000000045400000000000001440")
g.fromWkb(wkb)
```

**2. Acesso à geometria**
É possível acessar uma geometria já conhecida (WKB), através do método wkbType():
```python
if gPnt.wkbType() == QgsWkbTypes.Point:
   print(gPnt.wkbType())
if gLine.wkbType() == QgsWkbTypes.LineString:
   print(gLine.wkbType())
if gPolygon.wkbType() == QgsWkbTypes.Polygon:
   print(gPolygon.wkbType())
```
**3. Operações e predicados de uma geometria**
O QGIS utiliza a biblioteca GEOS para operações de geometria avançadas, como predicados de geometria (**contains(), intersects()...**) e operações de conjunto (**combine(), difference()...**). Ele também pode calcular propriedades geométricas, como a área de polígonos ou comprimentos de polígonos ou linhas. Abaixo, encontra-se um exemplo que combina a iteração dos recursos em uma determinada camada e a execução de alguns cálculos geométricos com base em suas geometrias. O código a seguir assume que “layer” é um objeto QgsVectorLayer que possui o recurso polygon:

```python
layer = QgsProject.instance().mapLayersByName('countries')[0]

query = '"name" LIKE \'Z%\''
features = layer.getFeatures(QgsFeatureRequest().setFilterExpression(query))

for f in features:
   geom = f.geometry()
   name = f.attribute('NAME')
   print(name)
   print('Area: ', geom.area())
   print('Perimeter: ', geom.length())
--------------------------------------
Zambia
Area: 62.822790653431205
Perimeter: 50.65232014052552
Zimbabwe
Area: 33.41113559136521
Perimeter: 26.608288555013935
```
