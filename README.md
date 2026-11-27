# Exp-11--Record-IMPLEMENTATION-OF-HUFFMAN-CODING
## NAME-J.AYSHWARIYA 
## REG NO-212224230030

## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:

Step 1: Read the input string from the user.

Step 2: Count how many times each character occurs (its frequency).

Step 3: Sort the characters by frequency, then repeatedly take the two lowest-frequency nodes and merge them into a new parent node whose frequency is their sum.

Step 4: Repeat Step 3 until only one node (the root of the Huffman tree) is left.

Step 5: Traverse the tree from the root, assigning 0 for every left branch and 1 for every right branch. The path to each character is its Huffman code. Print the characters with their codes.

 
## Program:

``` Python
# Step 1: Get the input string
input_string = "AYSHWARIYA"

# Step 2: Calculate frequency of each character
frequency = {}

for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Step 3: Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]

# Step 4: Main function to implement Huffman coding
while len(nodes) > 1:
    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

# The final node is the Huffman tree
huffman_tree = nodes[0]

# Step 5: Generate Huffman codes
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):
        huffman_codes[tree[0]] = code
    else:
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)

# Step 6: Print the characters and their Huffman codes
print("Character | Huffman Code")
print("-------------------------")

for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")


```
## Output:

### Print the characters and its huffmancode
<img width="457" height="296" alt="image" src="https://github.com/user-attachments/assets/8708eba1-33a2-43df-9c1a-7220e4eded4f" />





## Result
Thus the huffman coding was implemented to compress the data using python programming.
