---
title: Data Flow
description: The intented flow of data through the packaging value chain using Open 3P.
---

# Data Flow
Here, we show examples of how data could flow using the open standard. This tells the story of how wine bottles are created with a packaging manufacturer, how that packaging manufacturer sends their packaging to a packer/filler and then how that packer/filler will put packaging together, filled with a product and then send them to a retailer. The eight flow diagrams below compliment each other to build a complete picture.

!!! note "Shared responsiblity"

    When viewing the flows below be aware that no single individual and/or organisation is responsible for the entire data capture.
    It is the intent of Open 3P that experts in their part of the value chain are repsonsible for it's adherence to the data. 

## The flow
Open 3P has been designed to allow information to flow from base materials all the way through to a load. Below you can see how these are connected.
``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_example[base material]
    end
    subgraph materials[Materials]
        ma_example[material]
    end
    subgraph components[Components]
        co_example[component]
    end
    subgraph completePackages[Complete Packages]
        cp_example[complete package]
    end
    subgraph loads[Loads]
        lo_example[load]
    end
    bm_example --> ma_example
    ma_example --> co_example
    co_example --> cp_example
    cp_example --> lo_example
```
## Introducing basic items
At its most basic Open 3P allows the minimal amount of infomation to be passed along. In this example cardboard is used as the base material and then again as the material. At the component step the cardboard box is combined with tape to create a complete package ready to be filled by a product before being sent out on a load.
``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_cardboard[cardboard]
    end
    subgraph materials[Materials]
        ma_cardboard[cardboard]
    end
    subgraph components[Components]
        co_cardboard[cardboard box]
        co_example[tape]
    end
    subgraph completePackages[Complete Packages]
        cp_example[complete package]
    end
    bm_cardboard --> ma_cardboard
    ma_cardboard --> co_cardboard
    co_cardboard --> cp_example
    co_example --> cp_example
```
## Combining items to make complex items
Although some items used within the packaging value chains are simple, others are complex. Open 3P allows the combination of items at each schema level. In the example below a packaging tape is created by the combination of cellulose and adhesive. This is the used in conjunction with the cardboard box to create the complete packaging. The intent of Open 3P is for the packaging tape manufacturer to provide this information and share this along the value chain.
``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_cellulose[cellulose]
        bm_adhesive[adhesive]
        bm_cardboard[cardboard]
    end
    subgraph materials[Materials]
        ma_tape[tape]
        ma_cardboard[cardboard]
    end
    subgraph components[Components]
        co_cardboard[cardboard box]
        co_tape[tape]
    end
    subgraph completePackages[Complete Packages]
        cp_cardboard[delivery box]
    end
    bm_cellulose --> ma_tape
    bm_adhesive --> ma_tape
    bm_cardboard --> ma_cardboard
    ma_tape --> co_tape
    ma_cardboard --> co_cardboard
    co_cardboard --> cp_cardboard
    co_tape --> cp_cardboard
