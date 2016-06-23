# Fileserver2

A http download and upload server

## Features

* Default to append
* Delete support
* Truncate support
* Form value upload
* File upload

## Examples

### File upload

```
[~ t1 ] $ cat example.log 
example body
[~ t1 ] $ curl localhost:8000/upload -F file=@example.log
Files uploaded successfully : example.log 13 bytes 
[~ t1 ] $
```

Results

```
[~ t ] $ cat example.log 
example body
[~ t ] $ 
```

### Form upload

```
[~ t1 ] $ curl localhost:8000/upload -F file=test -F data="test body"
Files uploaded successfully : test 9 bytes 
[~ t1 ] $ 
```

### Delete

```
[~ t1 ] $ curl localhost:8000/upload -F file=example.log -F delete=yes 
file: example.log deleted
[~ t1 ] $ 
```

### Truncate
if file not exists, it will create it

if file exists, by default it will append to the file

use truncate to overwrite the file

```
curl localhost:8000/upload -F file=@example.log -F truncate=yes 
```

or

```
curl localhost:8000/upload -F file=test -F data="test body" -F truncate=yes 
```

end
