[home](http://github.com/timm/gold/README.md) :: <img align=right width=300 src="http://github.com/timm/gold//blob/master/etc/img/gold.png">
[lib1] ::
[cols] ::
[rows] ::
[&copy; 2020](http://github.com/timm/gold/LICENSE.md) by [Tim Menzies](http://menzies.us)   
# GOLD = the Gawk Object Layer

[home](http://github.com/timm/gold/README.me) ::
[lib] ::
[cols] ::
[rows] ::
[&copy; 2020](http://github.com/timm/gold/LICENSE.md) by [Tim Menzies](http://menzies.us)   
# GOLD = the Gawk Object Layer
----- 

```awk
function add(i,x,       k,f) {k=i.ois; f=k "Add";  return @f(i,x)}
function loop(i,        k,f) {k=i.ois; f=k "Loop"; return @f(i)}
function like(i,x,y,z,  k,f) {k=i.ois; f=k "Like"; return @f(i,x,y,z)}
```