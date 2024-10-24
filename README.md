# LEETCODE-TREES-951
Let's go through a dry run of the provided `flipEquiv` function with a pair of trees to understand how the algorithm works.
### Code Analysis:
- If both `root1` and `root2` are `null`, the trees are equivalent (both are empty).
- If one tree is `null` and the other is not, they are not equivalent.
- If the values of `root1` and `root2` are not the same, the trees are not equivalent.
- Otherwise, recursively check:
  - Case 1: if the left subtree of `root1` is equivalent to the left subtree of `root2`, and the right subtree of `root1` is equivalent to the right subtree of `root2`.
  - Case 2: if the left subtree of `root1` is equivalent to the right subtree of `root2`, and the right subtree of `root1` is equivalent to the left subtree of `root2` (this is the "flipping" case).

### Dry Run Example:

Let's consider two binary trees:

```
Tree 1:
      1
     / \
    2   3
   /   / \
  4   6   7

Tree 2:
      1
     / \
    3   2
   / \
  7   6
   \
    4
```

#### Initial Call: `flipEquiv(root1, root2)` where `root1.val = 1`, `root2.val = 1`

- Since both root values are equal, we proceed to check their subtrees.
- Now, we check two cases:

#### Case 1: Direct comparison (no flip)
`flipEquiv(root1.left, root2.left)` where `root1.left.val = 2`, `root2.left.val = 3`
- The values are not equal, so this part of the check returns `false`.

#### Case 2: Flipped comparison
`flipEquiv(root1.left, root2.right)` where `root1.left.val = 2`, `root2.right.val = 2`
- The values are equal, so we proceed to check their subtrees.

#### Subtrees of `2`:
- `flipEquiv(root1.left.left, root2.right.left)` where `root1.left.left.val = 4`, `root2.right.left.val = 4`
  - Both are leaf nodes, and their values are equal. This returns `true`.
- `flipEquiv(root1.left.right, root2.right.right)` where both are `null`.
  - Both are `null`, so this returns `true`.

Thus, the comparison of these subtrees returns `true`.

#### Now back to the root level:
`flipEquiv(root1.right, root2.left)` where `root1.right.val = 3`, `root2.left.val = 3`
- The values are equal, so we proceed to check their subtrees.

#### Subtrees of `3`:
- `flipEquiv(root1.right.left, root2.left.right)` where `root1.right.left.val = 6`, `root2.left.right.val = 6`
  - Both are leaf nodes, and their values are equal. This returns `true`.
- `flipEquiv(root1.right.right, root2.left.left)` where `root1.right.right.val = 7`, `root2.left.left.val = 7`
  - Both are leaf nodes, and their values are equal. This returns `true`.

Since both subtrees of the right nodes match, this part of the comparison returns `true`.

#### Final result:
Since the flipped comparison at both levels returns `true`, the overall function will return `true`. These trees are flip equivalent.
