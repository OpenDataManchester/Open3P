# Component Catalogue Materials

Materials should be provided as a separate csv file, in tidy format. This means that each row of the csv file should be one material for a component. An example is provided.

The specification of this csv file is as follows:

[component_catalogue_material.csv](https://github.com/OpenDataManchester/PPP/blob/main/docs/7_Supporting_Files/7_1_2_Component_Catalogue_Material_Template.csv){target=_blank}

|Column|Status|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See identifiers section for information on how to construct this identifier|
|materialIdentifier|`required`|String|The unique identifier of the created materials. See identifiers section for information on how to construct this identifier.|
|materialCatalogue|`required`|String|The unique identifier of the material that this row relates to. There must be an equivalent record in the `material_Catalogue` data|
|layer|`recommended`|integer|The layer associated with the component. The inner most layer (the layer closest to the product) denoted as 1, and the outermost layer is the biggest number.|
|materialWeight|`recommended`|numeric|The percentage of the total materials making-up the component. For every unique componentCatalogue, weightMaterial should add to 100%.|
|combinationPurpose|`recommended`|String|Why is this material being used? Use the identifier of the material function that this row relates to. The entry here should be drawn from the material function controlled list.|
|updateDate|`required`|String|The date that the material was provided/last updated. Use the format `dd/mm/yyyy`.|
