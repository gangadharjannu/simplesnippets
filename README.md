# simplesnippets
collection of javascript code snippets that are handy in programmer's day to day life

Fixing `typeof` operator

utility function for getting correct type using `Object.prototype.toString.call`
### 1

```console
var getType = function(obj) {
  return Object.prototype.toString.call(obj).match(/\s([a-z|A-Z]+)/)[1]
} 
```
### 2

```console
function getType(x){
 if (typeof x === 'object') return Object.prototype.toString.call(x).replace(/^\[object |\]$/g,'').toLowerCase()
 return typeof x
}
```
### 3

```console
function getTypeName(value) {
  if (value === null) {
      return "null";
  }
  var t = typeof value;
  switch(t) {
    case "function":
    case "object":
        if (value.constructor) {
            if (value.constructor.name) {
                return value.constructor.name;
            } else {
                // Internet Explorer
                // Anonymous functions are stringified as follows: 'function () {}'
                // => the regex below does not match
                var match = value.constructor.toString().match(/^function (.+)\(.*$/);
                if (match) {
                    return match[1];
                }
            }
        }
        // fallback, for nameless constructors etc.
        return Object.prototype.toString.call(value).match(/^\[object (.+)\]$/)[1];
    default:
        return t;
  }
}```

### References
[1] http://2ality.com/2011/11/improving-typeof.html