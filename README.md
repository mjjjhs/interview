
> **현 직장에서 진행하고 있는 프로젝트**  
> * Fuzecard
> * FuzeW
> * FuzeX
  
> **금일 발표 프로젝트**-**FuzeX Commerce**  
>  
>FuzeX 프로젝트의 토이프로젝트로 FuzeW 라는 하드웨어 월렛 기반의 콜드월렛 형태의 암호화폐 지갑을 암호화폐(현재 ERC20-FXT만 개발. 차후 버전업시에 비트코인캐시 및 이더리움 등 추가.)로 결제하여 구매하는 프로세스의 프로젝트  
>  
> **해당 프로젝트를 선정한 이유**  
>  
>어제 릴리즈한 가장 최신의 프로젝트이고 페이지 2개의 아주 간단한 프로젝트라서 아직 제 머리에 코드의 내용이 남아 있는 프로젝트라서 발표 주제로 선정  
>    
* * *  
>  
> **프로젝트 설명**  
>  
>설명 내용은 시나리오 화면과 해당 시나리오 구현 소스 중 포인트가 되는 부분을 설명하겠습니다.  
>  
>1. 구조 및 사용 스택  
>  
><img src="https://user-images.githubusercontent.com/4207593/54216452-03bbe080-452d-11e9-8741-3cfa7d385a79.png" width="70%">  
><img src="https://user-images.githubusercontent.com/4207593/54216643-601f0000-452d-11e9-942b-a7d52714ee50.png" width="50%">  
><img src="https://user-images.githubusercontent.com/4207593/54219659-497ba780-4533-11e9-8521-9bc46a2593bc.png" width="70%">  
>  
>해당 프로젝트 구조는 이렇게 되어 있습니다.  
>사용 스택은 Vue Nuxt, Vuex, bootstrap-vue, web3, socket.io, axios등을 사용했습니다.  
>  
>2. 진입 화면  
>  
>PC 화면 -  
>  
><img src="https://user-images.githubusercontent.com/4207593/54199765-19211280-450d-11e9-85ef-aea8f597cd43.png" width="70%">  
>  
>모바일 화면 -  
>  
><img src="https://user-images.githubusercontent.com/4207593/54200305-72d60c80-450e-11e9-93f4-f376995c66bf.png" width="50%">  
><img src="https://user-images.githubusercontent.com/4207593/54200303-723d7600-450e-11e9-99ad-2d0eda7b278f.png" width="50%">  
><img src="https://user-images.githubusercontent.com/4207593/54200304-72d60c80-450e-11e9-98d5-1acd51a31534.png" width="50%">  
>  
>소스 -  
>  
><img src="https://user-images.githubusercontent.com/4207593/54220757-7630be80-4535-11e9-8ec8-82385c67fe9d.png" width="70%">  
>  
>shopify 솔루션에서 shopify의 상품정보를 암호화(aes-256 + salt)해서 URL에 파라미터로 삽입하여 해당 페이지를 호출하면서 시나리오가 시작됩니다.  
>  
><img src="https://user-images.githubusercontent.com/4207593/54219996-bdb64b00-4533-11e9-9974-81ba21314762.png" width="90%">  
>  
>UI는 bootstrap-vue를 최대한 이용했습니다. 현 직장에 따로 디자이너가 없는 이유도 있으나 토이 프로젝트이다 보니 최대한 스스로 해보고자 했습니다.  
>  
><img src="https://user-images.githubusercontent.com/4207593/54220350-8e540e00-4534-11e9-8cfd-c89484539f0e.png" width="90%">  
>  
>해당 route를 타게되면 위와같은 Node.js에서 URL에 대한 validation check를 하고 true이면 해당 뷰를 그리고 스크립트를 실행합니다. false이면 설정해놓은 error 페이지를 노출합니다. 이전에 말한 암호화된 파라미터를 복호화해서 Vuex Store에 저장을 합니다.  컴포넌트나 다른 route 페이지에서 사용할 데이터는 최대한 Store에 저장해서 사용합니다.  관리가 편하고 props로 컴포넌트마다 들고 다닐 필요가 없을 뿐더러 잘못 수정해버리는 실수를 줄일 수 있습니다.  
>  
><img src="https://user-images.githubusercontent.com/4207593/54221453-e25ff200-4536-11e9-96ca-fa530d167930.png" width="70%">  
><img src="https://user-images.githubusercontent.com/4207593/54221463-e55ae280-4536-11e9-96f1-c521f354d8b6.png" width="70%">  
><img src="https://user-images.githubusercontent.com/4207593/54222235-59e25100-4538-11e9-88ea-9a23f05dcae4.png" width="90%">  
>  
>정규식을 이용한 validation을 진행했고  
>  
><img src="https://user-images.githubusercontent.com/4207593/54222313-7ed6c400-4538-11e9-8a14-e0690136f909.png" width="70%">  
><img src="https://user-images.githubusercontent.com/4207593/54221950-cc066600-4537-11e9-940e-56a244430db6.png" width="70%">  
><img src="https://user-images.githubusercontent.com/4207593/54222404-b2b1e980-4538-11e9-9e49-2996e58992d9.png" width="90%">  
>  
>E_164 및 ISO_3166 + google library를 재작성한 libphonenumber-js를 이용하여 국내 및 국제 전화번호 validation 기능도 추가하였습니다.  
>  
><img src="https://user-images.githubusercontent.com/4207593/54222705-4be10000-4539-11e9-8593-71dc5c00ab7b.png" width="90%">  
>  
>input 및 selectbox 및 checkbox 등의 value를 변수에 v-model로 설정하여 양방향으로 바라보게 하였고 해당 변수에 watch를 설정하여 인풋의 값을 수정하여 v-model이 변경되면 그것을 바라보던 watch가 작동하여 모든 데이터의 유효성을 체크하여 모두 유효하면 checkout 버튼을 활성화합니다. 그러나 v-model은 붙여넣기를 하면 반응을 하지않아
대응방안으로 focusout을 한번 더 걸어 체크를 하였습니다.  
>  
><img src="https://user-images.githubusercontent.com/4207593/54223882-c90d7480-453b-11e9-98bd-544edc34bf0b.png" width="70%">  
><img src="https://user-images.githubusercontent.com/4207593/54223977-fb1ed680-453b-11e9-9fe6-f459494ab328.png" width="90%">  
>  
>체크아웃 버튼 클릭시 axios post로 데이터를 구매자의 개인정보가 있기때문에 aes-256 + salt 로 암호화하여 서버로 Request 합니다. Promise를 이용하여 콜백처리하는 것보다 async await가 더욱 간결하기 때문에 애용합니다. 발표 준비를 하다 보니 try catch문을 넣었으면 더 좋았을 것 같다는 생각을 하게 됐습니다. 서버와 정상적으로 통신이 됐다면 Store에 필요한 data들을 dispatch합니다.  
>  
>3. 결제 송금 화면  
>  
><img src="https://user-images.githubusercontent.com/4207593/54223616-38369900-453b-11e9-8ba3-ba238574592c.png" width="70%">  
><img src="https://user-images.githubusercontent.com/4207593/54224824-a8deb500-453d-11e9-96c2-c44e0f48df76.png" width="90%">  
>  
>해당 페이지의 URL 파라미터로 이더리움(ERC20) 서버쪽에서 생성한 지갑 주소를 넣어 URL을 호출합니다. web3를 이용하여 이더리움 주소의 유효성을 검사하고 Store에 미리 저장되어 있는 이더리움 주소와도 비교하여 true와 false를 리턴하여 true일 경우 해당 페이지의 Dom을 그리고 스크립트를 시작합니다.  
>  
><img src="https://user-images.githubusercontent.com/4207593/54225621-77ff7f80-453f-11e9-870d-354ec7b8445d.png" width="90%">  
><img src="https://user-images.githubusercontent.com/4207593/54225633-7df56080-453f-11e9-9e68-8c8865efa1a8.png" width="90%">  
>  
>웹소켓을 서버와 연결하여 구매자가 실제 송금을 했는지 송금을 했다면 적게 혹은 더 많이 송금을 했는지 서버측에서 클라이언트측으로 메시지를 보냅니다.  
>  
><img src="https://user-images.githubusercontent.com/4207593/54228029-9e73e980-4544-11e9-8bb9-59d59c9a6c3e.png" width="70%">  
><img src="https://user-images.githubusercontent.com/4207593/54228079-be0b1200-4544-11e9-9bec-594e9240b14a.png" width="70%">  
>  
>웹소켓 메시지에 따른 팝업이 노출되어 구매자에게 현재 상태를 알립니다.  
>송금 상태를 디텍팅하고 구매액과 같은 암호화폐를 입금하면 성공 팝업을 노출하고 송금 상태를 디텍팅 했지만 송금 내역에 이상이 있을 경우 알람 팝업이 노출됩니다.  
>  
><img src="https://user-images.githubusercontent.com/4207593/54226353-fdcffa80-4540-11e9-8d99-c1a2b3a6a415.png" width="90%">  
>  
>interval로 progressbar를 60분을 맥스로 시간의 흐름과 동시에 진행합니다.  
>구매자는 1시간 안에 송금을 해야하고 미송금시 해당 이더리움 주소는 파기됩니다.  
>데이터베이스의 시간은 UTC로 되어 있기 때문에 localtime과 9시간 차이가 있습니다.  
>  
><img src="https://user-images.githubusercontent.com/4207593/54227306-fc073680-4542-11e9-8912-2fc23683e4c5.png" width="90%">  
>  
>글로벌 서비스로 기획되어 개발되었기 때문에 서버시간에 getTimezoneOffset을 이용한 서버시간과 로컬시간의 차이를 구해서 더한 시간으로 로컬시간과의 차이를 구하여 progressbar의 시간을 구합니다.  
>  
><img src="https://user-images.githubusercontent.com/4207593/54227679-cf075380-4543-11e9-9502-324de260a6e9.png" width="90%">  
>  
>qrcode 패키지를 이용하여 이더리움 표준 형식에 맞게 문자열을 만들어 주고 qrcode를 생성 합니다. 구매자는 해당 qrcode를 암호화폐 지갑을 이용하여 스캔하여 편리하게 송금을 할 수 있습니다.  
>  
* * *  
>  
> **마치며..**  
>  
>과도하게 심플한게 아닌가 하는 걱정도 들지만 그런것이 토이프로젝트의 묘미가 아닌가 싶기도 합니다. 발표할 기회를 마련해주셔서 정말 감사드리고 입사 여부와 상관없이 경청해주신 면접관분들께도 감사드린다는 말을 전하면서 발표를 마치겠습니다. 감사합니다.
