# Component Catalogue Materials

Materials should be provided as a separate csv file, in tidy format. This means that each row of the csv file should be one material for a component. An example is provided.

The specification of this csv file is as follows:

[rws_services.csv](https://github.com/OpenDataManchester/Open3R/blob/V2/docs/8_Supporting_Files/8_1_3_RWS_Services_Template.csv){target=_blank}

|Column|Status|Format|Notes|
|:-|:-|:-|:-|
|identifier|`required`|String|A globally unique identifier. See identifiers section for information on how to construct this identifier|
|componentCatalogue|`required`|String|The unique identifier of the component that this row relates to. There must be an equivalent record in the `component_Catalogue` data|
|layer|`required`|integer|The layer associated with the component. The inner most layer (the layer closest to the product) denoted as 1, and the outermost layer is the biggest number.|
|materialWeight|`required`|numeric|The percentage of the total materials making-up the component. For every unique componentCatalogue, weightMaterial should add to 100%.|
|materialType|`required`|String|Is the material 'synthetic' or 'biobased'? Use the identifier of the material type that this row relates to. The entry here should be drawn from the material type controlled list.|
|materialFunction|`required`|String|Why is this material being used? Use the identifier of the material function that this row relates to. The entry here should be drawn from the material function controlled list.|
|materialCategory|`required`|String|The category this material row relates to. The entry here should be drawn from the material category controlled list.|
|materialChemCID|`required`|String|The PubChem CID for the exact material used. The PubChem CID is PubChem's compound identifier, which is a non-zero integer for a unique chemical structure. PubChem CID can be found using their [search](https://pubchem.ncbi.nlm.nih.gov/). If for some reason the PubChem CID cannot be located, consider contributing to PubChem and create the compound identifier. However, if this cannot be done, please enter `Unknown`.|
|materialOther|`required`|String|If the materialChemCID is `Unknown`, please enter the unique material here.|
|materialPrivacy|`required`|Boolean|Is the unique materialChemCID or materialOther anonymous/ privately protected?|
|virginMaterial|`required`|numeric|The percent of the material that was newly created for the component.|
