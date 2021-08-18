# Module rio_tiler.io.base

rio_tiler.io.base: ABC class for rio-tiler readers.

None

## Classes

### AsyncBaseReader

```python3
class AsyncBaseReader(
    tms: morecantile.models.TileMatrixSet = <TileMatrixSet title='Google Maps Compatible for the World' identifier='WebMercatorQuad'>
)
```

#### Ancestors (in MRO)

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

    
#### feature

```python3
def feature(
    self,
    shape: Dict,
    **kwargs: Any
) -> Coroutine[Any, Any, rio_tiler.models.ImageData]
```

    
Read a Dataset for a GeoJSON feature.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| shape | dict | Valid GeoJSON feature. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### info

```python3
def info(
    self
) -> Coroutine[Any, Any, rio_tiler.models.Info]
```

    
Return Dataset's info.

**Returns:**

| Type | Description |
|---|---|
| rio_tile.models.Info | Dataset info. |

    
#### metadata

```python3
def metadata(
    self,
    pmin: float = 2.0,
    pmax: float = 98.0,
    **kwargs: Any
) -> Coroutine[Any, Any, rio_tiler.models.Metadata]
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
    **kwargs: Any
) -> Coroutine[Any, Any, rio_tiler.models.ImageData]
```

    
Read a Part of a Dataset.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| bbox | tuple | Output bounds (left, bottom, right, top) in target crs. | None |

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
    **kwargs: Any
) -> Coroutine[Any, Any, List]
```

    
Read a value from a Dataset.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| lon | float | Longitude. | None |
| lat | float | Latittude. | None |

**Returns:**

| Type | Description |
|---|---|
| list | Pixel value per bands/assets. |

    
#### preview

```python3
def preview(
    self,
    **kwargs: Any
) -> Coroutine[Any, Any, rio_tiler.models.ImageData]
```

    
Read a preview of a Dataset.

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
    **kwargs: Any
) -> Coroutine[Any, Any, Dict[str, rio_tiler.models.ImageStatistics]]
```

    
Return Dataset's statistics.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| pmin | float | Histogram minimum cut. Defaults to `2.0`. | `2.0` |
| pmax | float | Histogram maximum cut. Defaults to `98.0`. | `98.0` |

**Returns:**

| Type | Description |
|---|---|
| rio_tile.models.ImageStatistics | Dataset statistics. |

    
#### tile

```python3
def tile(
    self,
    tile_x: int,
    tile_y: int,
    tile_z: int,
    **kwargs: Any
) -> Coroutine[Any, Any, rio_tiler.models.ImageData]
```

    
Read a Map tile from the Dataset.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| tile_x | int | Tile's horizontal index. | None |
| tile_y | int | Tile's vertical index. | None |
| tile_z | int | Tile's zoom level index. | None |

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

### BaseReader

```python3
class BaseReader(
    tms: morecantile.models.TileMatrixSet = <TileMatrixSet title='Google Maps Compatible for the World' identifier='WebMercatorQuad'>
)
```

#### Ancestors (in MRO)

* rio_tiler.io.base.SpatialMixin

#### Descendants

* rio_tiler.io.base.MultiBaseReader
* rio_tiler.io.base.MultiBandReader
* rio_tiler.io.cogeo.COGReader

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

    
#### feature

```python3
def feature(
    self,
    shape: Dict,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read a Dataset for a GeoJSON feature.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| shape | dict | Valid GeoJSON feature. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and input spatial info. |

    
#### info

```python3
def info(
    self
) -> rio_tiler.models.Info
```

    
Return Dataset's info.

**Returns:**

| Type | Description |
|---|---|
| rio_tile.models.Info | Dataset info. |

    
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
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read a Part of a Dataset.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| bbox | tuple | Output bounds (left, bottom, right, top) in target crs. | None |

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
    **kwargs: Any
) -> List
```

    
Read a value from a Dataset.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| lon | float | Longitude. | None |
| lat | float | Latittude. | None |

**Returns:**

| Type | Description |
|---|---|
| list | Pixel value per bands/assets. |

    
#### preview

```python3
def preview(
    self,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read a preview of a Dataset.

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
    **kwargs: Any
) -> Dict[str, rio_tiler.models.ImageStatistics]
```

    
Return Dataset's statistics.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| pmin | float | Histogram minimum cut. Defaults to `2.0`. | `2.0` |
| pmax | float | Histogram maximum cut. Defaults to `98.0`. | `98.0` |

**Returns:**

| Type | Description |
|---|---|
| rio_tile.models.ImageStatistics | Dataset statistics. |

    
#### tile

