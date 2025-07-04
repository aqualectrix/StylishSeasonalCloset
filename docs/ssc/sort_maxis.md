# Group and Sort a Maxis Outfit

Because sorting involves manipulating the sortindex, and overriding Maxis sorting is difficult, we actually hide the Maxis outfit and create a texture-referenced clone to sort and group.

## Create the Package
1. [Create a package in BodyShop](/docs/packagecreation/bodyshop.md), copying the outfit you want to sort.
1. Open the package and check the name line in the Property Set (GZPS resource). Write this down. We'll call it "NAME" in future steps.
1. Change the name in the Property Set to "ssc_NAME". For example, `afttopmomshirt_black` would become `ssc_aftopmomshirt_black`. Commit and Save.
1. Add (or change the existing) a Text List line that reads "SSC_NAME". For example, `SSC_aftopmomshirt_black`. (This becomes the outfit's tooltip.) Copy this string. Commit.
1. Save the file using the copied string as the file name. The file name and and tooltip should match -- this helps you find the file later.

## Sort and Group
Here we use manual editing to put the outfit in the right CCCASOK group. You can skip the first two steps and do this later in the [BSOK Editor](https://www.picknmixmods.com/Sims2/Notes/BsokEditor/BsokEditor.html) if you prefer.
1. In the Property Set, change the `creator` line's value to be `00000000-0000-0000-0000-000000000000`. (You can usually copy this value from somewhere else in the Property Set.) Commit.
1. Change the `product` line's value to be the correct CCCASOK product ID. (It is helpful to have a list of these open to copy and paste values from.) Commit and Save.
1. In the Binary Index (BINX) resource, change the `sortindex` line's value to the appropriate [SSC sortindex value](/docs/ssc/sortindexes.md). (It is helpful to have that page open for reference). Commit and Save.

## Remove Unneeded Resources
1. Delete all TXTR and TXMT resources from your package. Save.
1. In the 3IDR file, remove all Material Definition lines. Commit and Save.

## Export Maxis Resources
1. In the SimPE Finder, use the **PropertySet Search** to search for your outfit's NAME.
1. Double-click the result to open the package containing it.
1. Extract the Property Set. Give it name you'll recognize like "NAME_gzps".
1. In the SimPE Finder, use the **NameMap Search** to search for your outfit's NAME, but without the color portion. For example, instead of searching for `aftopmomshirt_black`, search for just `aftopmomshirt`. (This makes sure you find all relevant TXMT resources.)
1. Double-click on one of the TXMTs you've found to open the package containing it. In the Resource List, sort by name.
1. Extract all the TXMTs that correspond to the color of your outfit. For example, for `aftopmomshirt_black`, you'd export just the `aftopmomshirt_black_txmt` TXMT. For `aftoplongsleevebustier_black`, you'd export not just `aftoplongsleevebustier_black_txmt`, but also `aftoplongsleevebustier_alpha5_black_txmt` and `aftoplongsleevebustier_alpha7_black_txmt`.

## Fix References
1. Open your package.
1. Add all the TXMTs you exported. Save.
1. Look at the Property Set resource. 
1. If there is more than one `overridesubset` line, note the names and the order in which they appear. For example, for aftoplongsleevebustier_black, you would note that there are three override subsets, in the order "alpha5, alpha7, top".
1. Look at the 3IDR resource.
1. Press the "Package" button and drag each Material Definition, **in order**, into the 3IDR resource. Use the Instance to figure out which Material Definition corresponds to which TXMT, and drag them in in the order you noted. Note that the override subsets "top", "bottom", and "body" don't usually have their names in the TXMT names; they are the default subsets.
1. Click each new Material Definition line **in order** and use the "up" button to move it up four clicks, just above the UI Data line. Verify that the instance numbers (the last set) are still in the correct order.
1. Commit and Save.
1. Delete all the TXMT resources. Save.

## Hide Maxis Outfit
1. Add the Maxis Property Set you exported.
1. Change the "flags" line in the Property Set to have the value 1.
1. Commit and Save.
