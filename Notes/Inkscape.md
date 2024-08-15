# Inkscape configuration directories
`Preferences > System > User config`

# Circuit Symbols for Diagrams
https://github.com/medwatt/circuitikz_symbols
1. Download the SVG file named `circuitikz_0.5mm_grid.svg`.
2. **Locate Inkscape Directory [[Inkscape#Inkscape configuration directories|(see here)]]**: Move the downloaded SVG file to Inkscape's symbol directory.
4. **Access Symbols in Inkscape**: To use the symbols, go to `Object > Symbols` within Inkscape and pick the SVG file from the drop-down list. Or `Ctrl + Shift + Y`

- Use 0.25mm thickness for wire and create a grid using `Document Properties > Grid`
- To modify the element symbols/variables, go to `Edit > Clone > Unlink clone`

# Using latex in Inkscape
https://inkscape.org/learn/tutorials/latex/
Make sure `pdflatex` is installed https://gist.github.com/rain1024/98dd5e2c6c8c28f9ea9d

**If the menu appears grayed out**, make sure you have inkscape installed with apt install and not snap