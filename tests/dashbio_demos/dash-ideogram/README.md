## Run the app

```bash
python tests/dashbio_demos/dash-ideogram/app.py
```
Then navigate to `localhost:8050` in your web browser.


## Usage

There are 2 tabs in this app: About and View.

The About tab contains a general overview of the Ideogram component.

In View tab you can choose view feature of the ideogram app. Also, you can 
specify different organism parameters such as species, sex, resolution. In labels 
you can turn the band off or on and same with the id of each chromosome. And 
another different style options such as orientation, rotatable, margin, height, width,
fully banded which you can specify.

## Documentation

Learn more about using the Ideogram with interactive examples in the [Dash Bio docs](https://dash.plotly.com/dash-bio/ideogram).


## Ideogram Properties Reference

- **id** (string; required): The ID used to identify this component in Dash callbacks and used to identify Ideogram instances.

- **ancestors** (dict; optional): A map associating ancestor labels to colors. Used to color chromosomes from different ancestors in polyploid genomes.
  
- **annotationHeight** (number; optional): Not used if annotationsLayout is set to "overlay". The height of histogram bars or the size of annotations tracks symbols.  

- **annotationTracks** (list of dicts; optional): A list of objects with metadata for each track, e.g., id, display name, color, shape. 

- **annotations** (list of dicts; optional): A list of annotation objects. Annotation objects can also have a name, color, shape, and track index. At the moment there is more keys specified and the docs need updating. 

- **annotations** is a list of dicts with keys:
  1. **chr** (string; optional)
  2. **name** (string; optional)
  3. **start** (number; optional)
  4. **stop** (number; optional)

- **annotationsColor** (string; default '#F00'): Color of annotations. 

- **annotationsData** (string; optional): Use this prop in a dash callback to return annotationData when hovered. It is read-only, i.e., it cannot be used with dash.dependencies.Output but only with dash.dependencies.Input. 

- **annotationsLayout** (a value equal to: 'tracks', 'histogram' or 'overlay'; default 'tracks'): Layout of ideogram annotations. One of "tracks", "histogram", or "overlay". "tracks": display annotations in tracks beside each chromosome. "histogram": display annotations in a histogram. Clusters annotations by location. Each cluster/bin is shown as a bar, the height of which represents the number of annotations on genomic range. "overlay": display annotations directly over chromosomes. 

- **annotationsPath** (string; optional): An absolute or relative URL directing to a JSON file containing annotation objects (JSON). 

- **assembly** (string; optional): Default: latest RefSeq assembly for specified organism. The genome assembly to display. Takes assembly name (e.g., "GRCh37"), RefSeq accession (e.g., "GCF_000306695.2"), or GenBank accession (e.g., "GCA_000005005.5"). 

- **barWidth** (number; default 3): Pixel width of histogram bars. Only used if annotationsLayout is set to "histogram". 

- **brush** (string; optional): Genomic coordinate range (e.g., "chr1:104325484-119977655") for a brush on a chromosome. Useful when ideogram consists of one chromosome and you want to be able to focus on a region within that chromosome, and create an interactive sliding window to other regions. 

- **brushData** (dict; optional): A dash callback that is activated when the 'brush' prop is used. It will return an dictionary like so: {'start': <value>, 'end': <value>, 'extent': <value>} where start is the left most edge, end is right most edge, and extent is the total width of the brush. It is read-only, i.e., it cannot be used with dash.dependencies.Output but only with dash.dependencies.Input. 

- **brushData** is a dict with keys:
  1. **end** (string; optional)
  2. **extent** (string; optional)
  3. **start** (string; optional)

- **chrHeight** (number; default 400): The pixel height of the tallest chromosome in the ideogram. 

- **chrMargin** (number; default 10): The pixel space of margin between each chromosome. 

- **chrWidth** (number; default 10): The pixel width of each chromosome.

- **chromosomes** (list of strings | dict; optional): A list of the names of chromosomes to display. Useful for depicting a subset of the chromosomes in the genome, e.g., a single chromosome. If Homology (between two different species): Ex: chromosomes={ 'human': ['1'], 'mouse': ['4'] } General case to specify specific chromosomes: Ex: chromosomes=['1', '2'].

- **className** (string; optional): The CSS class of the component wrapper.

- **container** (string; optional): CSS styling and the id of the container holding the Ideogram in react-ideogram.js, this is where all the d3 magic happens.

- **dataDir** (string; default 'https://unpkg.com/ideogram@1.5.0/dist/data/bands/native/'): Absolute or relative URL of the directory containing data needed to draw banded chromosomes. You will need to set up your own database to grab data from a custom database.  

- **filterable** (boolean; optional): Whether annotations should be filterable or not. 

- **fullChromosomeLabels** (boolean; optional): Whether to include abbreviation species name in chromosome label. Used for homology. 

- **histogramScaling** (a value equal to: 'absolute' or 'relative'; optional): Scaling of histogram bars height Only used if annotationsLayout is set to "histogram". One of "absolute" or "relative". "absolute": sets bar height relative to tallest bar in all chromosomes. "relative": sets bar height relative to tallest bar in each chromosome. 

- **homology** (dict; optional): Used to compare two chromosomes. The keys "chrOne" and "chrTwo" represent one chromosome each. Organism is the taxID or name. Start is an array, containing start one and start two, in this order. Stop is an array, containing stop one, and stop two, in this order. Ex: homology={ "chrOne": { organism": "9606", "start": [50000, 155701383], "stop": [900000, 156030895] }, "chrTwo": { organism": "10090", "start": [10001, 50000000], "stop": [2781479, 57217415] } }. 

- **homology** is a dict with keys:
    1. **chrOne** (dict; optional)
    **chrOne** is a dict with keys:
        1. **organism** (string; required)
        2. **start** (list of numbers; optional)
        3. **stop** (list of numbers; optional)
    2. **chrTwo** (dict; optional)
    **chrTwo** is a dict with keys:
        1. **organism** (string; required)
        2. **start** (list of numbers; optional)
        3. **stop** (list of numbers; optional)

- **localOrganism** (dict; optional): Provide local JSON organism into this prop from a local user JSON file. DataDir must not be initialized. 

- **organism** (string | number; default 'human'): Organism(s) to show chromosomes for. Supply organism's name as a string (e.g., "human") or organism's NCBI Taxonomy ID (taxid, e.g., 9606) to display chromosomes from a single organism, or an array of organisms' names or taxids to display chromosomes from multiple species. 

- **orientation** (a value equal to: 'vertical' or 'horizontal'; optional): The orientation of chromosomes on the page. 

- **perspective**  (a value equal to: 'comparative'; optional): Use perspective: 'comparative' to enable annotations between two chromosomes, either within the same organism or different organisms. Used for homology. 

- **ploidy** (number; default 1): The ploidy - number of chromosomes to depict for each chromosome set.

- **ploidyDesc** (list of dicts; optional): Description of ploidy in each chromosome set in terms of ancestry composition.
- **rangeSet**  (list of dicts; optional): List of objects describing segments of recombination among chromosomes in a chromosome set.
- **resolution** (number; optional): The resolution of cytogenetic bands to show for each chromosome. The quantity refers to an approximate value in bands per haploid set (bphs). One of 450, 550, or 850.
- **rotatable** (boolean; default True): Whether chromosomes are rotatable on click.
- **rotated** (boolean; optional): Dash callback that returns True if rotated, and False if not.
- **sex** (a value equal to: 'male' or 'female'; optional): Useful for omitting chromosome Y in female animals. Currently only supported for organisms that use XY sex-determination.
- **showAnnotTooltip** (boolean; default True): Whether to show a tooltip upon mousing over an annotation.
- **showBandLabels** (boolean; default False): Whether to show cytogenetic band labels, e.g., 1q21.
- **showChromosomeLabels** (boolean; default True): Whether to show chromosome labels, e.g., 1, 2, 3, X, Y.
- **showFullyBanded** (boolean; default True): Whether to show fully banded chromosomes for genomes that have sufficient data. Useful for showing simpler chromosomes of cytogenetically well-characterized organisms, e.g., human, beside chromosomes of less studied organisms, e.g., chimpanzee.
- **showNonNuclearChromosomes** (boolean; default False): Whether to show non-nuclear chromosomes, e.g., for mitochondrial (MT) and chloroplast (CP) DNA.
- **style** (dict; optional): The component's inline styles.