<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: Vineela Shaik  </h3>
<h3>Register Number: 212223040243 </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


A* Search Algorithm
<ol>
<li> Initialize the open list</li>
<li> Initialize the closed list put the starting node on the open list (you can leave its f at zero)</li>
<li> While the open list is not empty<br>
    a. Find the node with the least f on 
       the open list, call it "q"<br>
    b. Pop q off the open list<br>
    c. Generate q's 8 successors and set their parents to q for each successor<br><ol>
        i. If successor is the goal, stop search<br>
        ii. Else, compute both g and h for successor
          <br>
          successor.g = q.g + distance between successor and successor.h = distance from goal to 
          successor (This can be done using many 
          ways, we will discuss three heuristics- 
          Manhattan, Diagonal and Euclidean 
          Heuristics)<br>
          successor.f = successor.g + successor.h<br>
        iii. if a node with the same position as successor is in the OPEN list which has a lower f than successor, skip this successor <br>
        iv. if a node with the same position as 
            successor  is in the CLOSED list which has
            a lower f than successor, skip this successor
            otherwise, add  the node to the open list
     end (for loop)<br></ol>
    d. push q on the closed list
    end (while loop)
</li>
</ol>

<h2>PROGRAM :</h2>
<pre><code>
from collections import defaultdict
H_dist ={}
def aStarAlgo(start_node, stop_node):
    open_set = set(start_node)
    closed_set = set()
    g = {}  
    parents = {}   
    g[start_node] = 0
    parents[start_node] = start_node
    while len(open_set) > 0:
        n = None
        for v in open_set:
            if n == None or g[v] + heuristic(v) < g[n] + heuristic(n):
                n = v
        if n == stop_node or Graph_nodes[n] == None:
            pass
        else:
            for (m, weight) in get_neighbors(n):
                if m not in open_set and m not in closed_set:
                    open_set.add(m)
                    parents[m] = n
                    g[m] = g[n] + weight
                else:
                    if g[m] > g[n] + weight:
                        g[m] = g[n] + weight
                        parents[m] = n
                        if m in closed_set:
                            closed_set.remove(m)
                            open_set.add(m)
        if n == None:
            print("Path does not exist!")
            return None
        if n == stop_node:
            path = []
            while parents[n] != n:
                path.append(n)
                n = parents[n]
            path.append(start_node)
            path.reverse()
            print('Path found: {}'.format(path))
            return path
        open_set.remove(n)
        closed_set.add(n)
    print('Path does not exist!')
    return None
def get_neighbors(v):
    if v in Graph_nodes:
        return Graph_nodes[v]
    else:
        return None
def heuristic(n):
    return H_dist[n]
graph = defaultdict(list)
n,e = map(int,input().split())
for i in range(e):
    u,v,cost = map(str,input().split())
    t=(v,int(cost))
    graph[u].append(t)
    t1=(u,int(cost))
    graph[v].append(t1)
for i in range(n):
    node,h=map(str,input().split())
    H_dist[node]=int(h)
Graph_nodes=graph
start=input()
goal=input()
aStarAlgo(start, goal)
</code></pre>





## Sample Graph I

![image](https://github.com/user-attachments/assets/b5be52a9-588f-4969-a645-7b194426f339)

## Sample Input

10 14 <br>
A B 6 <br>
A F 3 <br>
B D 2 <br>
B C 3 <br>
C D 1 <br>
C E 5 <br>
D E 8 <br>
E I 5 <br>
E J 5 <br>
F G 1 <br>
G I 3 <br>
I J 3 <br>
F H 7 <br>
I H 2 <br>
A 10 <br>
B 8 <br>
C 5 <br>
D 7 <br>
E 3 <br>
F 6 <br>
G 5 <br>
H 3 <br>
I 1 <br>
J 0 <br>

## Sample Output

Path found: ['A', 'F', 'G', 'I', 'J']
<br>
![Screenshot 2025-04-24 112919](https://github.com/user-attachments/assets/9168c104-93fc-42c7-b27b-bede5e8b7a0e)


## Sample Graph II

![image](https://github.com/user-attachments/assets/45d10f44-eae6-476a-aa82-504c505cccfa)




## Sample Input

6 6 <br>
A B 2 <br>
B C 1 <br>
A E 3 <br>
B G 9 <br>
E D 6 <br>
D G 1 <br>
A 11 <br>
B 6 <br>
C 99 <br>
E 7 <br>
D 1 <br>
G 0 <br>

## Sample Output

Path found: ['A', 'E', 'D', 'G']
<br>
![Screenshot 2025-04-24 113147](https://github.com/user-attachments/assets/2097653d-3aee-4098-86ed-11b720e7b056)


## RESULT :
Thus a graph was constructed and implemantation of A star Search for the same graph was done successfully.
