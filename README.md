# Digital CAN Controller

We were trying to make a single bus CAN Controller through digital circuits as a part of Electronics Track in Tri-NIT Hackathon. 

## Transmitter (iter1.circ)

- We have implemented a CAN transmitter in which by hard coding the CAN Dataframe along with inputs in ROM (reversed manner i.e start of frame should be at the last address and
  so the as counter at left decrements it moves to other address locations one-by-one, finally *towards 00th address having 11 as its content* (to make it to be at rest after
  transmitting the data), and which will be transmitted serially).
- If we trigger the start (after setting the address in counter and can data frame in ROM) it will transmit data serially.

## Reciever (CAN_reciever.circ)

- We have implemented the Reciver's Identifier Circuit (that can be changed a little for each identifier address).

## Arbitration (iter2.circ & CAN_reciever.circ) (Circuit & Logic)

-  We have the Physical layer Bus circuit (as given in PS) and a Counter which will be counting for some preset cycles say 72 (after BUS becomes active) and then checks the BUS
  if it has been pulled up to reccessive state if so then, by using flags in Identifier and this circuit we can start/reset the Transmitter accordingly

- It happpens as dominant transmitter will keep on sending data, in other two node's reciever since the identifier doesn't match it will out LOW (flag1) based on which transmitter
  is reset and waits until the (flag2) from counter reports the end of message transferred in bus by dominant transmitter and so these other nodes will start transmitting (based on flag).

## To be done

- Integrate all the circuits, setup flags and verify the testcase.

