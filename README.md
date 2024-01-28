
# Graph

"Graph magic happening here! Explore code and visualizations in this GitHub repository."



[ Youtube Playlist ](https://www.youtube.com/watch?v=Y_0-AmbC0Ig&list=PLzjZaW71kMwSrxEtvK5uQnfNQ9UjGGzA-)

[ Cheat Sheet ](https://cheatography.com/hackin7/cheat-sheets/c-graph-theory-sample/pdf/)


## Questions
Q1 - https://leetcode.com/problems/find-if-path-exists-in-graph/

Sol.
```cpp
class Solution {
public:
    bool validPath(int n, vector<vector<int>>& edges, int source, int destination) {

        unordered_map<int, vector<int>> umap;
        for(auto x : edges){
            int u = x[0];
            int v = x[1];
            umap[u].push_back(v);
            umap[v].push_back(u);
        }

        vector<bool> visited(n+1, false);
        queue<int> q;
        q.push(source);
        visited[source] =true;
        while(!q.empty()){
            int top = q.front();
            q.pop();
            if(visited[destination] == true) return true;
            for(auto it : umap[top]){
                if(visited[it]==false){
                    visited[it]=true;
                    q.push(it);
                }
            }
        }
        return visited[destination];
    }
};
```

