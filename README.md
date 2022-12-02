# MongoDB and WebFlux Test

### MongoDB Shell Script
```shell
$ mongo
```
위의 `mongo` 명령어는 오래되어 기본설치시에 설치가 되지 않는듯 하고, 아래 `mongosh`를 다운받아야 한다.
`mongosh`를 다운받아 설치폴더안의 `/bin`에 넣어주어 추가적인 환경변수 설정이 필요없었다. 
```shell
$ mongosh
```

```shell
$ mongosh # 아래의 명령어가 default로 설정되어있어 간단하게 mongosh로 입력하면 실행된다.
$ mongosh "mongodb://localhost:27017"
```

사용중인 데이터베이스 확인
```shell
> show dbs;

# result
admin    40.00 KiB
chatdb   40.00 KiB
config  108.00 KiB
local    72.00 KiB
```

```shell
> use <database name>;
```

```shell
chatdb> show collections;

#result
chat
```
```shell
chatdb> db.chat.find();

# result
[
  {
    _id: ObjectId("6389886b71d6074a0e48d628"),
    msg: '안녕 난 ssar이라고 해',
    sender: 'ssar',
    receiver: 'cos',
    createdAt: ISODate("2022-12-02T05:08:59.174Z"),
    _class: 'com.coen.monchat.Chat'
  }
]
```

```shell
db.runCommand({convertToCapped: 'chat', size: 8192}); # change buffer size

#result
{ ok: 1 }
```

---

프로젝트 동일 폴더 temp에 html 파일 있음