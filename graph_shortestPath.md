
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
