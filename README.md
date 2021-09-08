# assignment2-makkena
# ajay
#### manali

>Manali is a **high-altitude Himalayan resort town** in India’s northern Himachal Pradesh state. It has a reputation as a backpacking center and honeymoon destination.
 Set on the Beas River, it’s a gateway for skiing in the Solang Valley and trekking in **Parvati Valley** It's also a jumping-off point for paragliding, rafting and mountaineering in the Pir Panjal mountains, home to 4,000m-high Rohtang Pass. manali is a cool and romntic place for lovers.

 ----
 # Heading for access to reach the place with order list and unordered list
 1. Start from marryville
 2. Go to kansas airport
    1. go to chicago airport
    2. go to delhi airport 
3. route map to manali
    1. Take Dr NS Hardikar Rd to NH9
    2. Drive from NH 44 to Mehmadpur
    3. Follow NH 205A to NH205 in Kharar
    4. Follow NH3 to Mall Rd in Manali
    5. Follow Mall Rd to Model Town Rd 3.    
* places in manali
    * Hadimba Temple
    * Jogini Waterfalls
    * Great Himalayan National Park
    * Rahala Falls
    * Bhrigu Lake 
 **[LinktoAboutme.md](Aboutme.md)**   

 ------
 # creating a drinks and food
**Introduction:**
 The following is to create a table with atleast 4 food/drinks that you would recommend someone try. Include a short paragraph that introduces the table.

|Mandatory   |fav1            |fav2             |fav3             |fav4       |
|:--------:  |:---------:     |:---------:      |:----------:     |:--------- |
|Food        |Biryani         |idly             |puri             |sprite     |
|Location    |ongole          |addanki          |vijayawada       |martur     |
|Amount      |450             |40               |55               |99         |

-----
# Section of Quotes
>“The life of inner peace, being harmonious and without stress, is the easiest type of existence.”
>*Author:* Ralph Waldo Emerson<br>
>"If you want total security, go to prison. There you're fed, clothed, given medical care and so on. The only thing lacking... is freedom"
>*Author:*Dwight D. Eisenhower

----
# Heading for code fencing
>There are various notions of a flow function that can be defined in a flow graph. Flow functions model the net flow of units between pairs of nodes, and are useful when asking questions such as what is the maximum number of units that can be transferred from the source node s to the sink node t? The simplest example of a flow function is known as a pseudo-flow. 
A pseudo-flow is a function f : V × V → ℝ that satisfies the following two constraints for all nodes u and v:
Skew symmetry: Only encode the net flow of units between a pair of nodes u and v (see intuition below), that is: f (u, v) = −f (v, u).
Capacity constraint: An arc's flow cannot exceed its capacity, that is: f (u, v) ≤ c(u, v).<https://en.wikipedia.org/wiki/Flow_network>
````
int n;
vector<vector<int>> capacity;
vector<vector<int>> adj;

int bfs(int s, int t, vector<int>& parent) {
    fill(parent.begin(), parent.end(), -1);
    parent[s] = -2;
    queue<pair<int, int>> q;
    q.push({s, INF});

    while (!q.empty()) {
        int cur = q.front().first;
        int flow = q.front().second;
        q.pop();

        for (int next : adj[cur]) {
            if (parent[next] == -1 && capacity[cur][next]) {
                parent[next] = cur;
                int new_flow = min(flow, capacity[cur][next]);
                if (next == t)
                    return new_flow;
                q.push({next, new_flow});
            }
        }
    }

    return 0;
}

int maxflow(int s, int t) {
    int flow = 0;
    vector<int> parent(n);
    int new_flow;

    while (new_flow = bfs(s, t, parent)) {
        flow += new_flow;
        int cur = t;
        while (cur != s) {
            int prev = parent[cur];
            capacity[prev][cur] -= new_flow;
            capacity[cur][prev] += new_flow;
            cur = prev;
        }
    }

    return flow;
}
````
Quick link to source code<https://cp-algorithms.com/graph/edmonds_karp.html>
