# Create an SSC Base Package.

SSC relies on a default-replacement-like system to change the clothing seasonally. These are instructions on how to create a Base package that gives us something to replace for each season. (You can also use an existing Maxis outfit as a base.)

> [!IMPORTANT]
> You can't just copy-and-alter an existing Base package. Their resources will have the same Group and therefore work as replacements for each other. You need to actually create the package in BodyShop in order to get a (pseudo-)uniquely assigned Group.

## Create and Name the Package
1. [Create a new clothing package in BodyShop](bodyshop.md). Name it something memorable.
	- Use a full-body, top, or bottom outfit as appropriate.
	- Use an outfit of the right age, outfit category, and gender. If an outfit doesn't exist in the variant you want, go download one and use that as the outfit you copy.
	> [!NOTE]
    > You'll never see the outfit you pick unless you remove *all* your corresponding seasonal files, so it doesn't really matter what you pick beyond that. I suggest picking something at the front of the catalog in the right categories (e.g. aftopsleevelesshirt_limeswirls for adult female everyday tops) and using it over and over again -- it will make later steps and repetitive steps simpler.

1. Grab your new file from the SavedSims folder and move it to your Downloads folder or wherever you like to work on files.

1. Rename it in the SSC style: `SSC_[AgeGenderBodypart]_[Style]_[Color Trait]_[Color Palette Trait]_Base.package`. For example, if you're creating a base for an adult female top in a casual style in dark green, you'd name the file `SSC_AFTop_Casual_Dark_Green_Base.package`. The name isn't absolutely crucial but it will help you keep your SSC content well-organized!

1. Open the file. 

1. Change (or add, if there isn't one) the Text List resource to be either the exact name of the file (without .package) or something very similar. Commit and Save.
1. Change the "name" line in the Property Set (GZPS) to look like the file name (without .package), but with everything in lowercase to emulate the Maxis style. For our example, that would be `ssc_aftop_casual_green_shade_base`. Commit.
1. Save.

## Remove Unnecessary Resources

### Textures
Because we're never going to see this outfit and we're not changing anything about the mesh or texture, we should remove the texture to save file space and loading time. 

1. [Texture reference](/docs/texturereference/tomaxis.md) your outfit to its Maxis equivalent. I'd suggest doing the advanced version and referencing directly to the Maxis TXMT rather than referencing your TXMT to the Maxis TXTR -- but either way, you are going to be saving a lot of space and time just by getting rid of the texture.

## Update Sortindex

1. In the Binary Index (BINX) resource, update the sortindex line to reflect SSC color sorting as documented [here](/docs/scc/sortindexes.md). (In the example we've been using, dark green, we'd use `4070`.)
1. Commit and Save.

## Update Product ID
1. Either manually or with the BSOK Editor, assign the appropriate product ID.