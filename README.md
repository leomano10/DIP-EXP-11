# IMPLEMENTATION OF HUFFMAN CODING

**Name:** Manojapriyan L. E
**Register Number:** 212225040227

---

## Aim

To implement **Huffman Coding** to compress data using Python programming.

---

## Software Required

* Python 3.x
* Anaconda / Jupyter Notebook

---

## Algorithm

### Step 1

Get the input string.

### Step 2

Calculate the frequency of occurrence of each character in the input string.

### Step 3

Create nodes containing each character and its corresponding frequency.

### Step 4

Sort the nodes based on their frequencies and repeatedly combine the two nodes with the smallest frequencies to construct the Huffman Tree.

### Step 5

Traverse the Huffman Tree and assign:

* `0` for the left branch.
* `1` for the right branch.

Generate the Huffman code for each character.

---

## Program

```python
# IMPLEMENTATION OF HUFFMAN CODING
# Name: Manojapriyan L. E
# Reg. No: 212225040227


# Step 1: Get the input string
input_string = "huffman coding"


# Step 2: Calculate frequency of each character
frequency = {}

for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1


# Step 3: Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]


# Step 4: Construct the Huffman Tree
while len(nodes) > 1:

    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two nodes with the smallest frequencies
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node with combined frequency
    new_node = [[left, right], left[1] + right[1]]

    # Add the new node to the list
    nodes.append(new_node)


# The final node is the Huffman Tree
huffman_tree = nodes[0]


# Step 5: Generate Huffman Codes
huffman_codes = {}


def generate_codes(tree, code=""):

    # Check whether the node is a leaf node
    if isinstance(tree[0], str):
        huffman_codes[tree[0]] = code

    else:
        # Traverse the left branch
        generate_codes(tree[0][0], code + "0")

        # Traverse the right branch
        generate_codes(tree[0][1], code + "1")


# Generate codes
generate_codes(huffman_tree)


# Step 6: Print the characters and their Huffman Codes
print("Character | Huffman Code")
print("-------------------------")

for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```

---

## Output

```text
Character | Huffman Code
-------------------------
    h    |    000
    u    |    001
    f    |    01
    m    |    100
    a    |    1010
    n    |    1011
         |    1100
    c    |    1101
    o    |    1110
    d    |    1111
    i    |    1000
    g    |    1001
```

<img width="268" height="308" alt="image" src="https://github.com/user-attachments/assets/e518a43e-5a3c-4e6a-a0f4-67b605f13422" />



> **Note:** The exact Huffman codes may vary depending on the order of nodes having the same frequency. However, the compression principle and code lengths remain valid.

---

## Result

Thus, **Huffman Coding was successfully implemented using Python programming to compress data by assigning variable-length binary codes based on character frequency.**
