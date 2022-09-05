# Latest Updates
A document that contains all the changes made to the standard.
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