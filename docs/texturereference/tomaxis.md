# Texture Reference a Recolor to a Maxis Texture

## Find the Maxis Texture Name(s)
1. Find the Maxis name of the texture you want to use.
	1. [Find the Property Set name](/docs/defaultreplace/maxisfindname) of a Maxis outfit that uses the texture.
	1. Open SimPE's Finder and use the "NameMap Search" to search for the full name of the outfit, e.g. `aftophalter_dots`. This will find the TXMT (Material Definition) for that texture.
	1. Double-click the TXMT name to open the package containing it. Go to Plugin View to look at the TXMT itself.
	1. Find the line called `stdMatBaseTextureName`. This value is the name of the texture. (If the outfit has more than one subset or "group", you'll want to find and note all of the `TextureName` lines and their names.)

## Reference Textures in Your TXMT
1. Open your recolor package and open the TXMT (Material Definition). Find `stdMatBaseTextureName` in your TXMT and replace the value with the Maxis name you found. (Repeat for any other `TextureName` lines.) Commit the change.
1. Remove the custom TXTR resources from your package; nothing references them anymore.
1. Save.

## Advanced - Use Maxis TXMT
If your TXMT now looks exactly like the Maxis one you found, and you don't mind the rare possibility that someone might create a replacement **for that TXMT** (unlikely), you can use the Maxis TXMT instead.
1. Extract the Maxis TXMT and add it to your package.
1. Edit the 3IDR to point to the Maxis TXMT (Material Definition) instead of yours.
1. Delete all TXMTs (both your original TXMT and the Maxis TXMT) from your package and save.