```
## Using items multiple times
Within the packaging value chain items are combined in different arrangements to create similar or completely distinct items. This can been seen below where the same sand and soda ash from a manufacuturer are used to make the two different types of glass; soda-lime glass and borosilicate glass. This information can be passed through the value chain, providing additional insights for stakeholders, clients and customers.
``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_sand[sand]
        bm_sodaAsh[soda ash]
        bm_limestone[limestone]
        bm_cullet[cullet]
        bm_boricOxide[boric oxide]
    end
    subgraph materials[Materials]
        ma_glass1["glass
        food and drink"]
        ma_glass2["glass
        pharmaceutical"]
    end
    subgraph components[Components]
        co_glassBottle1[glass bottle]
        co_glassBottle2[glass bottle]
    end
    subgraph completePackages[Complete Packages]
        cp_example1[complete packaging]
        cp_example2[complete packaging]
    end
    bm_limestone --> ma_glass1
    bm_cullet --> ma_glass1
    bm_sand --> ma_glass1
    bm_sand --> ma_glass2
    bm_sodaAsh --> ma_glass1
    bm_sodaAsh --> ma_glass2
    bm_boricOxide --> ma_glass2
    ma_glass1 --> co_glassBottle1
    ma_glass2 --> co_glassBottle2
    co_glassBottle1 --> cp_example1
    co_glassBottle2 --> cp_example2
```
## Creating a load
Taken as a whole the cardboard, tape and glass are combined at various points to create a wine delivery. With the addition of cork and aluminium all the materials and components can be seen.
``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_cardboard[cardboard]
        bm_sand[sand]
        bm_sodaAsh[soda ash]
        bm_limestone[limestone]
        bm_cullet[cullet]
        bm_aluminium[aluminium]
        bm_cork[cork]
        bm_cellulose[cellulose]
        bm_adhesive[adhesive]
    end
    subgraph materials[Materials]
        ma_cardboard[cardboard]
        ma_glass[glass]
        ma_cork[cork]
        ma_aluminium[aluminium]
        ma_tape[tape]
    end
    subgraph components[Components]
        co_glassBottle[bottle]
        co_corkCork[cork]
        co_aluminiumCapsule[capsule]
        co_cardboard[box]
        co_tape[tape]
    end
    subgraph completePackages[Complete Packages]
        cp_wineBottle[wine bottle]
        cp_cardboardBox[wine box]
    end
    subgraph loads[Loads]
        lo_wineDelivery[wine delivery]
    end
    bm_cardboard --> ma_cardboard
    bm_cullet --> ma_glass
    bm_sand --> ma_glass
    bm_limestone --> ma_glass
    bm_sodaAsh --> ma_glass
    bm_cork --> ma_cork
    bm_aluminium --> ma_aluminium
    bm_cellulose --> ma_tape
    bm_adhesive --> ma_tape
    ma_cardboard --> co_cardboard
    ma_glass --> co_glassBottle
    ma_aluminium --> co_aluminiumCapsule
    ma_cork --> co_corkCork
    ma_tape --> co_tape
    co_glassBottle --> cp_wineBottle
    co_corkCork --> cp_wineBottle
    co_aluminiumCapsule  --> cp_wineBottle
    co_cardboard --> cp_cardboardBox
    co_tape --> cp_cardboardBox
    cp_cardboardBox --> lo_wineDelivery
    cp_wineBottle --> lo_wineDelivery
```
## Within core schema combinations
The Open 3P standards allows further complexity when combining items within a schema. This is seen below where the two materials label and 'solvent free print substrate' are futher combined to create a 'printed label'.
``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_paper[paper]
        bm_adhesive[adhesive]
        bm_glassine[glassine]
        bm_ink[solvent free ink]
        bm_varnish[solvent free varnish]
    end
    subgraph materials[Materials]
        ma_label[label]
        ma_coating[solvent free print substrate]
        ma_label2[printed label]
    end
    subgraph components[Components]
        co_topLabel[branded front label]
        co_bottomLabel[branded back label]
        co_example[bottle]
    end
    subgraph completePackages[Complete Packages]
        cp_example[complete package]
    end
    bm_paper --> ma_label
    bm_adhesive --> ma_label
    bm_glassine --> ma_label
    bm_ink --> ma_coating
    bm_varnish --> ma_coating
    ma_label --> ma_label2
    ma_coating --> ma_label2
    ma_label2 --> co_topLabel
    ma_label2 --> co_bottomLabel
    co_topLabel --> cp_example
    co_bottomLabel --> cp_example
    co_example --> cp_example
```
## Laminates
Additionally base materials and materials can be layered in an ordered arrangement; known as lamination. In the example three base materials are layered together to create a laminate. Two of the materials are used twice within the material, with the third only being used the once.
``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_ep[ethylene-propylene]
        bm_eva[ethylene-vinyl acetate]
        bm_copolyester[copolyester]
    end
    subgraph materials[Materials]
        ma_shrinkwrap[plastic laminate]
    end
    subgraph components[Components]
        co_shrinkwrap[shrink wrap]
    end
    subgraph completePackages[Complete Packages]
        cp_shrinkwrap[shrink wrap]
    end
    bm_ep -- layer 1 --> ma_shrinkwrap
    bm_eva -- layer 2 --> ma_shrinkwrap
    bm_copolyester -- layer 3 --> ma_shrinkwrap
    bm_eva -- layer 4 --> ma_shrinkwrap
    bm_ep -- layer 5 --> ma_shrinkwrap
    ma_shrinkwrap --> co_shrinkwrap
    co_shrinkwrap --> cp_shrinkwrap
