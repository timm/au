
# cluster.gold


@include "tab"

```awk
function Cluster(i,tab, the) {
  Obj(i)
  is(i, "Cluster")
  i.min = length(tab.rows)^.5 
  has(i,"clusters")
  has(i,"leafs")
}

function _Div(i,t,rows,the,up) {
  morE(i.leafs,"TabClone",t,rows) 
  r1 = anyi(rows)
  i.left  = DistFar(rows[r1], t, the)
  i.right = DistFar(rows[r2], t, the)
  c = _Dist(rows[i.left], rows[i.right],t,the)
  for(r in rows) {
    a = _Dist(rows[i.left], rows[r], t, the)
    b = _Dist(rows[i.right],rows[r], t, the)
    x = (a^2 +c^2 - b^2)/(2*c)
    if (x>1) x = 1
    if (x<0) x = 0
    tmp[r]["id"]   = r
    tmp[r]["dist"] = x }
  n= int( keysort(tmp,"dist")/2 )
  mid = tmp[ n ].dist
  for(r in tmp)
    append(tmp[r].dist < mid ? lefts : rights,rows[r])
  if (length(lefts) > the.min) _Div(i,t,lefts,the)
  if (length(rights) > the.min) _Div(i,t,rights,the)}
```
