# README - JedAI-spatial for three-dimensional Geospatial Interlinking 

The following README will guide you through the whole process of Geospatial Interlinking using jedAI-spatial.


>  &#x1F4A1; **Tip:** If you want to learn more about jedAI-spatial read the docs <a href="https://github.com/AI-team-UoA/JedAI-spatial">here</a>.

## Input
**For all key attributes in JSON, exactly one file path must be provided.**

<table>
  <tr>
    <th>Attributes</th>
    <th>Info</th>
    <th>Value Type</th>
    <th>Required</th>
  </tr>
  <tr>
    <td><code>source</code></td>
    <td><code>csv</code><br><code>tsv</code>
    <br><code>GeoJSON</code><br><code>JSONRDF</code><br><code>rdf</code>format</td>
    <td><code>list</code></td>
    <td>&#10004;</td>
  </tr>
  <tr>
    <td><code>target</code></td>
    <td><code>csv</code><br><code>tsv</code>
    <br><code>GeoJSON</code><br><code>JSONRDF</code><br><code>rdf</code>format</td>
    <td><code>list</code></td>
    <td>&#10004;</td>
  </tr>
</table>

```
{
	"inputs" :
		"source": [
      "d5e730ba..."
    ],
    "target": [
      "cb37e262..."
    ],
}
```

## Parameters
Concering input, additional info must be provided.

<table>
  <tr>
    <th>Attributes</th>
    <th>Info</th>
    <th>Value Type</th>
    <th>Required</th>
  </tr>
  <tr>
	  <td><code>source</code></td>
	  <td>Provide info for source dataset to be processed correctly</td>
	  <td><a href="#source/target">source_object</a></td>
	  <td>&#10004;</td> 
  </tr>
  <tr>
	  <td><code>target</code></td>
	  <td>Provide info for target dataset to be processed correctly</td>
	  <td><a href="#source/target">target_object</a></td>
	  <td>&#10004;</td> 
  </tr>
  <tr>
	  <td><code>algorithm</code></td>
	  <td><code>GIA.nt</code><br><code>RADON</code><br>
    <code>Plane Sweep (List)</code><br>
    <code>Plane Sweep (Strips)</code><br>
    <code>PBSM (List)</code><br>
    <code>PBSM (Strips)</code><br>
    <code>R-Tree</code><br>
    <code>Quad Tree</code><br>
    <code>CR-Tree</code><br>
    <code>Strip Sweep</code><br>
    <code>Strip STR Sweep</code></td>
	  <td></td>
	  <td>&#10004;</td> 
  </tr>
</table>



#### source/target
Attributes of keys: `source`, `target`
<table>
  <tr>
    <th>Attributes</th>
    <th>Info</th>
    <th>Value Type</th>
    <th>Required</th>
  </tr>
  <tr>
	  <td><code>data_tpye</code></td>
	  <td><code>csv</code><br>
	  <code>tsv</code><br>
	  <code>geojson</code><br>
	  <code>jsonrdf</code><br>
	  <code>rdf</code>
	  <td><code>string</code></td>
    <td>&#10004;</td> 
  </tr>
  <tr>
	  <td><code>geo_index</code></td>
	  <td>Index of the geometry</td>
	  <td><code>int</code></td>
	  <td>&#10004; if <code>csv</code> or <code>tsv</code></td> 
  </tr>
  <tr>
	  <td><code>attributes_first_row</code></td>
	  <td><code>true</code>/<code>false</code> if input dataset contains attributes at the first row</td>
	  <td><code>bool</code></td>
	  <td>&#10004; if <code>csv</code> or <code>tsv</code></td> 
  </tr>
  <tr>
	  <td><code>prefix_RDF</code></td>
	  <td>Prefix of the RDF triples</td>
	  <td><code>string</code></td>
	  <td>&#10004; if <code>rdf</code></td> 
  </tr>
</table>


> Input Examples
>
```
"parameters" : {
  "source" : {
      "data_type" : "csv",
      "geo_index": 0,
      "attributes_first_row" : true         
  },
  "target" : {
      "data_type" : "csv",
      "geo_index": 0,
      "attributes_first_row" : true         
  },
  "algorithm": "R-Tree"                
  },       

```

## Output
**For all key attributes in JSON, exactly one file path must be provided.**

<table>
  <tr>
    <th>Attributes</th>
    <th>Info</th>
    <th>Value Type</th>
    <th>Required</th>
  </tr>
  <tr>
    <td><code>metrics</code></td>
    <td>Creates a file with the metrics in <br><code>.json</code> format</td>
    <td><code>path</code></td>
    <td></td>
  </tr>
  <tr>
    <td><code>pairs</code></td>
    <td>Creates a ntriples file with the pairs that were matched<br><code>.nt</code> format</td>
    <td><code>path</code></td>
    <td></td>
  </tr>
</table>

```
"outputs": {
    "metrics" : {
      "url":"s3://klms-bucket/jedai-spatial/output_metrics.json"
    },
    "pairs" :{
      "url": "s3://klms-bucket/jedai-spatial/output_pairs.nt"
    }
}

```