```
## Packaging Tier
This final example shows how the above examples are combined to create a flow for the wine bottles, with the inclusion of tiers for the packaging at the load schema.
``` mermaid
flowchart LR
    subgraph baseMaterials[Base Materials]
        bm_cardboard[cardboard]
        bm_sand[sand]
        bm_sodaAsh[soda ash]
        bm_limestone[limestone]
        bm_cullet[cullet]
        bm_aluminium[aluminium]
        bm_cork[cork]
        bm_cellulose[cellulose]
        bm_adhesive[adhesive]
        bm_paper[paper]
        bm_adhesive2[adhesive]
        bm_glassine[glassine]
        bm_ink[solvent free ink]
        bm_varnish[solvent free varnish]
        bm_ep[ethylene-propylene]
        bm_eva[ethylene-vinyl acetate]
        bm_copolyester[copolyester]
    end
    subgraph materials[Materials]
        ma_cardboard[cardboard]
        ma_glass[glass]
        ma_cork[cork]
        ma_aluminium[aluminium]
        ma_tape[tape]
        ma_label[label]
        ma_coating[solvent free print substrate]
        ma_label2[printed label]
        ma_shrinkwrap[plastic laminate]
    end
    subgraph components[Components]
        co_glassBottle[bottle]
        co_corkCork[cork]
        co_aluminiumCapsule[capsule]
        co_cardboard[box]
        co_tape[tape]
        co_topLabel[branded front label]
        co_bottomLabel[branded back label]
        co_shrinkwrap[shrink wrap]
    end
    subgraph completePackages[Complete Packages]
        cp_wineBottle[wine bottle]
        cp_cardboardBox[wine box]
        cp_shrinkwrap[shrink wrap]
    end
    subgraph loads[Loads]
        lo_wineDelivery[wine delivery]
    end
    bm_cardboard --> ma_cardboard
    bm_cullet --> ma_glass
    bm_sand --> ma_glass
    bm_limestone --> ma_glass
    bm_sodaAsh --> ma_glass
    bm_cork --> ma_cork
    bm_aluminium --> ma_aluminium
    bm_cellulose --> ma_tape
    bm_adhesive2 --> ma_tape
    bm_paper --> ma_label
    bm_adhesive --> ma_label
    bm_glassine --> ma_label
    bm_ink --> ma_coating
    bm_varnish --> ma_coating
    bm_ep -- layer 1 --> ma_shrinkwrap
    bm_eva -- layer 2 --> ma_shrinkwrap
    bm_copolyester -- layer 3 --> ma_shrinkwrap
    bm_eva -- layer 4 --> ma_shrinkwrap
    bm_ep -- layer 5 --> ma_shrinkwrap
    ma_label --> ma_label2
    ma_coating --> ma_label2
    ma_label2 --> co_topLabel
    ma_label2 --> co_bottomLabel
    ma_cardboard --> co_cardboard
    ma_glass --> co_glassBottle
    ma_aluminium --> co_aluminiumCapsule
    ma_cork --> co_corkCork
    ma_tape --> co_tape
    ma_shrinkwrap --> co_shrinkwrap
    co_glassBottle --> cp_wineBottle
    co_corkCork --> cp_wineBottle
    co_aluminiumCapsule  --> cp_wineBottle
    co_topLabel --> cp_wineBottle
    co_bottomLabel --> cp_wineBottle
    co_cardboard --> cp_cardboardBox
    co_tape --> cp_cardboardBox
    co_shrinkwrap --> cp_shrinkwrap
    cp_cardboardBox -- Secondary --> lo_wineDelivery
    cp_wineBottle -- Primary --> lo_wineDelivery
    cp_shrinkwrap -- Transit --> lo_wineDelivery
```