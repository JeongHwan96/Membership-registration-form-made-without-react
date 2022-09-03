<p align="center">
  <h1 align="center">Vanilla JS를 활용한 회원가입 폼✨</h1>

  <p align="center">
Vanilla JS를 사용하여 만든 회원가입 폼 입니다  <br> 현재까지 진행 중인 작업물은 <a href="https://whimsical-choux-aaf670.netlify.app/">여기서</a>에서 확인하실 수 있습니다.
  <br/>
  내용 추가와 수정이 있다면 변경되는대로 바로바로 올리겠습니다! 😊 
  <br/> 
  <br>
  (해당 폼은 마켓컬리 회원가입 폼을 참고하여 제작 하였습니다 🥰 )
  <br/>
  <br/>
  🛠  Technical Skills 
  <br/>
  <br/>
    <img src="https://img.shields.io/badge/-HTML-0088CC?style=flat&logo=HTML"/>
     <img src="https://img.shields.io/badge/-CSS-CC2277?style=flat&logo=CSS"/>
  <img src="https://img.shields.io/badge/-VanillaJS-F7F8E0?style=flat&logo=VanillaJS"/>
  <br/>
  <br/>
  
</p>

## Project Introduction ❤️

- 회원 가입을 할 수 있는 페이지 입니다
- html, css, vanilla js 등을 사용하여 제작 하였습니다
- 감사합니다~❤️❤️

## Simple Description ✨

<p align="center">
  <img src="https://user-images.githubusercontent.com/76175940/186162249-d8f67333-9bee-4412-a0f9-204c7cb04d41.gif">
  </p>
  
## Develop History 📜

2022-09-03

중복확인 버튼 기능 구현 시작

2022-09-01

가입하기 입력시 마지막 체크 기능 구현 시작

2022-08-30

- 생년월일 정규표현식 기능 적용 완료
- 추가입력 사항 기능 구현 완료
- 이용약관동의 체크박스 기능 구현 완료

2022-08-25

-생년월일 정규표현식 기능 적용

2022-08-23

- 카카오 주소 API 사용
- 인증번호 입력 창 카운터 기능 적용 완료

2022-08-11

-비밀번호, 이름 정규 표현식 작업 완료

//비밀번호<br><br>
$('#pw1').on({<br>
keyup: function(){<br>
const regExp1 = /.{10,}/g;
const regExp2 = /((?=._[A-Za-z])+((?=._[0-9])+|(?=.\*[\!\@\#\$\%\^\&\*\_\-])+)+)+[^\s][A-Za-z0-9\!\@\#\$\%\^\&\*\_\-]/g;
const regExp3 = /(.)\1\1/g; //연속3자이면 true 이면 오류, 아니고 false 이면 정상

                    //1. 10자이상이 아니면
                    if( regExp1.test($(this).val())===false  ){
                        $('.guid-pw1').text('최소 10자 이상 입력');
                        $('.guid-pw1').addClass('error');
                    }
                    else{

                        //2. 영문(필수) + (숫자 또는 특수문자)필수 (공백 제외)만 허용하며, 2개 이상 조합
                        if( regExp2.test($(this).val())===false  ){
                            $('.guid-pw1').text('영문/숫자/특수문자(공백 제외)만 허용하며, 2개 이상 조합');
                            $('.guid-pw1').addClass('error');
                        }
                        else if( regExp3.test($(this).val())===true  ){
                            $('.guid-pw1').text('동일한 숫자 3개 이상 연속 사용 불가');
                            $('.guid-pw1').addClass('error');
                        }
                        else{
                            $('.guid-pw1').removeClass('error');
                        }
                    }
                }
            });

            //2-2 동일한 비밀번호를 입력
            $('#pw2').on({
                keyup: function(){
                    if( $('#pw1').val() !== $('#pw2').val()  ){
                        $('.guid-pw2').addClass('error');
                    }
                    else{
                        $('.guid-pw2').removeClass('error');
                    }
                }
            });<br><br>

            //이름
             $('#irum').on({<br>
                keyup: function(){<br>
                    // 오류가 있으면 삭제하고 정상문자만 입력된다.
                    const regExp = /[^A-Za-z0-9가-힣ㄱ-ㅎㅏ-ㅣ]/g;
                    if($(this).val()===''){
                        $('.guid-irum').addClass('error');
                    }
                    else{
                        $('.guid-irum').removeClass('error');
                        $(this).val( $(this).val().replace(regExp,'') );
                    }
                }
            })

2022-08-10

- 아이디 정규표현식 작업 완료

  $('#id').on({<br>
                keyup: function(e){
                    const regExp1 = /[`~!@#$%\^&_()\-\_=+\\\|\{\}\[\]'";:\/?.>,<]/g; //특수문자는 자동으로 삭제<br>
  const regExp2 = /.{6,16}/g; //6자이상<br>
  const regExp3 = /(?=._[A-Za-z])+(?=._[0-9])_[A-Za-z0-9]/g; //영문 또는 영문,숫자조합<br>

                    // 정규표현식.test(문자열); true 또는 false 6자이상, 영문혹은 영문숫자<br>
                    // 문자열.replace(정규표현식, '')  //특수문자는 삭제<br>
                    if( regExp1.test($('#id').val()) === true  ){ //특수문자이면<br>
                        $('#id').val( $('#id').val().replace(regExp1, '') ); //삭제<br>
                    }<br>
                    else if( regExp2.test($('#id').val()) === false ) { // 6~16 범위가 아니면<br>
                        $('.guid-id').addClass('error');<br>
                        $('.guid-id').text('최소 6자 이상 입력');<br>
                    }<br>
                    else if( regExp3.test($('#id').val()) === false ){<br>
                        $('.guid-id').addClass('error');<br>
                        $('.guid-id').text('영문 또는 영문,숫자조합');<br>
                    }<br>
                    else{<br>
                        $('.guid-id').removeClass('error');<br>
                        $('.guid-id').text('');<br>
                    }                    <br>
                }<br>
            });<br>

2022-08-09

- 입력창, 버튼 등 CSS 작업
- 생년월일 폼 HTML 작업
- 아이디 정규표현식 작업 시작

2022-08-05

- 이용약관 동의 부분 HTML 작업

2022-08-04

- Header부분(회원가입 Text 부분) HTML 작업
- 입력폼 HTML 작업
