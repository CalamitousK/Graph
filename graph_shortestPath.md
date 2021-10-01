
# Shortest Path in Undirected Graph with Unit Weights

## Thought Process

 * Create a distance array which will store the shortest path from source to all vertices
 * Initialize all the elements of the distance array with infinity
 * Assign the dist of source element as 0, because distance between source and source is always zero
 * create a queue
 * Push the source node into queue
 * Traverse while queue will become empty
     * Take out the node from queue
     * traverse all it's adjacent nodes
     * if the distance already stored in that node i.e dis[node] + 1 is smaller than the dis


```cpp
#include<bits/stdc++.h>
using namespace std;

void shortest_path(int v, int src, vector<int> adj[]){
    //create a distance array and initialize it with infinity
    int dis[v];
    for(int i=0; i<v; i++){
        dis[i] = INT_MAX;
    }
    
    //distance of source from the source will be zero
    
    dis[src] = 0;
    queue<int> q;
    q.push(src);
    
    //update if path is smaller
    while(!q.empty()){
        int node = q.front();
        q.pop();
        
        for(auto it : adj[node]){
            if((dis[node] + 1)<dis[it]){
                dis[it] = dis[node]+1;
                q.push(it);
            }
        }
    }
    //print result
    for(int i=0; i<v; i++) cout<<dis[i]<<" ";
}
int main(){
    int n, m;
    cin>>n>>m;
    
    vector<int> adj[n];
    for(int i=0; i<m; i++){
        int u, v;
        cin>>u>>v;
        
        adj[u].push_back(v);
        adj[v].push_back(u);
    }
    
    shortest_path(n, adj);
    return 0;
}

```
