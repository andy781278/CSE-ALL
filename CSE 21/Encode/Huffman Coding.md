#Encode 
Pseudocode(C: list of symbols $a_i$ with frequencies $w_i$ , i=1,...,n):
F: Make a forest of trees each consisting of a single vertex $a_i$ and their weight $w_i$
Repeat until a tree is made:
	take the lowest two weighted trees, have them combine under a new tree where the root is the combined weight, and left is the bigger weight, right is the smaller weight

Example:
5A4B3C3D2E2F1G1H1J
5A4B3C3D2E2F1G   2{1H,1J}
5A4B3C3D2E2F   3{2{1H,1J},1G}
5A4B3C3D   4{2E,2F}   3{2{1H,1J},1G}
5A4B 6{3C,3D}   4{2E,2F}   3{2{1H,1J},1G}
5A 6{3C,3D}   4{2E,2F}   7{4B,3{2{1H,1J},1G}}}
6{3C,3D}   9{5A,4{2E,2F}}   7{4B,3{2{1H,1J},1G}}}
9{5A,4{2E,2F}}   13{7{4B,3{2{1H,1J},1G}}},6{3C,3D}}
22{13{7{4B,3{2{1H,1J},1G}}},6{3C,3D}},9{5A,4{2E,2F}}}
22[13[7[4B,3[2[1H,1J],1G]]],6[3C,3D]],9[5A,4[2E,2F]]]

0 left, 1 right

0000 -> B
000100 -> H
000101 -> J
00011 -> G
010 -> C
011 -> D
10 -> A
110 -> E
111 -> F
![[Pasted image 20251124104039.png]]
Length Comparison:
Usual Fixed Coding: 9 characters, 4 bit each, 5+4+3+3+2+2+3=22X4=88 bits
Huffman Coding: 5X2+4X3+3X3+3X3+2X3+2X3+1X5+1X6+1X6 = 60 bits

Decoding is easy, no need for dividers
Entropy: Higher it is, the less ordered it is and the harder to compress it down

Constant space for each element is required for the removal of commas/dividers when storing a list