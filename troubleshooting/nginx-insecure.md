* 브라우저 blocked:mixed-content 이슈 발생 시 조치 방안
  
  add_header Content-Security-Policy "upgrade-insecure-requests";

  브라우저에게 HTTP로 요청하는 리소스를 HTTPS로 자동 변경해서 사용하라고 지시하는 CSP(Content Security Policy) 설정
