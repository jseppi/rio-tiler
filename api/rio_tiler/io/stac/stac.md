# Module rio_tiler.io.stac

rio_tiler.io.stac: STAC reader.

None

## Variables

```python3
DEFAULT_VALID_TYPE
```

## Functions

    
### fetch

```python3
def fetch(
    filepath: str,
    **kwargs: Any
) -> Dict
```

    
Fetch STAC items.

A LRU cache is set on top of this function.

**Parameters:**

| Name | Type | Description | Default |
|---|---|---|---|
| filepath | str | STAC item URL. | None |
| kwargs | any | additional options to pass to client. | None |

**Returns:**

| Type | Description |
|---|---|
| dict | STAC Item content. |

## Classes

### STACReader

```python3
class STACReader(
    filepath: str,
    item: Union[NoneType, Dict, pystac.item.Item] = None,
    tms: morecantile.models.TileMatrixSet = <TileMatrixSet title='Google Maps Compatible for the World' identifier='WebMercatorQuad'>,
    minzoom: int = None,
    maxzoom: int = None,
    include_assets: Union[Set[str], NoneType] = None,
    exclude_assets: Union[Set[str], NoneType] = None,
    include_asset_types: Set[str] = {'image/tiff', 'image/jp2', 'image/vnd.stac.geotiff; cloud-optimized=true', 'image/tiff; application=geotiff', 'image/x.geotiff', 'application/x-hdf5', 'image/tiff; application=geotiff; profile=cloud-optimized', 'application/x-hdf', 'image/tiff; profile=cloud-optimized; application=geotiff'},
    exclude_asset_types: Union[Set[str], NoneType] = None,
    reader: Type[rio_tiler.io.base.BaseReader] = <class 'rio_tiler.io.cogeo.COGReader'>,
    reader_options: Dict = NOTHING,
    fetch_options: Dict = NOTHING
)
```

#### Attributes

| Name | Type | Description | Default |
|---|---|---|---|
| filepath | str | STAC Item path, URL or S3 URL. | None |
| item | dict or pystac.Item, STAC | Stac Item. | None |
| minzoom | int | Set minzoom for the tiles. | None |
| minzoom | int | Set maxzoom for the tiles. | None |
| include | set of string | Only Include specific assets. | None |
| exclude | set of string | Exclude specific assets. | None |
| include_asset_types | set of string | Only include some assets base on their type. | None |
| exclude_asset_types | set of string | Exclude some assets base on their type. | None |
| reader | rio_tiler.io.BaseReader | rio-tiler Reader. Defaults to `rio_tiler.io.COGReader`. | `rio_tiler.io.COGReader` |
| reader_options | dict | Additional option to forward to the Reader. Defaults to `{}`. | `{}` |
| fetch_options | dict | Options to pass to `rio_tiler.io.stac.fetch` function fetching the STAC Items. Defaults to `{}`. | `{}` |

#### Ancestors (in MRO)

* rio_tiler.io.base.MultiBaseReader
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