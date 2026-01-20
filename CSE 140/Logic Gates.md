
Buffer - amplify power, like Minecraft

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
