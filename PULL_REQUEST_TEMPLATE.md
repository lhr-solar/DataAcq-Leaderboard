# Quality Assurance Checklist
To make reviews more efficient, please make sure the board meets the following standards and check everything off once the board meets the quality check. Once everything has been checked, the assigned reviewers will begin the review process. _Edit this description to check off the list._

There are exceptions with all guidelines. As long as your decisions are justified, then you are good! Contact the reviewers or the leads about any exceptions.

**Please *read* every word on *every* bullet point before checking off the corresponding box.**

## Minimum Prerequisites
- [x] The board passes ERC and DRC.
    - Note some ERC warnings are acceptable (**_CAUTION_** please be careful)
    - Note some DRC warnings are acceptable (less so than ERC: **_CAUTION_** please be careful).
- [x] All traces are routed.
- [x] Units are in metric.
- [ ] Gerbers are in a zip file in the main directory (after physical design is done)

**Please *read* every word on *every* bullet point before checking off the corresponding box.**

## Schematic Level Requirements 
- [x] Is proper noise resistance given to all peripheral devices (bypass caps and coils/ferrites)?  
- [x] Is proper ESD protection given to all MCU input pins (zener diodes)? You could also write the input pin rating for the MCU on the schematic.  
- [x] Is proper power protection given to peripheral devices (zener diodes)?  
- [x] Are peripheral units used properly (reading datasheet)?  
- [x] Are testing points added at useful places?  
- [x] Is there proper short to GND protection at MCU outputs (inline resistors)?  
- [x] Do ADC inputs have caps (appropriately sized to prevent RC delay)?  
- [x] Are ADC inputs biased so there is room above expected value to determine if value is being overflowed?  
- [x] Are LEDs located at useful places (comm, power, debugging, extra GPIO)? They should be placed in locations
- [x] Are parts chosen easy to collect?  
- [x] Are parts chosen easy to solder?  
- [x] Is there reverse polarity protection on inputs?  
- [x] Do parts in the schematic match the actual part datasheet?

**Please *read* every word on *every* bullet point before checking off the corresponding box.**

## BOM Requirements
- [x] **Bill Of Materials**: is there an Excel Sheet BOM and a Mouser Cart link?
- [x] Are *all* the correct parts in the BOM?
- [x] Is each part in the Mouser Cart in stock (or do we have the part in stock)?
- [x] Does each part in the Mouser Cart have a margin for part quantity?
- [x] Does every component in the schematic have a footprint, mouser link/datasheet, and reference number associated with it?

**Please *read* every word on *every* bullet point before checking off the corresponding box.**

## Layout Level Requirements 
### 2D Spacing
- [x] The components are spaced out at an optimal distance.
    - All components can be easily hand-soldered.
    - IPC-SM-782A Standard requires a minimum distance of 1.0mm from edge to edge.
- [x] Components that are in parallel with each other are spaced out at an equal distance when possible.
- [x] The components are aligned with each other when possible.
- [x] Components are grouped based off of functionality.
    - E.g. all components for CAN should be grouped.
- [x] Bypass capacitors are less than 1cm away from their respective IC's power pins.

### 3D Spacing
- [x] Layout of components have been placed with mounting location and usage of the board in mind.
    - Are PCBs going to be stacked on above/below this board? Are tall components placed accordingly?
    - Are buttons and lights easily accessible and viewable?
    - When mounted into the car, are the heights of the components and connectors accounted for?
- [ ] I am not reading every word and I need to start this checklist over.
    - Please uncheck everything you have checked and start over.
- [x] Location of connectors and wires going out of the board will prevent messy wiring.
    - Are all the wires that are going in the same direction placed on the same edge of the board?

### Components
- [x] Do footprints match the schematic?
    - Make sure pins on the footprint correspond to pins in the schematic 
    - (e.g. counterclockwise pins on footprint and alternating pins on schematic is *bad*)
- [x] Custom footprints have been double checked with the datasheet.
- [x] Footprints are consistent across the PCB: *i.e. all 0805 for Resistors/Capacitors*
- [x] Pin 1 of the footprint is labeled in some way. 
- [x] Are LED's in easy to see places? 
- [x] Are test points in easy to reach places?  
- [x] Are critical paths of switching converters as small as possible?  

### Copper Layer 
- [x] The trace widths and trace clearances are greater than JLCPCB's minimum requirements (https://jlcpcb.com/capabilities/Capabilities). 
    - [x] Are signal traces are .15mm unless provided with reasoning?   
        - NOTE: One net can have multiple trace widths  
- [x] The trace lengths are as short as possible. 
    - Can there be a more optimal route if you go to another layer? 
- [x] Each trace's width is capable of handling the expected current flow. 
    - Use PCB width calculator to calculate trace width. 
- [x] *No sharp corners. No trace angles equal to or less than 90 degrees. 
    - Orthogonal traces should have vias if necessary. 
- [x] Are edges of board surrounded by clean ground on both layers with stitching vias?  
- [x] Traces are in parallel with each other when possible (exceptions can be made to prevent signal coupling). 
    - E.g. traces connected between an IC and MCU can be placed in parallel with each other. 
- [x] There are no random trace appendages. 
- [x] Vias placed in copper pads are fully encompassed in the copper pads. 
- [x] Through-hole components do not have extraneous vias. 
- [x] Vias should be appropriately sized according to the connected net(s) and expected current capacity.

*Not really a problem for modern manufacturing techniques but good practice and important for high speed signal integrity.

### Silkscreen Layer
- [x] Visible text sizes are greater than .8mm(L), .8mm(H), .15mm(W).
- [x] All visible text is on the silkscreen layer.
- [x] All reference labels of each component are not overlapping a copper pad or another component.
- [x] All connector pins are labeled with a meaningful and helpful name.
- [x] All LEDs are labeled with a meaningful and helpful name.
- [x] Silkscreens are mostly facing one direction (or 2). 

### Edge Cut Layer
- [x] The dimensions of the board and the mounting holes are nice values in metric i.e. no long decimals.
- [x] The physical outline of the board is on the edge cut layer.
- [x] Edge cuts are straight and parallel with opposite edge of the board.
- [x] Mounting holes are aligned and support M3 screws. All mounting holes should have distances between them shown in comments layer.
- [x] Corners are curved and contoured to mounting holes.

**Please *read* every word on *every* bullet point before checking off the corresponding box.**

## IMPORTANT NOTICE
- [x] I am confident that this board will be safe to use in a safety critical environment.
- [x] I have read every word on every bullet point and have only checked off a bullet point if I have read every word.
- [x] ((( **OPTIONAL** ))) I had fun :^)

## Other Comments
_Write any comments about the board that would help the reviewers here._

BOM: 

- For the XBee LTE module, two 10 pin, 2mm pitch, female connectors will be soldered to the PCB instead. This allows the LTE module to be taken on and off the PCB. This part is not included in KiCad's BOM b/c it does not have a symbol. It is included in the mouser cart. Link to part: https://www.mouser.com/ProductDetail/Preci-dip/831-87-010-10-001101?qs=1N3g64hlyj4fvgxnz%2F%252BTYw%3D%3D

Safety:

- XBee RF Antenna: must be placed >= 26 cm from people
- XBee LTE Antenna: must be placed >= 20 cm from people

DRC Warnings:

- Ignoring: Silkscreen overlap
- Ignoring: Silkscreen clipped by solder mask
- Ignoring: Silkscreen clipped by board edge

Note: 

- Not needed: Is there proper short to GND protection at MCU outputs (inline resistors)?
- Not needed (LSOM takes care of): Is there reverse polarity protection on inputs?