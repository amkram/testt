##### Welcome to the Taxonium documentation

```{toctree}
:includehidden:
:hidden:

index.md
taxoniumtools.md
advanced.md
```

Taxonium is a tool for exploring phylogenetic trees. The web interface can be accessed at [taxonium.org](https://taxonium.org/) and the source code repository at [https://github.com/theosanderson/taxonium](https://github.com/theosanderson/taxonium).

## Getting started

### Viewing a Newick tree

If you have a tree in Newick format and you just want to view it, you can just go to [Taxonium.org](http://taxonium.org), and select your tree file.

```{image} https://user-images.githubusercontent.com/19732295/169146746-4a31799a-66cf-4490-b925-ca17abf6af61.png
:width: 30em
:class: no-scaled-link
```

Or just drag and drop the file into the Taxonium window.

#### Adding metadata to your tree

Optionally, you can also upload a metadata file with your tree. This file should be in TSV or CSV format. It should have a heading with column names. The left-most column should contain the node names as used in the Newick file. The remaining columns should contain metadata for each node.

```{image} https://user-images.githubusercontent.com/19732295/169146935-6f40721a-7457-480a-85ed-185e5daaa205.png
:width: 30em
:class: no-scaled-link
```

```{eval-rst}
.. note::
    All files supplied to Taxonium can also have .gz extensions, indicating they are gzipped: i.e. tree.nwk.gz, metadata.tsv.gz, taxonium.jsonl.gz
```

### Viewing the global SARS-CoV-2 tree

We maintain an instance of Taxonium that displays a version of the SARS-CoV-2 global public tree built by the UShER team, at [Cov2Tree.org](http://cov2tree.org).

```{image} https://user-images.githubusercontent.com/19732295/169147139-8f67e297-9d0c-4707-9e92-95827498e24d.png
:width: 40em
:class: no-scaled-link
```

### Using an UShER mutation annotated tree

Taxonium is especially powerful when applied to a tree that has been annotated with mutations. With these trees it can allow searching for mutations, or displaying genotypes. Such trees are often generated by [UShER](https://github.com/yatisht/usher/). Please refer to the [UShER documentation](https://usher-wiki.readthedocs.io/en/latest/) for advice on how to make such a tree.

:::{note}
Sometimes you might just want to annotate an existing SARS-CoV-2 tree. You can download MATs pre-built by the UShER team from [here](https://hgwdev.gi.ucsc.edu/~angie/UShER_SARS-CoV-2/), which you can add your own metadata to using `taxonium_to_usher`.
:::

Once you have an UShER-annotated tree, we provide a tool for converting it to a format that Taxonium can use. The Taxonium format is a JSONL file with a list of nodes, each with all of its metadata, and a position. To create such a file we can use the `usher_to_taxonium` tool, from the `taxoniumtools` package.

**We have a more detailed page on [how to use `usher_to_taxonium`](./taxoniumtools.md)**

# Browsing a tree

### Getting around

Once you have loaded a tree into the Taxonium interface you can explore it.

You can **pan** by clicking and dragging the tree, or using the arrow keys on your keyboard.

You can **zoom vertically** by scrolling with your mouse, or with the buttons at the bottom right of the window, or with the + and - keys on your keyboard.

You can **zoom horizontally** by scrolling with your mouse whilst holding down Ctrl, or by toggling the scroll type with the icon in the bottom right and then scrolling normally or using the buttons in the bottom right.

### Using the minimap

At the top right of the tree is a minimap showing the whole tree, with a box showing the viewport you are currently looking at. You can click on a spot on the minimap to jump the view to a particular place on the minimap.

### Selecting a node

Click on a node to select it. The bottom of the right hand panel will display information about the node. You can click the arrow next to the nodes name to jump the selection up to this node's parent node.

If this node has descendants, the number of them will be displayed. You can click the list icon next to this number to list these descendants.

```{note}
When you zoom in very far on a big tree the view box may look like a horizontal line, but that's just because you are zoomed in on such a small vertical part of the tree.
```

If you want to turn off the minimap you can do so under the settings.

### Colouring the tree

You can use the **Color by** option to color the tree. You can color by any metadata item, and for MATs you can also colour by the genotype at any desired position.

### Searching the tree

You can add one or more searches to the tree in the right hand search panel. These can include searches on most metadata items.

You can also add a "Boolean" search, this enables you to combine sub-searches, either in AND mode, meaning a node must satisfy all or them, or OR mode, meaning it can satisfy any one.

```{note}
For MATs you can search for **mutations**. Note that this will identify the internal node at which a mutation is said to have occurred in the tree.
```

### Changing the tree type

If the tree has a time tree, inferred with [Chronumental](https://github.com/theosanderson/chronumental), a drop-down menu on the right hand side will allow you to toggle the x-axis between **time** and **genetic distance**.

### Custom settings

You can click the settings icon at the bottom right of the tree to:

- Enable/disable the minimap
- Change the density of text
- Toggle mutation types (by default only amino acid changes are shown, but nucleotide changes can be enabled)