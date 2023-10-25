
```bash
function getDay(year, month){
  var y = new Date(year,month,1,0,0,0);
  var yd = new Date(y-1000);
  return yd.getDate();
}
```
