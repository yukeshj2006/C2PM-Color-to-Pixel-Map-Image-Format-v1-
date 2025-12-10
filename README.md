# C2PM-Color-to-Pixel-Map-Image-Format-v1-
C2PM (Color-to-Pixel Map) v1 is an experimental image format that reverses the traditional way images are stored.
Instead of mapping each pixel to a color value, C2PM maps each unique color to the list of pixel positions where it appears.

This creates a fully lossless inverted index of an image, enabling extremely fast color-based operations, mask generation, 
and analytical transformations directly from the format itself.

C2PM v1 is a structural prototype:
• exact RGB color preservation
• color → pixel index mapping
• simple binary specification
• encoder and decoder included
• no compression or hashing yet

─────────────────────────────────
HOW TO BUILD AND USE
─────────────────────────────────
1. Requirements
GCC or Clang
stb_image.h and stb_image_write.h (included in the repo)

2. Compile the Encoder
gcc encoder.c -o c2pm_encode -lm

3. Compile the Decoder
gcc decoder.c -o c2pm_decode -lm

4. Encode an Image (PNG → C2PM)
./c2pm_encode input.png output.c2pm

5. Decode an Image (C2PM → PNG)
./c2pm_decode output.c2pm restored.png

─────────────────────────────────
POTENTIAL USE CASES
─────────────────────────────────

While C2PM v1 is not optimized for size, its inverted-index structure enables unique workflows:

Pixel Art & Game Development
• Pixel artists often work with limited color palettes.
• C2PM allows instant selection of all pixels of a single color.
• Perfect for tools that highlight or modify sprite regions by palette.

Retro Game Engines and Tile Editors
• Palette swapping becomes trivial (O(U) instead of O(P)).
• Real-time recoloring without scanning the image.

Green-Screen / Chroma Keying Experiments
• Directly access all pixels of a given color range.
• Instant mask generation for single-color backgrounds.
• Act as an intermediate "selection format" for VFX R&D.

AI / Computer Vision
• Fast generation of pixel masks for segmentation.
• Useful for datasets where color class = region type.
• Efficient analytical operations on color-dominant images.

Educational & Research Tools
• Demonstrates inverted indexing data structures.
• Helps visualize how color distributions form images.
• Useful for teaching compression and alternative image representations.

─────────────────────────────────
ROADMAP
─────────────────────────────────
v2 — RLE compression for index lists  
v3 — Hash-indexed color table (O(1) lookup)  
v4 — Optional compression modes (lossy & lossless)  
v5 — C2PM viewer + color masking tools  

C2PM is open-source under the MIT License and intended for research, experimentation, and educational use.

Created by: Yukesh J
─────────────────────────────────
CREDITS
─────────────────────────────────
This project uses the stb_image and stb_image_write libraries by Sean Barrett (nothings.org),
released into the public domain and MIT-licensed.
