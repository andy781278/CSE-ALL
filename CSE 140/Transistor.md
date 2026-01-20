
Complementary Metal Oxide Semiconductor (CMOS) Switches
Metal - Conductor
Oxide - Insulator
Silicon - Semiconductor
Source/Drain - Semiconductor with impurities

negative Metal Oxide Semiconductor (nMOS)
- negative charge go through the source, gets pulled by the positive charge in the gate, but can't get to it because of the oxide, making it a capacitor.
- negative charge going through Semiconductors generate small resistance.

- If you put negative charge in the gate instead of positive, then positive charge gets stuck between the source and drain, then it neutralizes with anything coming from source.
- This makes an open circuit, since no current flows, with infinite resistance.

- pass logic 1 to the gate, nMOS turns on.
- pass logic 0 to the gate, nMOS turns off.

- Passes 0s well

positive Metal Oxide Semiconductor (pMOS)
- Completely opposite to nMOS, but everything else works the same
- pass logic 1 to the gate, pMOS turns off.
- pass logic 0 to the gate, pMOS turns on.

- Passes 1s well

NOT Gate:
p on top, n on bot
Delay: 2CR

##### NOT Gate

| Input | P   | N   | Output | Delay |
| ----- | --- | --- | ------ | ----- |
| 0     | ON  | OFF | 1      | 2CR   |
| 1     | OFF | ON  | 0      | 2CR   |


##### NAND Gate

| Input (A B) | P1  | P2  | N1  | N2  | Output | Delay |
| ----------- | --- | --- | --- | --- | ------ | ----- |
| 0 0         | ON  | ON  | OFF | OFF | 1      | CR    |
| 0 1         | ON  | OFF | OFF | ON  | 1      | 2CR   |
| 1 0         | OFF | ON  | ON  | OFF | 1      | 2CR   |
| 1 1         | OFF | OFF | ON  | ON  | 0      | 4CR   |
##### AND Gate

| Input (A B) | P1  | P2  | N1  | N2  | X   | P   | N   | Output (Y) | Delay X | Delay Y | Total Delay |
| ----------- | --- | --- | --- | --- | --- | --- | --- | ---------- | ------- | ------- | ----------- |
| 0 0         | ON  | ON  | OFF | OFF | 1   | OFF | ON  | 0          | CR      | 2CR     | 3CR         |
| 0 1         | ON  | OFF | OFF | ON  | 1   | OFF | ON  | 0          | 2CR     | 2CR     | 4CR         |
| 1 0         | OFF | ON  | ON  | OFF | 1   | OFF | ON  | 0          | 2CR     | 2CR     | 4CR         |
| 1 1         | OFF | OFF | ON  | ON  | 0   | ON  | OFF | 1          | 4CR     | 2CR     | 6CR         |
##### Transmission Gate
Z - disconnected, neither 0 or 1

| A   | EN  | N   | P   | B   |
| --- | --- | --- | --- | --- |
| 0   | 0   | OFF | OFF | Z   |
| 1   | 0   | OFF | OFF | Z   |
| 0   | 1   | ON  | ON  | 0   |
| 1   | 1   | ON  | ON  | 1   |
