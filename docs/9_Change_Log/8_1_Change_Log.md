---
title: Latest Updates
---


# Latest Updates
A document that contains all the changes made to the standard.

## November 30, 2023
### Documents
 - Changed ALL date related fields to ISO 8601 standard, changed the format to `Date`.
 - Updated ALL JSON dates to read as `yyyy-mm-dd`. 
 - Changed appropriate identifier fields to UUID from string.
 - Changed Boolean values in JSON examples to `true` and `false` rather than `"TRUE"` and `"FALSE"`.
 - Change manufactedCountry format to string, and improved description to indicate that the numeric value should be used from ISO 3166.
 - Changed Numeric format to either Decimal or Integer.
    - Materials
        - areaDensity -> Decimal
        - areaDensityTolerance -> Decimal
    - Components
        - height -> Decimal
        - width -> Decimal
        - depth -> Decimal
        - volume -> Decimal
        - weight -> Decimal
        - weightTolerance -> Decimal
        - recycledContent -> Decimal
    - Complete Packaging
        - height -> Decimal
        - width -> Decimal
        - depth -> Decimal
        - volume -> Decimal
        - weight -> Decimal
        - weightTolerance -> Decimal
        - servingCapacity -> Integer
    - Multipacks
        - identicalQuantity -> Integer
    - Loads
        - timesSent -> Integer
    - Material Constituents
        - virginMaterial -> Decimal
        - layer -> Integer
        - materialPercentage -> Decimal
    - Component End of Life Routes
        - orderOfPrecedence -> Integer
    - Complete Packaging End of Life Routes
        - orderOfPrecedence -> Integer
    - Load Constituent
        - quantityInLoad -> Integer

## November 23, 2023
### Documents
 - Reworked data diagrams to show the constituents lists as the edges between the tables.
 - Updated data diagrams to remove obsolete `Load_Catalogue`.

## November 17, 2023
### Data fields
 - Added `areaDensity`, `areaDensityUnit`, `areaDensityTolerance`, `areaDensityToleranceType`, `areaDensityDate` to Materials core schema.

## October 12, 2023
### Model
 - Added Organisations relationships list
 - Removed Load Catalogue
 - Added Load Consitutuents relationship list  

### Data fields
 - Added manufacturers to all core schemas
 - Added manufacturing country to complete packaging, multipack and load
 - Removed componentContactWithProduct from Complete Packaging
 - Added contactWithProduct to Complete Packaging Constituents

### Documents
- Updated homepage for v2.1

## September 29, 2023
### Documents
 - Reworked data formats page to include various worked examples

## September 22, 2023
### Documents
- Added blank Excel workbook to supporting files page
- Added blank csvs for all core schema and all relationship lists to supporting files page and each schema page 

## September 7, 2023
### Documents
- Added example for Recycled Content Claims
- Added example for Recyclability Claims
- Added example for Certification Claims
- Added example for Components
- Added example for Complete Packaging End of Life
- Added example for Complete Packaging

## August 11, 2023
### Documents
- Added licence page so that users don't need to navigate to Github
- Improved homepage text regarding licencing
- Improved sidebar navigation
- Added licence to the footer
- Added Relationship list, UUID and Single Source of Truth to Key Concepts page
- Improved reability of Start Here Introduction
- Fixed comestics typo to cosmetics in products types
- Added product type descriptions
- Various other typos

### Data Fields
- Harmonised all boolean field descriptions so that they all stated "Answer as: 'TRUE' for yes and 'FALSE' for no."

## July 14, 2023
### Documents
- Removed catalogue from the introduction area
- Improved working about packaging levels
- Reworked introduction
- Improved key concepts page
- Updated data flow
- Improved Complete Packaging End of Life Route Relationship List
- Added Controlled List information page
- Improved the Goverance Page
- Improved the branding to fit with the Open 3P brand guidelines

## July 5, 2023
### Documents
- Removed banner detailing that the standard is about plastic packaging.
- Added Apache Licence to homepage

## July 4, 2023
### Documents, Model, Data Fields
- Moved to [verion 2.0](https://github.com/OpenDataManchester/PPP/releases/tag/v2.0.0). Read the release notes on [Github](https://github.com/OpenDataManchester/PPP/releases/tag/v2.0.0).

## March 17, 2023
### Documents
- General improvements

## March 10, 2023
### Documents
- Added versioning control so that there can be parrellell versions
- Updated Identifiers page to include information regarding UUID

## March 9, 2023
### Documents
- Variours changes to files for added function for versioning

## February 7, 2023
### Model
- Changed component catologue to components

### Documents
- Added additional examples
- Updated all data schema to based on changes

### Data Fields
- Changed tags to external identifiers

## February 3, 2023
### Model
- Changed materials catologue to base materials
- Added country to base materials

### Documents
- Added examples to base materials


## January 20, 2023
### Documents
- Added schema images to all Data Specification pages
- Added JSON example to all Data Specification pages
- Added CSV examples
- Added CSV templates

### Data Fields
- Fixed Complete Packaging Recycling Disruptor List

## January 06, 2023
### Documents
- Neaten up tables so that the status column doesn't go over multiple lines.
- Updated schema image.
- Fixed naming for material and material catalogue pages.
- Added favicon.

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