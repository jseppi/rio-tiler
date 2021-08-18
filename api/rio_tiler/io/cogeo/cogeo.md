# Module rio_tiler.io.cogeo

rio_tiler.io.cogeo: raster processing.

None

## Classes

### COGReader

```python3
class COGReader(
    filepath: str,
    dataset: Union[rasterio.io.DatasetReader, rasterio.io.DatasetWriter, rasterio.io.MemoryFile, rasterio.vrt.WarpedVRT] = None,
    tms: morecantile.models.TileMatrixSet = <TileMatrixSet title='Google Maps Compatible for the World' identifier='WebMercatorQuad'>,
    minzoom: int = None,
    maxzoom: int = None,
    colormap: Dict = None,
    nodata: Union[float, int, str, NoneType] = None,
    unscale: Union[bool, NoneType] = None,
    resampling_method: Union[rasterio.enums.Resampling, NoneType] = None,
    vrt_options: Union[Dict, NoneType] = None,
    post_process: Union[Callable[[numpy.ndarray, numpy.ndarray], Tuple[numpy.ndarray, numpy.ndarray]], NoneType] = None
)
```

#### Attributes

| Name | Type | Description | Default |
|---|---|---|---|
| filepath | str | Cloud Optimized GeoTIFF path. | None |
| dataset | rasterio.io.DatasetReader or rasterio.io.DatasetWriter or rasterio.vrt.WarpedVRT | Rasterio dataset. | None |
| tms | morecantile.TileMatrixSet | TileMatrixSet grid definition. Defaults to `WebMercatorQuad`. | `WebMercatorQuad` |
| minzoom | int | Overwrite Min Zoom level. | None |
| maxzoom | int | Overwrite Max Zoom level. | None |
| colormap | dict | Overwrite internal colormap. | None |
| nodata | int or float or str | Global options, overwrite internal nodata value. | None |
| unscale | bool | Global options, apply internal scale and offset on all read operations. | None |
| resampling_method | rasterio.enums.Resampling | Global options, resampling method to use for read operations. | None |
| vrt_options | dict | Global options, WarpedVRT options to use for read operations. | None |
| post_process | callable | Global options, Function to apply after all read operations. | None |

#### Ancestors (in MRO)

* rio_tiler.io.base.BaseReader
* rio_tiler.io.base.SpatialMixin

#### Descendants

* rio_tiler.io.cogeo.GCPCOGReader

#### Instance variables

```python3
center
```

Dataset center + minzoom.

```python3
spatial_info
```

Return Dataset's spatial info.

#### Methods

    
#### close

```python3
def close(
    self
)
```

    
Close rasterio dataset.

    
#### feature

