
# num.gold


@include "col"

```awk
function Num(i,at,txt) {
  Col(i,at,txt)
  is(i, "Num")
  i.mu = i.m2 = i.sd = 0
  i.lo = 10^32
  i.hi = -1*i.lo }

function _Add(i,x,    d) {
  i.lo  = x < i.lo ? x : i.lo
  i.hi  = x > i.hi ? x : i.hi
  d     = x - i.mu
  i.mu += d/i.n
  i.m2 += d*(x - i.mu)
  i.sd  = i.m2<0 ? 0 : (i.n<2 ? 0 : (i.m2/(i.n-1)))^0.5 }

function _Spread(i) { return i.sd }
function _Mid(i)    { return i.mu }

function _Dist(i,x,y) {
  if      (x=="?") { y = norm(i,y); x = y>0.5 ? 0 : 1 }
  else if (y=="?") { x = norm(i,x); y = x>0.5 ? 0 : 1 }
  else             { x = norm(i,x); y = norm(i,y)     }
  return abs(x-y) }

function _Cut(i,j,       a,b,c,r1,r2) {
  a  = 1/(2*i.sd^2) - 1/(2*j.sd^2)
  b  = j.mu/(j.sd^2) - i.mu/(i.sd^2)
  c  = i.mu^2 /(2*i.sd^2) - j.mu^2 / (2*j.sd^2) - log(j.sd/i.sd)
  r1 = (-b + (b^2 - 4*a*c)^.5)/(2*a)
  r2 = (-b - (b^2 - 4*a*c)^.5)/(2*a)
  return  (r1>= i.mu && r1<=j.mu) ? r1 : r2  }
```