```python3
def tile(
    self,
    tile_x: int,
    tile_y: int,
    tile_z: int,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read a Map tile from the Dataset.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| tile_x | int | Tile's horizontal index. | None |
| tile_y | int | Tile's vertical index. | None |
| tile_z | int | Tile's zoom level index. | None |

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

### MultiBandReader

```python3
class MultiBandReader(
    reader: Type[rio_tiler.io.base.BaseReader],
    reader_options: Dict = NOTHING,
    tms: morecantile.models.TileMatrixSet = <TileMatrixSet title='Google Maps Compatible for the World' identifier='WebMercatorQuad'>
)
```

#### Attributes

| Name | Type | Description | Default |
|---|---|---|---|
| reader | rio_tiler.io.BaseReader | reader. | None |
| reader_options | dict, option | options to forward to the reader. Defaults to `{}`. | `{}` |
| tms | morecantile.TileMatrixSet | TileMatrixSet grid definition. Defaults to `WebMercatorQuad`. | `WebMercatorQuad` |
| bands | sequence | Band list. **READ ONLY attribute**. | None |

#### Ancestors (in MRO)

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

    
#### feature

```python3
def feature(
    self,
    shape: Dict,
    bands: Union[Sequence[str], str] = None,
    expression: Union[str, NoneType] = None,
    band_expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read and merge parts defined by geojson feature from multiple bands.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| shape | dict | Valid GeoJSON feature. | None |
| bands | sequence of str or str | bands to fetch info from. | None |
| expression | str | rio-tiler expression for the band list (e.g. b1/b2+b3). | None |
| band_expression | str | rio-tiler expression for each band (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `self.reader.feature` method. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and tile spatial info. |

    
#### info

```python3
def info(
    self,
    bands: Union[Sequence[str], str] = None,
    *args,
    **kwargs: Any
) -> rio_tiler.models.Info
```

    
Return metadata from multiple bands.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| bands | sequence of str or str | band names to fetch info from. Required keyword argument. | None |

**Returns:**

| Type | Description |
|---|---|
| dict | Multiple bands info in form of {"band1": rio_tile.models.Info}. |

    
#### metadata

```python3
def metadata(
    self,
    pmin: float = 2.0,
    pmax: float = 98.0,
    bands: Union[Sequence[str], str] = None,
    **kwargs: Any
) -> rio_tiler.models.Metadata
```

    
Return metadata from multiple bands.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| pmin | float | Histogram minimum cut. Defaults to `2.0`. | `2.0` |
| pmax | float | Histogram maximum cut. Defaults to `98.0`. | `98.0` |
| bands | sequence of str or str | bands to fetch info from. Required keyword argument. | None |
| kwargs | optional | Options to forward to the `self.reader.stats` method. | None |

**Returns:**

| Type | Description |
|---|---|
| dict | Multiple bands info an statistics in form of {"band1": rio_tile.models.Metadata}. |

    
#### parse_expression

```python3
def parse_expression(
    self,
    expression: str
) -> Tuple
```

    
Parse rio-tiler band math expression.

    
#### part

```python3
def part(
    self,
    bbox: Tuple[float, float, float, float],
    bands: Union[Sequence[str], str] = None,
    expression: Union[str, NoneType] = None,
    band_expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read and merge parts from multiple bands.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| bbox | tuple | Output bounds (left, bottom, right, top) in target crs. | None |
| bands | sequence of str or str | bands to fetch info from. | None |
| expression | str | rio-tiler expression for the band list (e.g. b1/b2+b3). | None |
| band_expression | str | rio-tiler expression for each band (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the 'self.reader.part' method. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and tile spatial info. |

    
#### point

```python3
def point(
    self,
    lon: float,
    lat: float,
    bands: Union[Sequence[str], str] = None,
    expression: Union[str, NoneType] = None,
    band_expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> List
```

    
Read a pixel values from multiple bands.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| lon | float | Longitude. | None |
| lat | float | Latittude. | None |
| bands | sequence of str or str | bands to fetch info from. | None |
| expression | str | rio-tiler expression for the band list (e.g. b1/b2+b3). | None |
| band_expression | str | rio-tiler expression for each band (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `self.reader.point` method. | None |

**Returns:**

| Type | Description |
|---|---|
| list | Pixel value per bands. |

    
#### preview

```python3
def preview(
    self,
    bands: Union[Sequence[str], str] = None,
    expression: Union[str, NoneType] = None,
    band_expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read and merge previews from multiple bands.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| bands | sequence of str or str | bands to fetch info from. | None |
| expression | str | rio-tiler expression for the band list (e.g. b1/b2+b3). | None |
| band_expression | str | rio-tiler expression for each band (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `self.reader.preview` method. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and tile spatial info. |

    
#### stats

```python3
def stats(
    self,
    pmin: float = 2.0,
    pmax: float = 98.0,
    bands: Union[Sequence[str], str] = None,
    **kwargs: Any
) -> Dict[str, rio_tiler.models.ImageStatistics]
```

    
Return array statistics from multiple bands.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| pmin | float | Histogram minimum cut. Defaults to `2.0`. | `2.0` |
| pmax | float | Histogram maximum cut. Defaults to `98.0`. | `98.0` |
| bands | sequence of str or str | bands to fetch info from. Required keyword argument. | None |
| kwargs | optional | Options to forward to the `self.reader.stats` method. | None |

**Returns:**

| Type | Description |
|---|---|
| dict | Multiple bands statistics in form of {"band1": rio_tile.models.ImageStatistics}. |

    
#### tile

```python3
def tile(
    self,
    tile_x: int,
    tile_y: int,
    tile_z: int,
    bands: Union[Sequence[str], str] = None,
    expression: Union[str, NoneType] = None,
    band_expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read and merge Web Map tiles multiple bands.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| tile_x | int | Tile's horizontal index. | None |
| tile_y | int | Tile's vertical index. | None |
| tile_z | int | Tile's zoom level index. | None |
| bands | sequence of str or str | bands to fetch info from. | None |
| expression | str | rio-tiler expression for the band list (e.g. b1/b2+b3). | None |
| band_expression | str | rio-tiler expression for each band (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `self.reader.tile` method. | None |

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

### MultiBaseReader

```python3
class MultiBaseReader(
    reader: Type[rio_tiler.io.base.BaseReader],
    reader_options: Dict = NOTHING,
    tms: morecantile.models.TileMatrixSet = <TileMatrixSet title='Google Maps Compatible for the World' identifier='WebMercatorQuad'>
)
```

#### Attributes

| Name | Type | Description | Default |
|---|---|---|---|
| reader | rio_tiler.io.BaseReader | reader. | None |
| reader_options | dict, option | options to forward to the reader. Defaults to `{}`. | `{}` |
| tms | morecantile.TileMatrixSet | TileMatrixSet grid definition. Defaults to `WebMercatorQuad`. | `WebMercatorQuad` |
| assets | sequence | Asset list. **READ ONLY attribute**. | None |

#### Ancestors (in MRO)

* rio_tiler.io.base.BaseReader
* rio_tiler.io.base.SpatialMixin

#### Descendants

* rio_tiler.io.stac.STACReader

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

    
#### feature

```python3
def feature(
    self,
    shape: Dict,
    assets: Union[Sequence[str], str] = None,
    expression: Union[str, NoneType] = None,
    asset_expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read and merge parts defined by geojson feature from multiple assets.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| shape | dict | Valid GeoJSON feature. | None |
| assets | sequence of str or str | assets to fetch info from. | None |
| expression | str | rio-tiler expression for the asset list (e.g. asset1/asset2+asset3). | None |
| asset_expression | str | rio-tiler expression for each asset (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `self.reader.feature` method. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and tile spatial info. |

    
#### info

```python3
def info(
    self,
    assets: Union[Sequence[str], str] = None,
    *args,
    **kwargs: Any
) -> Dict[str, rio_tiler.models.Info]
```

    
Return metadata from multiple assets.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| assets | sequence of str or str | assets to fetch info from. Required keyword argument. | None |

**Returns:**

| Type | Description |
|---|---|
| dict | Multiple assets info in form of {"asset1": rio_tile.models.Info}. |

    
#### metadata

```python3
def metadata(
    self,
    pmin: float = 2.0,
    pmax: float = 98.0,
    assets: Union[Sequence[str], str] = None,
    **kwargs: Any
) -> Dict[str, rio_tiler.models.Metadata]
```

    
Return metadata from multiple assets.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| pmin | float | Histogram minimum cut. Defaults to `2.0`. | `2.0` |
| pmax | float | Histogram maximum cut. Defaults to `98.0`. | `98.0` |
| assets | sequence of str or str | assets to fetch info from. Required keyword argument. | None |
| kwargs | optional | Options to forward to the `self.reader.metadata` method. | None |

**Returns:**

| Type | Description |
|---|---|
| dict | Multiple assets info and statistics in form of {"asset1": rio_tile.models.Metadata}. |

    
#### parse_expression

```python3
def parse_expression(
    self,
    expression: str
) -> Tuple
```

    
Parse rio-tiler band math expression.

    
#### part

```python3
def part(
    self,
    bbox: Tuple[float, float, float, float],
    assets: Union[Sequence[str], str] = None,
    expression: Union[str, NoneType] = None,
    asset_expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read and merge parts from multiple assets.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| bbox | tuple | Output bounds (left, bottom, right, top) in target crs. | None |
| assets | sequence of str or str | assets to fetch info from. | None |
| expression | str | rio-tiler expression for the asset list (e.g. asset1/asset2+asset3). | None |
| asset_expression | str | rio-tiler expression for each asset (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `self.reader.part` method. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and tile spatial info. |

    
#### point

```python3
def point(
    self,
    lon: float,
    lat: float,
    assets: Union[Sequence[str], str] = None,
    expression: Union[str, NoneType] = None,
    asset_expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> List
```

    
Read pixel value from multiple assets.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| lon | float | Longitude. | None |
| lat | float | Latittude. | None |
| assets | sequence of str or str | assets to fetch info from. | None |
| expression | str | rio-tiler expression for the asset list (e.g. asset1/asset2+asset3). | None |
| asset_expression | str | rio-tiler expression for each asset (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `self.reader.point` method. | None |

**Returns:**

| Type | Description |
|---|---|
| list | Pixel values per assets. |

    
#### preview

```python3
def preview(
    self,
    assets: Union[Sequence[str], str] = None,
    expression: Union[str, NoneType] = None,
    asset_expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read and merge previews from multiple assets.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| assets | sequence of str or str | assets to fetch info from. | None |
| expression | str | rio-tiler expression for the asset list (e.g. asset1/asset2+asset3). | None |
| asset_expression | str | rio-tiler expression for each asset (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `self.reader.preview` method. | None |

**Returns:**

| Type | Description |
|---|---|
| rio_tiler.models.ImageData | ImageData instance with data, mask and tile spatial info. |

    
#### stats

```python3
def stats(
    self,
    pmin: float = 2.0,
    pmax: float = 98.0,
    assets: Union[Sequence[str], str] = None,
    **kwargs: Any
) -> Dict[str, Dict[str, rio_tiler.models.ImageStatistics]]
```

    
Return array statistics from multiple assets.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| pmin | float | Histogram minimum cut. Defaults to `2.0`. | `2.0` |
| pmax | float | Histogram maximum cut. Defaults to `98.0`. | `98.0` |
| assets | sequence of str or str | assets to fetch info from. Required keyword argument. | None |
| kwargs | optional | Options to forward to the `self.reader.stats` method. | None |

**Returns:**

| Type | Description |
|---|---|
| dict | Multiple assets statistics in form of {"asset1": rio_tile.models.ImageStatistics}. |

    
#### tile

```python3
def tile(
    self,
    tile_x: int,
    tile_y: int,
    tile_z: int,
    assets: Union[Sequence[str], str] = None,
    expression: Union[str, NoneType] = None,
    asset_expression: Union[str, NoneType] = None,
    **kwargs: Any
) -> rio_tiler.models.ImageData
```

    
Read and merge Wep Map tiles from multiple assets.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| tile_x | int | Tile's horizontal index. | None |
| tile_y | int | Tile's vertical index. | None |
| tile_z | int | Tile's zoom level index. | None |
| assets | sequence of str or str | assets to fetch info from. | None |
| expression | str | rio-tiler expression for the asset list (e.g. asset1/asset2+asset3). | None |
| asset_expression | str | rio-tiler expression for each asset (e.g. b1/b2+b3). | None |
| kwargs | optional | Options to forward to the `self.reader.tile` method. | None |

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

### SpatialMixin

```python3
class SpatialMixin(
    tms: morecantile.models.TileMatrixSet = <TileMatrixSet title='Google Maps Compatible for the World' identifier='WebMercatorQuad'>
)
```

#### Attributes

| Name | Type | Description | Default |
|---|---|---|---|
| tms | morecantile.TileMatrixSet | TileMatrixSet grid definition. Defaults to `WebMercatorQuad`. | `WebMercatorQuad` |
| bbox | tuple | Dataset bounds (left, bottom, right, top). **READ ONLY attribute**. | None |
| minzoom | int | Overwrite Min Zoom level. **READ ONLY attribute**. | None |
| maxzoom | int | Overwrite Max Zoom level. **READ ONLY attribute**. | None |

#### Descendants

* rio_tiler.io.base.BaseReader
* rio_tiler.io.base.AsyncBaseReader

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