```python3
def feature(
    self,
    shape: Dict,
    dst_crs: Union[rasterio.crs.CRS, NoneType] = None,
    shape_crs: rasterio.crs.CRS = CRS.from_epsg(4326),
    max_size: int = 1024,
    indexes: Union[Sequence[int], int, NoneType] = None,
    expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read part of a COG defined by a geojson feature.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| shape | dict | Valid GeoJSON feature. | None |
| dst_crs | rasterio.crs.CRS | Overwrite target coordinate reference system. | None |
| shape_crs | rasterio.crs.CRS | Input geojson coordinate reference system. Defaults to `epsg:4326`. | `epsg:4326` |
| max_size | int | Limit the size of the longest dimension of the dataset read, respecting bounds X/Y aspect ratio. Defaults to `1024`. | `1024` |
| indexes | sequence of int or int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `COGReader.part` method. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### get_zooms

```python3
def get_zooms(
    self,
    tilesize: int = 256
) -> Tuple[int, int]
```

    
Calculate raster min/max zoom level.

    
#### info

```python3
def info(
    self
) -> rio_tiler.models.Info
```

    
Return COG info.

    
#### metadata

```python3
def metadata(
    self,
    pmin: float = 2.0,
    pmax: float = 98.0,
    **kwargs: Any
) -> rio_tiler.models.Metadata
```

    
Return Dataset's statistics and info.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| pmin | float | Histogram minimum cut. Defaults to `2.0`. | `2.0` |
| pmax | float | Histogram maximum cut. Defaults to `98.0`. | `98.0` |

**Returns:**

| Type | Description |
|---|---|
| rio_tile.models.Metadata | Dataset statistics and metadata. |

    
#### part

```python3
def part(
    self,
    bbox: Tuple[float, float, float, float],
    dst_crs: Union[rasterio.crs.CRS, NoneType] = None,
    bounds_crs: rasterio.crs.CRS = CRS.from_epsg(4326),
    max_size: int = 1024,
    indexes: Union[int, Sequence, NoneType] = None,
    expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read part of a COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| bbox | tuple | Output bounds (left, bottom, right, top) in target crs ("dst_crs"). | None |
| dst_crs | rasterio.crs.CRS | Overwrite target coordinate reference system. | None |
| bounds_crs | rasterio.crs.CRS | Bounds Coordinate Reference System. Defaults to `epsg:4326`. | `epsg:4326` |
| max_size | int | Limit the size of the longest dimension of the dataset read, respecting bounds X/Y aspect ratio. Defaults to `1024`. | `1024` |
| indexes | sequence of int or int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `rio_tiler.reader.part` function. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### point

```python3
def point(
    self,
    lon: float,
    lat: float,
    indexes: Union[Sequence[int], int, NoneType] = None,
    expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> List
```

    
Read a pixel value from a COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| lon | float | Longitude. | None |
| lat | float | Latittude. | None |
| indexes | sequence of int or int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `rio_tiler.reader.point` function. | None |

**Returns:**

| Type | Description |
|---|---|
| list | Pixel value per band indexes. |

    
#### preview

```python3
def preview(
    self,
    indexes: Union[Sequence[int], int, NoneType] = None,
    expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Return a preview of a COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| indexes | sequence of int or int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `rio_tiler.reader.preview` function. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### read

```python3
def read(
    self,
    indexes: Union[Sequence[int], int, NoneType] = None,
    expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read the COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| indexes | sequence of int or int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `rio_tiler.reader.read` function. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### stats

```python3
def stats(
    self,
    pmin: float = 2.0,
    pmax: float = 98.0,
    hist_options: Union[Dict, NoneType] = None,
    **kwargs: Any
) -> Dict[str, rio_tiler.models.ImageStatistics]
```

    
Return bands statistics from a COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| pmin | float | Histogram minimum cut. Defaults to `2.0`. | `2.0` |
| pmax | float | Histogram maximum cut. Defaults to `98.0`. | `98.0` |
| hist_options | dict | Options to forward to numpy.histogram function. | None |
| kwargs | optional | Options to forward to `rio_tiler.reader.stats`. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageStatistics | bands statistics. |

    
#### tile

```python3
def tile(
    self,
    tile_x: int,
    tile_y: int,
    tile_z: int,
    tilesize: int = 256,
    indexes: Union[Sequence[int], int, NoneType] = None,
    expression: Union[str, NoneType] = None,
    tile_buffer: Union[int, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read a Web Map tile from a COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| tile_x | int | Tile's horizontal index. | None |
| tile_y | int | Tile's vertical index. | None |
| tile_z | int | Tile's zoom level index. | None |
| tilesize | int | Output image size. Defaults to `256`. | `256` |
| indexes | int or sequence of int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `COGReader.part` method. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and tile spatial info. |

    
#### tile_exists

```python3
def tile_exists(
    self,
    tile_z: int,
    tile_x: int,
    tile_y: int
) -> bool
```

    
Check if a tile is intersets the dataset bounds.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| tile_x | int | Tile's horizontal index. | None |
| tile_y | int | Tile's vertical index. | None |
| tile_z | int | Tile's zoom level index. | None |

**Returns:**

| Type | Description |
|---|---|
| bool | True if the tile is intersets the dataset bounds. |

### GCPCOGReader

```python3
class GCPCOGReader(
    filepath: str,
    src_dataset: Union[rasterio.io.DatasetReader, rasterio.io.DatasetWriter, rasterio.io.MemoryFile, rasterio.vrt.WarpedVRT] = None,
    tms: morecantile.models.TileMatrixSet = <TileMatrixSet title='Google Maps Compatible for the World' identifier='WebMercatorQuad'>,
    minzoom: int = None,
    maxzoom: int = None,
    colormap: Dict = None,
    nodata: Union[float, int, str, NoneType] = None,
    unscale: Union[bool, NoneType] = None,
    resampling_method: Union[rasterio.enums.Resampling, NoneType] = None,
    vrt_options: Union[Dict, NoneType] = None,
    post_process: Union[Callable[[numpy.ndarray, numpy.ndarray], Tuple[numpy.ndarray, numpy.ndarray]], NoneType] = None
)
```

#### Attributes

| Name | Type | Description | Default |
|---|---|---|---|
| filepath | str | Cloud Optimized GeoTIFF path. | None |
| src_dataset | rasterio.io.DatasetReader or rasterio.io.DatasetWriter or rasterio.vrt.WarpedVRT | Rasterio dataset. | None |
| tms | morecantile.TileMatrixSet | TileMatrixSet grid definition. Defaults to `WebMercatorQuad`. | `WebMercatorQuad` |
| minzoom | int | Overwrite Min Zoom level. | None |
| maxzoom | int | Overwrite Max Zoom level. | None |
| colormap | dict | Overwrite internal colormap. | None |
| nodata | int or float or str | Global options, overwrite internal nodata value. | None |
| unscale | bool | Global options, apply internal scale and offset on all read operations. | None |
| resampling_method | rasterio.enums.Resampling | Global options, resampling method to use for read operations. | None |
| vrt_options | dict | Global options, WarpedVRT options to use for read operations. | None |
| post_process | callable | Global options, Function to apply after all read operations. | None |
| dataset | rasterio.vrtWarpedVRT | Warped VRT constructed with dataset GCPS info. **READ ONLY attribute**. | None |

#### Ancestors (in MRO)

* rio_tiler.io.cogeo.COGReader
* rio_tiler.io.base.BaseReader
* rio_tiler.io.base.SpatialMixin

#### Instance variables

```python3
center
```

Dataset center + minzoom.

```python3
spatial_info
```

Return Dataset's spatial info.

#### Methods

    
#### close

```python3
def close(
    self
)
```

    
Close rasterio dataset.

    
#### feature

```python3
def feature(
    self,
    shape: Dict,
    dst_crs: Union[rasterio.crs.CRS, NoneType] = None,
    shape_crs: rasterio.crs.CRS = CRS.from_epsg(4326),
    max_size: int = 1024,
    indexes: Union[Sequence[int], int, NoneType] = None,
    expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read part of a COG defined by a geojson feature.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| shape | dict | Valid GeoJSON feature. | None |
| dst_crs | rasterio.crs.CRS | Overwrite target coordinate reference system. | None |
| shape_crs | rasterio.crs.CRS | Input geojson coordinate reference system. Defaults to `epsg:4326`. | `epsg:4326` |
| max_size | int | Limit the size of the longest dimension of the dataset read, respecting bounds X/Y aspect ratio. Defaults to `1024`. | `1024` |
| indexes | sequence of int or int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `COGReader.part` method. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### get_zooms

```python3
def get_zooms(
    self,
    tilesize: int = 256
) -> Tuple[int, int]
```

    
Calculate raster min/max zoom level.

    
#### info

```python3
def info(
    self
) -> rio_tiler.models.Info
```

    
Return COG info.

    
#### metadata

```python3
def metadata(
    self,
    pmin: float = 2.0,
    pmax: float = 98.0,
    **kwargs: Any
) -> rio_tiler.models.Metadata
```

    
Return Dataset's statistics and info.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| pmin | float | Histogram minimum cut. Defaults to `2.0`. | `2.0` |
| pmax | float | Histogram maximum cut. Defaults to `98.0`. | `98.0` |

**Returns:**

| Type | Description |
|---|---|
| rio_tile.models.Metadata | Dataset statistics and metadata. |

    
#### part

```python3
def part(
    self,
    bbox: Tuple[float, float, float, float],
    dst_crs: Union[rasterio.crs.CRS, NoneType] = None,
    bounds_crs: rasterio.crs.CRS = CRS.from_epsg(4326),
    max_size: int = 1024,
    indexes: Union[int, Sequence, NoneType] = None,
    expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read part of a COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| bbox | tuple | Output bounds (left, bottom, right, top) in target crs ("dst_crs"). | None |
| dst_crs | rasterio.crs.CRS | Overwrite target coordinate reference system. | None |
| bounds_crs | rasterio.crs.CRS | Bounds Coordinate Reference System. Defaults to `epsg:4326`. | `epsg:4326` |
| max_size | int | Limit the size of the longest dimension of the dataset read, respecting bounds X/Y aspect ratio. Defaults to `1024`. | `1024` |
| indexes | sequence of int or int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `rio_tiler.reader.part` function. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### point

```python3
def point(
    self,
    lon: float,
    lat: float,
    indexes: Union[Sequence[int], int, NoneType] = None,
    expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> List
```

    
Read a pixel value from a COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| lon | float | Longitude. | None |
| lat | float | Latittude. | None |
| indexes | sequence of int or int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `rio_tiler.reader.point` function. | None |

**Returns:**

| Type | Description |
|---|---|
| list | Pixel value per band indexes. |

    
#### preview

```python3
def preview(
    self,
    indexes: Union[Sequence[int], int, NoneType] = None,
    expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Return a preview of a COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| indexes | sequence of int or int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `rio_tiler.reader.preview` function. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### read

```python3
def read(
    self,
    indexes: Union[Sequence[int], int, NoneType] = None,
    expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read the COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| indexes | sequence of int or int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `rio_tiler.reader.read` function. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### stats

```python3
def stats(
    self,
    pmin: float = 2.0,
    pmax: float = 98.0,
    hist_options: Union[Dict, NoneType] = None,
    **kwargs: Any
) -> Dict[str, rio_tiler.models.ImageStatistics]
```

    
Return bands statistics from a COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| pmin | float | Histogram minimum cut. Defaults to `2.0`. | `2.0` |
| pmax | float | Histogram maximum cut. Defaults to `98.0`. | `98.0` |
| hist_options | dict | Options to forward to numpy.histogram function. | None |
| kwargs | optional | Options to forward to `rio_tiler.reader.stats`. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageStatistics | bands statistics. |

    
#### tile

```python3
def tile(
    self,
    tile_x: int,
    tile_y: int,
    tile_z: int,
    tilesize: int = 256,
    indexes: Union[Sequence[int], int, NoneType] = None,
    expression: Union[str, NoneType] = None,
    tile_buffer: Union[int, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read a Web Map tile from a COG.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| tile_x | int | Tile's horizontal index. | None |
| tile_y | int | Tile's vertical index. | None |
| tile_z | int | Tile's zoom level index. | None |
| tilesize | int | Output image size. Defaults to `256`. | `256` |
| indexes | int or sequence of int | Band indexes. | None |
| expression | str | rio-tiler expression (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `COGReader.part` method. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and tile spatial info. |

    
#### tile_exists

```python3
def tile_exists(
    self,
    tile_z: int,
    tile_x: int,
    tile_y: int
) -> bool
```

    
Check if a tile is intersets the dataset bounds.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| tile_x | int | Tile's horizontal index. | None |
| tile_y | int | Tile's vertical index. | None |
| tile_z | int | Tile's zoom level index. | None |

**Returns:**

| Type | Description |
|---|---|
| bool | True if the tile is intersets the dataset bounds. |