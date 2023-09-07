**Introduction**
Working with professor Megan Hofmann -> https://www.megan-hofmann.com/

who is the developer of the python library -> https://pypi.org/project/knit-script/

KnitScript is a specialized programming language designed to simplify the process of creating knitting patterns. Instead of manually specifying individual knitting stitches, KnitScript allows you to define patterns using higher-level constructs like textures and patterns, making knitting design more intuitive.

**Pattern Composition**

In KnitScript, patterns are composed of sub-patterns, enabling you to describe the placement and size of textures, rather than dealing with stitch-by-stitch instructions. While you have the flexibility to define patterns stitch by stitch, KnitScript makes it easier to work with larger knitting designs.

**Example Pattern**

Here's an example of a KnitScript program that defines a pattern with stockinette stitch, seed stitch, ribbing, and a slipped waves texture in the corners, all surrounded by a garter stitch border:

```knitscript
pattern squares
  fill (slippedWaves, 8, 8), fill (stst, 8, 8).
  fill (seed, 8, 8), fill (rib (1, 1), 8, 8).
end

show (standalone (garterBorder (squares, 4, 2)))
```

**Pattern Instructions**

When you run a KnitScript program, it generates knitting instructions. For example, the program above would produce instructions like "WS: CO 20 (20 sts)" and "RS: K 20 (20 sts)," guiding you through the knitting process.

**Verification**

KnitScript ensures the correctness of patterns. It checks for issues such as running out of stitches, having too many stitches left, or using stitches incorrectly. If any problems are detected, KnitScript provides clear feedback.

**Getting Started**

To learn more about KnitScript, you can explore the tutorial, watch the demo video, and download the KnitScript editor for both Windows and Mac platforms. Detailed information can be found in the language reference page.

**Background**

KnitScript originated as a student project at the University of Washington, inspired by other knitting languages like Purl, KP, and Knitting Visualizer. You can access project reports and poster slides in the provided links.

**Source Code**

To run KnitScript, you'll need Python 3.7 or later, ANTLR 4, and the antlr4-python3-runtime package installed. After installing dependencies, run `python setup.py build`. You can execute KnitScript programs using `python -m knitscript <filename>` or `knitscript <filename>` if you've run `python setup.py develop`.

---

This paraphrased version provides an overview of KnitScript, its features, example usage, and instructions for getting started with the language.
