# jq

+ **INPUT**
```
{
    "Success": "false",
    "a": [
        {
            "b": "test_job_id",
            "c": "test_error_type",
            "d": "test_error_message",
            "e": "test_job_url",
            "f": "test recipe name"
        }
    ]
}
```

+ **SETUP**
```
response=$(cat <<EOF
{"Success": "false","a": [{"b": "test_job_id","c": "test_error_type","d": "test_error_message","e": "test_job_url","f": "test recipe name"}]}
EOF
)
```

+ **COMMANDS**
```
x=$(echo $response | jq -r '.Success')
```
```
y=$(echo $response | jq ".a | .[] | .b" | wc -l)
```
```
z=$(echo $response | jq ".a | .[] | .b")
```
