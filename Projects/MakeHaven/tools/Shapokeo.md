# Steps
1. Create toolpaths with carbide create
2. Switch to carbide motion and zero machine
3. Use accessory to indicate corner of work area
	1. Switch tool to probe by changing collet (clamp for probe that is 1/8"). Tighten with wrench.
	2. Switch to "jog" tab and move probe to inside of hole
	3. Probe corner with V2 accessory
4. Load the endmill you will use to then zero Z axis
- For proper alignment, can use edge of table
- Dimensions: 33" x 33" x 4"


# Carbide create
- Insert width/height/thickness of material
- Zero = bottom of table
- Top mode - cut with depth, Bottom mode = cut through
- Can import svgs and inkscape files to trace

### Toolpaths
Contour - follow line
Pocket - remove material to certain depth
Texture - add specific textures
Drill - drill a hole

- Endmils cut out shapes, Ball mills cut smoother, Engravers are for finer paths
- Flutes are the # of channels on a drill bit that extract out sawdust 

- Stepover = how much paths are offset from each pass, 
- tabs are used to prevent piece from flying out

