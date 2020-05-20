# jq
```
x=$(echo $response | jq -r '.Success')
```
```
y=$(echo $response | jq ".a | .[] | .b" | wc -l)
```
```
z=$(echo $response | jq ".a | .[] | .b")
```
