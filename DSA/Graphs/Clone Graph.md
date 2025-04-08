# Problem 

- Deep clone a given graph
- To create a new copy with new reference with the old data...

## Approach 

- Initialize the hashtable to store the original node and the corresponding cloned node.
- Using bfs.. creae a queue to store the current Node that is being checked.
- Iterate through each node using bfs method.
- For each current node check the neighbours are in the hashtable.
- If not present in the hashtable
  -  Add them in the hashtable
  -  push to the queue to expand
- else using the hashtable reference it in the neightbour list.


## Code 

```c++
/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> neighbors;
    Node() {
        val = 0;
        neighbors = vector<Node*>();
    }
    Node(int _val) {
        val = _val;
        neighbors = vector<Node*>();
    }
    Node(int _val, vector<Node*> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
};
*/

class Solution {
public:
    Node* cloneGraph(Node* node) {
        if (!node)
            return nullptr;

        unordered_map<Node*, Node*> mp;
        queue<Node*> q;

        // Clone the starting node and put it in the map
        Node* clone = new Node(node->val);
        mp[node] = clone;
        q.push(node);

        while (!q.empty()) {
            Node* curr = q.front();
            q.pop();

            for (Node* neighbor : curr->neighbors) {
                // If the neighbor is not cloned yet
                if (mp.find(neighbor) == mp.end()) {
                    mp[neighbor] = new Node(neighbor->val);
                    q.push(neighbor);
                }
                // Link the clone of the neighbor to the current clone
                mp[curr]->neighbors.push_back(mp[neighbor]);
            }
        }

        return clone;
    }
};

```
