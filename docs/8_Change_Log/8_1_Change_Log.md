# Latest Updates
A document that contains all the changes made to the standard.
## January 06, 2023
### Documents
- Neaten up tables so that the status column doesn't go over multiple lines.

## December 20, 2022
### Model
- separate out materials and material catalogue -> move to the front of the process

### Data Fields
- Component Catalogue: add identifier to link materials

## November 25, 2022
### Documentation
- Add definitions of recycling and reuse
- Bug fixes, typos and tweaks throughout

### Data Fields
- Component Catalogue: `branding` added due to updated epr
- Component Catalogue: `loaned` added due to epr
- Multipack: `outsideTier` removed because encoded with tier level

### Controlled Lists
- add none option to drs

## November 18, 2022
### Documents
- Complete Packaging: reformat component catalogue references by replacing `independentComponent`, `previouslyAssembledComponent` and `allComponent` with    
- Component Catalogue: created `previouslyAssembledComponent` as boolean and `componentLink` for addressing which components are attached when created.
- Upload Schema

## November 11, 2022
### Documents
- Component Catalogue: Update measurement guidelines.
- Complete Packaging: Update measurement guidelines.

## October 21, 2022
### Documents
- Complete Packaging: `householdWaste` turned into required field - representing the updated EPR

### Controlled Lists
- Completed Definitions for `shapes`
- Completed Definitions for `opacity`
- Completed Definitions for `level`
- Removed tertiary and replaced with ‘shipment’ and ‘transit’ to reflect updated EPR for `level`

## September 30, 2022
### Documents
- Fix typo in Key Concepts, Multipack
- For measurements: Add rounding rule. 
- Change volume measurement to millilitres
- For measurements: clarify why component measurements are slightly different to GS1's complete packaging measurement guidance. 

### Data Fields
- Complete Packaging: Added `weightTolerance` to the complete packaging

## September 26, 2022
### Structural/Model Changes
- Controlled list material function -> material purpose

### Data Fields
- Component Catalgoue: Moved `level` from  component catalogue to load catalogue
- Component Catalgoue: Removed `importedUK` since `manufacturedCountry` codes the same information
- Component Catalogue: `recycledContent` description updated - Recycled Content as the minimum allowable recycled content
- Component Catalogue: Added `weightTolerance` - definition to be updated.
- Component Catalogue Materials: `virginMaterial` description updated - virigin material as the maximum allowable created for the component
- Load: add the field `loadIdentifier` to link to the load catalogue


## September 9, 2022
### Data Fields
- required fields updated 
- All:`uploaded` changed to `update`
- All: `update` added
- All: `discontinued` changed to `discontinue`
- Component Catalogue Materials: added `materialName` 
- Component Catalgoue: added `partOfMultipack`
- Multipack: `packagingItems` replaced `completePackaging` and `component`

### Structural/Model Changes
- Added downloadable csv files to Supporting Files

## September 5, 2022
### Structural/Model Changes
- Data Flow created
- Introduction changed to `Start Here`; `Key Concepts` moved into `Start Here` and files updated to reflect these changes
### Data Fields
- required fields updated (still in process)

## September 2, 2022
### Structural/Model Changes
- Removal of Unique Components (fields moved to Component Catalogue or Complete Packaging)
- Addition of Load Catalogue: load split into load and load catalogue

### Data Fields
- Component Catalgoue: `format` split into `shape` and `function`
- Component Catalogue: Addition of `level`, `reuseSystem`, `importedUK`, and `manufacturedCountry` from unique components
- Component Catalogue Materials: `materialFunction` turned into `materialPurpose`
- Complete Packaging: Addition of `componentContactWithProduct` coverted from `directContactWithProduct` from unique components
- All: `tags` converted into a dictionary; `height`, `weight`, `depth`, `volume`, and `weight` converted into numeric