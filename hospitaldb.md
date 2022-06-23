#병원관리 프로그램1


##외부 스키마 :
###환자
|성명|휴대전화번호|병명|주치의|<u>주민등록번호|
|----|-----------------|-------------|-----|-------------|

 (환자의 슈퍼키:성명,기본키:주민등록번호,외래키:주치의)
###의사
|소속|성명|<u>사번|휴대전화번호|주치환자성명|직급|
|-----|-----|---------|------------------|-----|-----|


(슈퍼키:성명 기본키:사번-외래키:주치환자성명)
####직원들
|소속|성명|<u>사번|휴대전화번호|직급|
|-----|-----|------|-------------|-----|

(슈퍼키:성명,기본키:사번)
###간호사
|소속|성명|사번|주치환자|
|-----|-----|--------------|-------|
(외래키:주치환자,소속,사번,성명)

###진료
|환자성명|의사성명|간호사성명|병명|<u>병명코드|
|-----|-----|------|-------------|-----|
외래키 전부

###진료과
|진료과명|의사성명|간호사성명|
|--------|-----|------|

모두외래키


-----------------------------------------------------------

연결성은 환자,의사,간호사이고  환자는 진료로  1:다로 연결됨

의사는 환자와 진료로 1:n로 연결

간호사는 환자와 진료로 1:n 연결

의사와 간호사는 직원들로 묶어지고 1:n 연결임.

의사와 간호사는 진료과에 1:1 연결

---------------------------------------------


##병원요구사항 명세서

1.환자는 진료를 받기위해 성명,휴대전화번호,주민등록번호를 말해야함
2.의사는 환자의 주치의가 되며 환자의 병명을 db에 입력해야함
3.환자는 주민등록번호와 성명으로 구분해야함
4. 의사또한 성명과 사번으로 구분
5. 의사는 간호사를 직원들에 배정받음.
6. 환자는 의사와 간호사를 진료로 묶어짐.
7. 환자는 주치의가 배정되면 바꿀수 없음
8. 의사는 환자와 1:n로 배정
9. 간호사는 환자와 1:n로 배정

-------------------------------------------------------------------

##ER다이어그램
![ER-diagram][logo]

