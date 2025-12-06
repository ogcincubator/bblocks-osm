
# Highway (Schema)

`ogc.osm.features.highway` *v0.1*

This is used to describe roads and footpaths

[*Status*](http://www.opengis.net/def/status): Under development

## Examples

### Motorway
#### json
```json
{
  "highway": "motorway",
  "name": "A-7 Autovía del Mediterráneo",
  "surface": "asphalt",
  "oneway": "yes",
  "lanes": 3,
  "maxspeed": "120",
  "bridge": "no",
  "tunnel": "no",
  "source": "survey 2024-09"
}
```

#### jsonld
```jsonld
{
  "@context": "https://raw.githubusercontent.com/ogcincubator/bblocks-osm/undefined/build/annotated/osm/features/highway/context.jsonld",
  "highway": "motorway",
  "name": "A-7 Autov\u00eda del Mediterr\u00e1neo",
  "surface": "asphalt",
  "oneway": "yes",
  "lanes": 3,
  "maxspeed": "120",
  "bridge": "no",
  "tunnel": "no",
  "source": "survey 2024-09"
}
```

#### ttl
```ttl
@prefix dct: <http://purl.org/dc/terms/> .
@prefix osm: <https://example.com/osm/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

[] a osm:Motorway ;
    rdfs:label "A-7 Autovía del Mediterráneo" ;
    dct:source "survey 2024-09" ;
    osm:hasLaneCount 3 ;
    osm:hasSurfaceType <https://example.com/osm/surfaces/asphalt> ;
    osm:isOneWay "yes" .


```


### Steps
#### json
```json
{
  "highway": "steps",
  "name": "Station Stairway",
  "surface": "stone",
  "source": "local authority asset register"
}
```

#### jsonld
```jsonld
{
  "@context": "https://raw.githubusercontent.com/ogcincubator/bblocks-osm/undefined/build/annotated/osm/features/highway/context.jsonld",
  "highway": "steps",
  "name": "Station Stairway",
  "surface": "stone",
  "source": "local authority asset register"
}
```

#### ttl
```ttl
@prefix dct: <http://purl.org/dc/terms/> .
@prefix osm: <https://example.com/osm/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

[] a osm:Steps ;
    rdfs:label "Station Stairway" ;
    dct:source "local authority asset register" ;
    osm:hasSurfaceType <https://example.com/osm/surfaces/stone> .


```


### Residential road
#### json
```json
{
  "highway": "residential",
  "name": "Elm Street",
  "surface": "gravel",
  "lanes": 2,
  "oneway": false,
  "maxspeed": "30",
  "sidewalk": "both",
  "cycleway": "shared",
  "source": "OSM + field check"
}
```

#### jsonld
```jsonld
{
  "@context": "https://raw.githubusercontent.com/ogcincubator/bblocks-osm/undefined/build/annotated/osm/features/highway/context.jsonld",
  "highway": "residential",
  "name": "Elm Street",
  "surface": "gravel",
  "lanes": 2,
  "oneway": false,
  "maxspeed": "30",
  "sidewalk": "both",
  "cycleway": "shared",
  "source": "OSM + field check"
}
```

#### ttl
```ttl
@prefix dct: <http://purl.org/dc/terms/> .
@prefix osm: <https://example.com/osm/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

[] a osm:Residential ;
    rdfs:label "Elm Street" ;
    dct:source "OSM + field check" ;
    osm:hasLaneCount 2 ;
    osm:hasSurfaceType <https://example.com/osm/surfaces/gravel> ;
    osm:isOneWay false .


```

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
title: OpenStreetMap Highway Tag Collection
description: Proto schema for validating a subset of OSM 'highway' tags on ways/relations/nodes.
type: object
properties:
  highway:
    type: string
    description: Main classifier for roads, paths, and road-related features.
    enum:
    - motorway
    - trunk
    - primary
    - secondary
    - tertiary
    - unclassified
    - residential
    - service
    - motorway_link
    - trunk_link
    - primary_link
    - secondary_link
    - tertiary_link
    - living_street
    - pedestrian
    - busway
    - bus_guideway
    - bus_stop
    - bus_station
    - raceway
    - footway
    - path
    - track
    - cycleway
    - bridleway
    - steps
    - crossing
    - road
    - construction
    x-jsonld-id: '@type'
    x-jsonld-type: '@id'
    x-jsonld-extra-terms:
      motorway: https://example.com/osm/Motorway
      trunk: https://example.com/osm/Trunk
      primary: https://example.com/osm/Primary
      secondary: https://example.com/osm/Secondary
      tertiary: https://example.com/osm/Tertiary
      unclassified: https://example.com/osm/Unclassified
      residential: https://example.com/osm/Residential
      service: https://example.com/osm/Service
      motorwayLink: https://example.com/osm/MotorwayLink
      trunkLink: https://example.com/osm/TrunkLink
      primaryLink: https://example.com/osm/PrimaryLink
      secondaryLink: https://example.com/osm/SecondaryLink
      tertiaryLink: https://example.com/osm/TertiaryLink
      living_street: https://example.com/osm/LivingStreet
      pedestrian: https://example.com/osm/Pedestrian
      busway: https://example.com/osm/Busway
      bus_guideway: https://example.com/osm/BusGuideway
      bus_stop: https://example.com/osm/BusStop
      bus_station: https://example.com/osm/BusStation
      raceway: https://example.com/osm/Raceway
      footway: https://example.com/osm/Footway
      path: https://example.com/osm/Path
      track: https://example.com/osm/Track
      cycleway: https://example.com/osm/Cycleway
      bridleway: https://example.com/osm/Bridleway
      steps: https://example.com/osm/Steps
      crossing: https://example.com/osm/Crossing
      road: https://example.com/osm/Road
      construction: https://example.com/osm/Construction
  name:
    type: string
    description: Human-readable street/path name.
    x-jsonld-id: http://www.w3.org/2000/01/rdf-schema#label
  surface:
    type: string
    description: Physical surface type.
    enum:
    - asphalt
    - concrete
    - paved
    - unpaved
    - gravel
    - compacted
    - dirt
    - ground
    - grass
    - cobblestone
    - sett
    - stone
    - wood
    x-jsonld-id: https://example.com/osm/hasSurfaceType
    x-jsonld-type: '@id'
    x-jsonld-base: https://example.com/osm/surfaces/
  lanes:
    type: integer
    minimum: 1
    description: Number of marked lanes.
    x-jsonld-id: https://example.com/osm/hasLaneCount
  oneway:
    type:
    - string
    - boolean
    description: One-way traffic indicator.
    enum:
    - 'yes'
    - 'no'
    - '-1'
    - true
    - false
    x-jsonld-id: https://example.com/osm/isOneWay
  maxspeed:
    type: string
    description: Posted or implicit max speed.
    pattern: ^(\d+\s?(km/h|mph)?|[A-Z]{2}:[A-Za-z0-9_\-]+)$
  bridge:
    type: string
    enum:
    - 'yes'
    - 'no'
  tunnel:
    type: string
    enum:
    - 'yes'
    - 'no'
  cycleway:
    type: string
    enum:
    - lane
    - track
    - opposite_lane
    - opposite_track
    - share_busway
    - shared
    - 'no'
  sidewalk:
    type: string
    enum:
    - both
    - left
    - right
    - separate
    - 'no'
  access:
    type: string
    enum:
    - 'yes'
    - 'no'
    - private
    - destination
    - permissive
    - customers
    - delivery
  source:
    type: string
    description: Provenance for tags.
    x-jsonld-id: http://purl.org/dc/terms/source
required:
- highway
oneOf:
- properties:
    highway:
      const: motorway
      x-jsonld-id: '@type'
      x-jsonld-type: '@id'
    oneway:
      enum:
      - 'yes'
      - true
      description: Motorways are typically one-way per carriageway.
      x-jsonld-id: https://example.com/osm/isOneWay
- properties:
    highway:
      const: steps
      x-jsonld-id: '@type'
      x-jsonld-type: '@id'
    surface:
      enum:
      - concrete
      - stone
      - wood
      description: Common surfaces for steps.
      x-jsonld-id: https://example.com/osm/hasSurfaceType
      x-jsonld-type: '@id'
      x-jsonld-base: https://example.com/osm/surfaces/
- not:
    properties:
      highway:
        enum:
        - motorway
        - steps
$comment: 'Notes:

  - Enumerations reflect commonly documented values on the OSM wiki (Map features
  + Key:highway).

  - Many specialized keys (e.g., lanes:forward/backward, maxspeed:conditional) are
  omitted for simplicity.

  - Consider replacing tight enums with patterns or merging editor presets for broader
  coverage.

  '
x-jsonld-prefixes:
  rdfs: http://www.w3.org/2000/01/rdf-schema#
  osm: https://example.com/osm/
  dct: http://purl.org/dc/terms/

```

Links to the schema:

* YAML version: [schema.yaml](https://raw.githubusercontent.com/ogcincubator/bblocks-osm/undefined/build/annotated/osm/features/highway/schema.json)
* JSON version: [schema.json](https://raw.githubusercontent.com/ogcincubator/bblocks-osm/undefined/build/annotated/osm/features/highway/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "highway": {
      "@context": {
        "motorway": "osm:Motorway",
        "trunk": "osm:Trunk",
        "primary": "osm:Primary",
        "secondary": "osm:Secondary",
        "tertiary": "osm:Tertiary",
        "unclassified": "osm:Unclassified",
        "residential": "osm:Residential",
        "service": "osm:Service",
        "motorwayLink": "osm:MotorwayLink",
        "trunkLink": "osm:TrunkLink",
        "primaryLink": "osm:PrimaryLink",
        "secondaryLink": "osm:SecondaryLink",
        "tertiaryLink": "osm:TertiaryLink",
        "living_street": "osm:LivingStreet",
        "pedestrian": "osm:Pedestrian",
        "busway": "osm:Busway",
        "bus_guideway": "osm:BusGuideway",
        "bus_stop": "osm:BusStop",
        "bus_station": "osm:BusStation",
        "raceway": "osm:Raceway",
        "footway": "osm:Footway",
        "path": "osm:Path",
        "track": "osm:Track",
        "cycleway": "osm:Cycleway",
        "bridleway": "osm:Bridleway",
        "steps": "osm:Steps",
        "crossing": "osm:Crossing",
        "road": "osm:Road",
        "construction": "osm:Construction"
      },
      "@id": "@type",
      "@type": "@id"
    },
    "oneway": "osm:isOneWay",
    "surface": {
      "@context": {
        "@base": "https://example.com/osm/surfaces/"
      },
      "@id": "osm:hasSurfaceType",
      "@type": "@id"
    },
    "name": "rdfs:label",
    "lanes": "osm:hasLaneCount",
    "maxspeed": {},
    "bridge": {},
    "tunnel": {},
    "cycleway": {},
    "sidewalk": {},
    "access": {},
    "source": "dct:source",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "osm": "https://example.com/osm/",
    "dct": "http://purl.org/dc/terms/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://raw.githubusercontent.com/ogcincubator/bblocks-osm/undefined/build/annotated/osm/features/highway/context.jsonld)


# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/bblocks-osm](https://github.com/ogcincubator/bblocks-osm)
* Path: `_sources/features/highway`

