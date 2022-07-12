# Basic Authentication


Basic ```{username}:{password}```를 base64 encoding하여 헤더에 추가  


응답을 받은 서버는 헤더를 decode해서 username과 password를 구함

```
[header]
Authorization : Basic {username}:{password}
```

---

## curl  
```curl -u {username}:{password} -d grant_type=client_credentials {host}```

---

## go 언어


```go 
req, err := http.NewRequest(http.MethodPost, "host", nil)
req.SetBasicAuth(clientAuth.ClientId, clientAuth.ClientSecret)
```

##### net/http 패키지 내부 

```go
// package http

// header에 Authorization 추가
func (r *Request) SetBasicAuth(username, password string) {
	r.Header.Set("Authorization", "Basic "+basicAuth(username, password))
}

// "{username}:{password}" 형태를 base64 인코딩
func basicAuth(username, password string) string {
	auth := username + ":" + password
	return base64.StdEncoding.EncodeToString([]byte(auth))
}
```

##### 전체 코드 

```go
body := struct {
    GrantType    string `json:"grant_type"`
}{
    GrantType:    "client_credentials",
}
pbytes, _ := json.Marshal(body)
req, err := http.NewRequest(http.MethodPost, "https://host/token", bytes.NewBuffer(pbytes))
if err != nil {
    log.Fatalln(err)
}

req.Header.Add("Content-Type", "application/x-www-form-urlencoded")
req.SetBasicAuth(clientAuth.ClientId, clientAuth.ClientSecret) // Basic Authentication 등록

client := &http.Client{}
resp, err := client.Do(req)
if err != nil {
    log.Fatalln(err)
}
defer resp.Body.Close()

bytes, _ := ioutil.ReadAll(resp.Body)
fmt.Println(string(bytes))
```