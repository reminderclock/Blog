```javascript
    request(endpoint) {
        return fetch(`${entryPiont}${endpoint}`)
        .then((res) => {
            if(!res.ok) {
                throw new Erorr('http error');
            }
            return res.json();
        })
        .catch((e) => {
            throw new Error(`무언가 잘못${e.message}`)
        })
    }
    //
    async request(endPoint) {
        try{
            const res = await fetch(`${entryPiont}${endPoint}`);
            console.log(res)
            if(!res.ok){
                throw new Error('http Error');
            }
            return await res.json();
        }
        catch(e) {
            throw new Error(`무언가 잘못되었습니다. ${e.message}`)
        }
    }
    //
        request(endPoint) {
        return axios.get(`${entryPiont}${endPoint}`)
        .then((res)=>res.data)
        .catch((error)=>{
        if(error.response) {
            // 요청이 이루어졌으며 서버가 2XX의 범위를 벗어나는 상태코드로 응답
            console.log(error.response.data);
            console.log(error.response.status);
            console.log(error.response.headers);
        }
        else if(error.request) {
            // 요청이 이루어 졌으나 응답을 받지 못함
            // `error.request`는 브라우저의 XMLHttpRequest 인스턴스 또는
            // Node.js의 http.ClientRequest 인스턴스입니다.
            console.log(error.request);
        }
        else {
            // 오류를 발생시킨 요청을 설정하는 중에 문제가 발생했습니다.
            console.log('Error', error.message)
        }
        console.log(error.config);
        })
    }
    //
      async request(endPoint) {
        try {
            const res = await axios.get(`${entryPiont}${endPoint}`)
            return res.data;
        }
        catch(error){
        if(error.response) {
            console.log(error.response.data);
            console.log(error.response.status);
            console.log(error.response.headers);
        }
        else if(error.request) {
            console.log(error.request);
        }
        else {
            console.log('Error', error.message)
        }
        console.log(error.config);
        }
    }

    axios.get('/사용자/12345', {
  validateStatus: 함수(상태) {
    // 상태 코드가 500 이상일 경우. 작은 것(500)이 간섭합니다.
    반환 상태 < 500;
  }
})


    <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```
