- 👋 Hi, I’m @YZPKQ02
- 👀 I’m interested in Algorithm, and i love Data Structure and Graph Theory
```cpp
struct SCC {
    int num, cnt;
    int dfn[N], low[N], col[N];
    stack< int > st;
    vector< int > adj[N], scc[N];

    void tarjan(int x) {
        dfn[x] = low[x] = ++ num;
        st.push(x);
        for (const auto &y : adj[x]) {
            if (!dfn[y]) {
                tarjan(y);
                low[x] = min(low[x], low[y]);
            } else if (!col[y]) {
                low[x] = min(low[x], dfn[y]);
            }
        }
        if (low[x] == dfn[x]) {
            col[x] = ++ cnt;
            scc[cnt].push_back(x);
            while (st.top() != x) {
                col[st.top()] = cnt;
                scc[cnt].push_back(st.top());
                st.pop();
            }
            st.pop();
        }
    }
};
```
<!---
YZPKQ02/YZPKQ02 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
