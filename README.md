# SSL-
lDap SSL인증서 문제 해결

OpenSSL
1.
>openssl s_client -connect url:port -showcerts

3.
----BEGIN CERTIFICATE----
----END CERTIFICATE----
부분 복사해서 {파일명}.crt ex) ldap.crt 생성

4.
crt 생성한 경로 > keytool -import -v -trustcacerts -alias {등록할 인증서 별칭} -file {파일명}.crt -keystore {"java cacerts 경로"} -keypass changeit -storepass changeit

"java cacerts 경로" window시 경로는 ""감싸줘야한다.
ex) "C:\PRogram Files\Java\jdk1.8.0_181\jre\lib\security\cacerts"

5.
>keytool -list -keystore "C:\PRogram Files\Java\jdk1.8.0_181\jre\lib\security\cacerts" | findstr "{등록한 인증서 별칭}"
ex) findstr "ldap"

추가한 인증서가 등록된걸 확인
