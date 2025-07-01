# Texture Reference a Recolor to an External Texture

Sometimes a texture is used in more than one package -- for example, outfits across ages or shoe textures across outfits. In that case you can save space by only including the actual texture in one file, and referencing it from other files. The file holding the texture is often called the "repository"; the files referencing the texture are often called "repositoried" or "repo'd".

## Find Texture Name(s)
1. Open a package containing TXTRs that you want to reference. Find the name (shown in the Resource List or in the Plugin View) of each TXTR you want.

## Reference Textures in Your TXMT
1. Open your recolor package and open the TXMT (Material Definition). Find `stdMatBaseTextureName` in your TXMT and replace the value with the TXTR name you found that includes "stdMatBaseTextureName". (Repeat for any other `TextureName` lines, matching the line name with the texture name.) Commit the change.
1. Remove the custom TXTR resources from your package; nothing references them anymore.
1. Save.