[logo]:https://viewer.diagrams.net/?tags=%7B%7D&highlight=0000ff&edit=_blank&layers=1&nav=1&title=HOSPITAL%20D.B%20ERDIAGRAM#R5V1dl5s2EP01PJYD%2BgI92l43aZvsSc82TfrI2sSmxcbFbNbur69YJGMkZY1tQHLihz1GgLzMzJ25MxrZDpysdm%2FyaLN8n83j1AHefOfAOweAMAjZ33JgXw2gkA8s8mReDfn1wEPyX8wHPT76lMzjbePCIsvSItk0B2fZeh3PisZYlOfZc%2FOyL1na%2FNRNtIiVgYdZlKqjn5J5seSPBYJ6%2FG2cLJbik31CqzOrSFzMn2S7jObZ89EQnDpwkmdZUb1b7SZxWspOyOXTL%2FtP6bt%2FyJtff9%2F%2BG30c%2F%2FbH%2FZ8%2FVZP9fM4th0fI43Vx8dSjpykl9%2FcP4ce3u93nbeQ9LzN%2Bi%2Fc1Sp%2B4vJzpnUOpQ0NnOnHo1KHi6Yu9EGmePa3ncTmt58Dx8zIp4odNNCvPPjMbYmPLYpWyI5%2B9bfm%2F82f8GudFvDvSHH%2BWN3G2iot8zy7hZw9q4XYJKK6On2st%2B%2BKa5ZGGCR%2BLuGEtDlPXwmNvuPzOkCXQyHLijAInRM507IygE05UWS6z1ePT1pwcEZTl6Kly9DVyDPqSI1TlKEstXs9HpW9gR7M02m6TWVNYTQs9T3TxvOFQVMHlcRoVydemf9FJgd%2F6IUvY5x4EDiFqCBwC5OLmJNvsKZ%2FF%2FL5jSEtTybqDQJqoiPJFXCgTvajl8ESXawopmnoXPZbhQ1YXE2l1hqkm3ib%2FRY8vp7ym1qI0WaxLlTI9xTkbKK04Ya58xE%2Bskvm8vFGj0dcsiYcW%2FqG1Q28Bkta6vsriiSLH99fKMK%2BAqojwMSuKbDWkCHcN2Q0j0EDriukdD2shcEYaV2xDWCPWhbWwa3cc75Li89H7v8r3zAVWR3e7o1N3%2B4tceOU%2FT9tH366eINk%2FX%2Bzq8empenb2vq8Ywr0tXio05aW%2BEeKbupLuz7582cb9qEgNyLfi94CgLkJmxLTf87FWmCWf91%2BkOi5zI0bsKXRGSJWqeWJPJImaJva%2BynOuDCXnya5%2FZk%2BbEqdXMHsJDnRgZ68yKLuovbAl67m9r%2FIna8JmB0I0we59qvHMI2fsvVRaXoLd2PZ4R6yLd0BTC7x5oi9MpX%2BmL%2FvrK5j%2Byal6dv5AZfrW1COElf7oVB%2FqKve3SfURMO36oGrwmtJ9GWKgM7ayhi9L1DTVh6DrYHKe7Iam%2Bgh3RvURHtbbQ3W9xS6qL2zJeqoP1fKLNVS%2FAyGaoPpQV4S5capvQbzrvBBjAdUXpjI01b%2FC9ctUXzNV385frfPY47KMVScso%2FqaFbibadJpGvjB4M25vla1I%2BsZ%2FmE50BjDR52Xi86T3dAMHwedMXwcDNymo6a3djF8dH1RZxg6itS01ppw2YEQTTB8pGn3u3WGbz7MIU0nwM0zfGEqQzP8K1y%2FzPA1U%2FXt%2FNUM2ppivrDSH53ho%2FPy8XW2js%2BFqj%2Foqhu3ucq0X3vwto14R44Ua%2FyoGLtS%2F4g0DeAw79mw96SJWjZmMw1H%2B6PLNuUF215MTtci%2B%2B2wWy0tjavVEFJeo9hnmiabbWwuCEOC9Mo7sh1CVNsBvcVgTarZBapd6IWNIBzi19FdHnyI84Q9VknXjSJeKMUSxMtttQpQWyM%2BIG4z1AMYtAz1w6Eea5L2GuNjZwycUK1%2BGIe2skdJ0yyjMxJZmZ1BG5%2B3R%2BkUtI2BEdkFRkBdYX5C0z51cXAZJAm8CUjqerZFp0EZbUfOiFoISWobJDUrhTcabU%2FjlliFWwQV3EJ4KXNGMmghClwKbUOtJmNT12TK0Iqcsc9xHGL7cAwDSdqaXQJkUBxrEpPvFsehXTjGGhwHLghp%2FSIXwpoosMbYFaq1B9a6pValq%2FIGYH3oABTSDoEbAAXZgQ7Zpcb7AndfKTGhSAJ3YDolBi2dALEsI1ZJ%2BMXBXGXgVgZzosuKxyUFp1ZjXKLgLJS7YonEFAsnmk7qTgAeYtwAeOAj09GbALuAiz3Xk%2FJdD7k09OqXFG9b4zhUMmkfWJdJC32ctyXCOIyVEqSmtWdYDFtd3IKt4WlXcatKkmso%2Bg2lI0RdevxClyFVTZ8RsTHitvqiglvg2dJCH6LaGDw0zyZ9FcOIlEN7xlee2vsDu4pmOKAKUllG7B9F6wt9APGbX%2FyAgoDRpW%2FPa94b6IppN70WjcKmW8Ae0KrA1NI06avIRj3acBAEEeM03a4im0z3EFbWpFoDnfoulnhE4Lny%2F2Qe3%2Fqqmu2rzhhhV6ZptHSlCnaHpec91dB6ahY7ic%2FArvoXIlCKy5heWP6Su8CIZ1%2FSHOhrX%2BGYB9jyDb3xaAyltj7iqxm2jqGr3QLdfUFlX3Wy4QvhpwEOrAI4BsSF8CjVboI9vDQYYznzxiFw5TzePN6BFu%2B217qxr0DYRSqJHjQQBz9Qx0lgV%2FKMqOceZVMSSyPehRjGlLiiiizmAgzEUPkke%2FD8vTSiIIBdX5I9VHvKBu1FoboypeIsmXDHTOKIfxconbzypaA27laDmkb5YXer0fM8aU%2B71ZiY8z1fbUTimK82wsNAfe%2FLUePmnkudwhxPeuu2hKvjfXKwLmleu09OM1XP%2B%2BSo6kit2dor8GHpPjkoTdDfRjnabd2yY5JkWyePxJmh7L9bg9MHLsQYopBFZB%2BTJtsq204wI0YwZLkTgMi2CocvqjASjh%2F4YZYXy2yRraN0Wo9KhlJf8y7LNtyW%2Fo6LYs9%2F8Cp6KrJrovdp3x%2Ba8v3XRXZd6bcFg7KOnmLZ5%2BmbrbT0FClbWLqTb7fF4I4dIrVs6QV35RCxnQ6RHdY%2FR1ddXv%2BmH5z%2BDw%3D%3D

##정규화

의사,간호사,환자는 각각이 원자값으로 구성되어있음으로 제1정규형에 속함

###진료
|환자성명|의사성명|간호사성명|병명|<u>병명코드|
|-----|-----|------|-------------|-----|

|환자성명|의사성명|간호사성명|병명|<u>병명코드|
|-----|-----|------|-------------|-----|
|홍길동|김길동|홍두께|i4562,i9920|

#####제1정규형
|환자성명|의사성명|간호사성명|병명|<u>병명코드|
|-----|-----|------|-------------|-----|
|홍길동|김길동|홍두께|위염|i4562|
|홍길동|김길동|홍두께|기관지염|i9920|

#####제2정규형
병명코드정렬릴레이션

|<u>병명코드|환자성명|병명|
|-----|-----|----|
|i4562|홍길동|위염|
|i9920|홍길동|기관지염|

환자기록  릴레이션 (신설)
|<u>환자번호|환자성명|의사성명|간호사성명|
|---------|---------|---------|---------|
|p00001|홍길동|김길동|홍두께|

#####제3정규형 ,보이스코드

환자를 의사와 간호사 릴레이션으로 분리

|환자번호|환자성명|의사성명|
|---------|---------|---------|
|p0001|홍길동|김길동|

|환자번호|환자성명|간호사성명|
|---------|---------|---------|
|p0001|홍길동|홍두께|
