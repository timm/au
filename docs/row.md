
# row.gold


```awk
function Row(i,a, tab) {
  Obj(i)
  is(i,"Row")
  for(j in a) add(tab.cols.all[j], a[j]) }

function  _Dist(i,j,tab,the,     k,n,d) {
  if (!length(cols))  
    return  _Dist(i,j,tab,the)
  for(k in the.cols) {
    n+=1
    d+= dist(tab.cols.all[k], i.cells[k], j.cells[k] )^the.p }
  return (d/n)^(1/the.p) }

function _Far(i,tab,the,     tmp,n) {
  for(j in tab.rows) {
    tmp[j]["id"] = j
    tmp[j]["dist"] = _Dist(i,tab.rows[j],tab,the) }
  return = int( the.far * keysort(tmp,"dist") ) }
```
