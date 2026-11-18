# Record: Implementation of Huffman Coding

## Aim

To write a Python program to implement Huffman Coding for character-based data compression using character frequency.

## Software Used

- Python 3
- Jupyter Notebook / VS Code

## Algorithm

**Step 1:** Initialize the input string.

**Step 2:** Create an empty dictionary to store the frequency of each character.

**Step 3:** Traverse the input string and count the frequency of every character.

**Step 4:** Create nodes containing each character and its corresponding frequency.

**Step 5:** Sort the nodes based on their frequencies.

**Step 6:** Select the two nodes with the smallest frequencies.

**Step 7:** Combine the selected nodes into a new node with the sum of their frequencies.

**Step 8:** Repeat the process until only one node remains. This forms the Huffman Tree.

**Step 9:** Generate Huffman Codes by traversing the tree:
- Assign `0` to the left branch.
- Assign `1` to the right branch.

**Step 10:** Display each character along with its corresponding Huffman Code.

## Program

```python
input_string = "GOKUL B(212225230076)"  # Example input string

# Calculate character frequencies
frequency = {}

for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Create initial nodes
nodes = [[char, freq] for char, freq in frequency.items()]

# Build the Huffman Tree
while len(nodes) > 1:

    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

# The final node is the Huffman Tree
huffman_tree = nodes[0]

huffman_codes = {}

# Generate Huffman Codes
def generate_codes(tree, code=""):

    if isinstance(tree[0], str):
        # If it is a leaf node
        huffman_codes[tree[0]] = code

    else:
        # If it is an internal node
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)

# Display Huffman Codes
print("Character | GOKUL B(212225230076)")
print("-------------------------")

for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```

## Output

The program displays the Huffman Code assigned to each character based on its frequency.

<img width="501" height="396" alt="image" src="https://github.com/user-attachments/assets/02e2d917-6c88-4a70-aa85-8970831b83a2" />


## Result

Thus, Huffman Coding is successfully implemented using Python by calculating character frequencies, constructing a Huffman Tree, and generating unique binary codes for each character.
