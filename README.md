# javascript_02_20201126
javascript_02


--------------------
##. js_05.html
--------------------

    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="utf-8">
      <title></title>

      <script type="text/javascript">

    //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
    // 전역변수 no 선언하기
    //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
    var no=0;
    //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
    // 국영수 점수 3개를 입력받아 총점을 리턴하는 함수 선언하기
    //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

    function getTot(kor, eng, math){


      //실행구문;
      //총점을 저장하는 지역변수 tot 선언.
      var tot = kor + eng + math;

      return tot;
    }
    //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
    // 국영수 점수 3개를 입력 받아 평균을 리턴하는 함수 선언하기
    //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

    function getAvg(kor,eng,math){
    //총점을 저장하는 지역변수 tot를 선언하고
    //총점 구하는 함수를 호출하는 총점을 선물받아 tot에 저장

      var tot = getTot(kor,eng,math);
      //평균 저장하는 지역변수 avg 선언
      var avg = tot/3;
      // 함수를 중단하고 avg 변수안의 데이터를 반환
      return avg;

    }
    function getHakjum(kor,eng,math){

     var avg = getAvg(kor,eng,math);
     var hakjum = "F";
     if (avg >=90 && avg <=100){
      hakjum = "A";
     }else if(avg>=80 && avg <90){
      hakjum = "B";
     }else if(avg>=70 && avg <80){
      hakjum = "C";
     }else if(avg>=60 && avg <70){
      hakjum = "D";
     }
     return hakjum;
    }

    //------------------------------
    // 국,영,수 점수 3개를 입력 받아 합격, 불합격을 리턴하는 함수 선언.
    // 합격 기준 => 평균 60점 이상이고 모두 40점 이상
    //------------------------------ 
    function getPass(kor, eng, math){
      // 평균을 저장하는 지역변수 avg 선언
      // 평균 구하는 함수를 호출하여 평균을 선물 받아 avg 저장
      var avg = getAvg(kor,eng,math);
      // 변수 result에 "불합격 저장하기
      var result = "불합격 ";


      // 불합격 메시지를 저장할 msg 변수 선언하고 ""저장하기
      var msg = "";
      // 평균이 60 이상이고, 각 점수가 40 이상이면 합격 저장
      if(avg>=60 && kor >=40 && eng >=40 && math >=40 ){
        result = "합격";
      // 만약 result 변수안에 불합격이 저장되어 있으면
      }else{
        msg = msg + "( ";
        var cnt = 0;
        if (avg<60){
          if(cnt++>0){msg = msg + ", ";}
          msg = msg + "평균 60점 이하";
        }
        if (kor<40){
          if(cnt++>0){msg = msg + ", ";}
          msg = msg + "국어점수 40점 이하";
        }
        if (eng<40){
          if(cnt++>0){msg = msg + ", ";}
          msg = msg + "영어점수 40점 이하";
        }
        if (math<40){
          if(cnt++>0){msg = msg + ", ";}
          msg = msg + "수학점수 40점 이하";
        }
        msg = msg + " )";
      }
      // result 변수안의 데이터 리턴
      return result +msg;
    }

    //--------------------------------
    // 학생명, 국영수 점수 3개, 총점, 평균, 합격여부 등의 데이터를 
    // 테이블 태그에 넣어서 리턴하는 함수
    //--------------------------------
    function getSungjukInfo( stu_name, kor, eng, mat){
      //--------------------------------
      // 총점 저장하는 지역변수 tot 선언하고
      // getTot 함수를 호출하여 총점을 얻어 tot 변수에 저장하기
      //--------------------------------
      var tot = getTot(kor, eng, mat);
      //--------------------------------
      // 평균 저장하는 지역변수 avg 선언하고
      // getAvg 함수를 호출하여 총점을 얻어 avg 변수에 저장하기
      //--------------------------------
      var avg = getAvg(kor, eng, mat);
      // avg = Math.round(avg); // 소수점 반올림
      // avg = Math.floor(avg); // 소수점 내림
      // avg = Math.ceil(avg); // 소수점 올림
      avg = avg.toFixed(1); //괄호()안의 숫자는 소수점 몇째자리 까지 보여줄것인가


      //--------------------------------
      // 합격여부 저장하는 지역변수 pass 선언하고
      // getPass 함수를 호출하여 합격여부를 얻어 pass 변수에 저장하기
      //--------------------------------
      var pass = getPass(kor, eng, mat);
      //--------------------------------
      // 학점 저장하는 지역변수 hakjum 선언하고
      // getHakjum 함수를 호출하여 학점을 얻어 hakjum 변수에 저장하기
      //--------------------------------
      var hakjum = getHakjum(kor, eng, mat);
      //--------------------------------
      // HTML 태그 문자열 저장하는 지역변수 html_src 선언하고
      // HTML 태그 문자열 저장하기
      //--------------------------------
      var html_src =
      // "<table border=1 align=center>"
      // + "<tr bgcolor='lightblue'><th>학생명<th>총점<th width='150'>평균<th>학점<th>합격여부</tr>"+
      "<tr align=center>"
      + "<td>"+(++no)+"</td>"
      + "<td>"+stu_name+"</td>"
      + "<td>"+tot+"</td>"
      + "<td>"+avg+"</td>"
      + "<td>"+hakjum+"</td>"
      + "<td>"+pass+"</td>"
      + "</tr>";


      //----------------------------
      // html_src 변수 안의 문자열 리턴하기
      //----------------------------

      return html_src
    }






    </script>
    </head>
    <body>

      <script type="text/javascript">



        //-------------------------
        // 전역변수 kor, eng, mat 선언하고 점수 입력하기
        //-------------------------
        // var kor = 20, eng = 30, mat = 35;
        // var kor = 20, eng = 99, mat = 88;
        // var kor = 99, eng = 30, mat = 99;
        // var kor = 77, eng = 88, mat = 35;
        // var kor = 20, eng = 30, mat = 75;
        // var kor = 80, eng = 30, mat = 25;
        // var kor = 30, eng = 80, mat = 25;

        //-------------------------
        //getTot 함수 호출하여 얻은 총점 출력하기
        //-------------------------
        // document.write("사오정 총점 : " + getTot(kor,eng,mat)+"<hr>");
        //-------------------------
        //getAvg 함수 호출하여 얻은 평균 출력하기
        //-------------------------
        // document.write("사오정 평균 : " + getAvg(kor,eng,mat)+"<hr>");
        //---------------------------------
        //getHakjum 함수 호출하여 얻은 학점 출력하기
        //---------------------------------
        // document.write("사오정 학점 : "+getHakjum(kor,eng,mat)+"<hr>");
        //---------------------------------
        //getPass 함수 호출하여 얻은 합격(불합격) 출력하기
        //---------------------------------
        // document.write("사오정 결과 : "+getPass(kor,eng,mat)+"<hr>");

        //------------------------------
        // getSungjukInfo함수 호출하여 얻은 문자열을 body 태그 안에 출력하기
        //------------------------------
        document.write("<table border=1 align=center>"
        + "<tr bgcolor='lightblue'><th>번호<th>학생명<th>총점<th width='150'>평균<th>학점<th>합격여부</tr>");
        document.write(getSungjukInfo("황보면",80,100,50));
        document.write(getSungjukInfo("차승윤",45,10,30));
        document.write("</table>");
      </script>

    </body>
    </html>




--------------------
##. js_06.html
--------------------
<--
    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="utf-8">
      <title></title>

      <script type="text/javascript">
        function getSum(num){
          var tot = 0;
          for(var i=0;i<=num ; i++){

            tot=tot+i;
          }
          return tot;

        }


      </script>



    </head>
    <body>
      <script type="text/javascript">
        document.write("합계 : " + getSum(5) + "<br>");
        document.write("tot값 : " + tot + "<br>");
      </script>

    </body>
    </html>
    <!-- 
    --------------------------------------------------
    <문>에러 이유는?
    --------------------------------------------------
      => 에러발생 지점은 document.write("tot값 : " + tot + "<br>"); 
      => 함수 안에서 var 로 선언된 지역 변수는 함수 외부에서 호출 불가능
      => var tot = 0; 에서 var를 생략하면 전역변수가 되므로 호출 가능
    -------------------------------------------------- 


     -->








--------------------
##. js_07.html
--------------------
      <!--
      <1단계> prompt 상자 띄우고 [아이디] 입력
      --------------------
      <2단계> [아이디]가 "abc"일 경우 <3단계> 이동, 아닐 경우 <1단계>로 이동
      --------------------
      <3단계> prompt 상자 띄우고 [암호] 입력
      --------------------
      <4단계> [암호]가 "123"일 경우 <5단계> 이동, 아닐 경우 <3단계>로 이동
      --------------------
      <5단계> 웹 화면에 "로그인 성공..." 출력

     -->





    <!DOCTYPE html>
    <html>
    <head>
      <meta charset="utf-8">
      <title></title>

      <script type="text/javascript">





      </script>


    </head>
    <body>
      <script type="text/javascript">

        //-------------------------
        // 아이디를 체크하는 함수 선언.
        // 아이디를 잘못 입력하면 계속 아이디를 입력하라고 한다.
        //-------------------------
        function check_id(){
          // prompt 상자를 띄우고 아이디를 입력 받아 변수에 저장하기
          var id = prompt("아이디 입력 요망","");
          // 만약 아이디가 abc가 아니면 check_id()함수 호출하기
          if(id!="abc"){
            check_id();
          }

        }


        //-------------------------
        // 암호를 체크하는 함수 선언.
        // 암호를 잘못 입력하면 계속 아이디를 입력하라고 한다.
        //-------------------------
        function check_pwd(){
          // prompt 상자를 띄우고 아이디를 입력 받아 변수에 저장하기
          var pwd = prompt("암호 입력 요망","");
          // 만약 아이디가 abc가 아니면 check_id()함수 호출하기
          if(id!="123"){
            check_pwd(); //자기가 자기함수를 부른다고 해서 [재귀함수호출]이라고 한다.
          }

        }

        // check_id 함수를 호출하고 호출이 끝나면 check_pwd 함수 호출하고 호출이 끝나면
        // 로그인 성공 출력하는 함수 선언
        // 이 함수는 실질적으로 아이디, 암호를 체크하지는 않고 전체 프로그램의 컨트롤 역할만 하고 있다.
        function controll(){
          //check_id() 함수 호출로 아이디 체크하기
          // <주의> check_id() 함수가 완전히 끝나야 다음 코드가 실행된다.
          check_id();
          //check_pwd() 함수 호출로 아이디 체크하기
          // <주의> check_pwd() 함수가 완전히 끝나야 다음 코드가 실행된다.
          check_pwd();
          document.write("로그인성공...");
        }
        controll();




      </script>

    </body>
    </html>



~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
##. js_08.html
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


<!-- 
	<1단계> prompt 상자 띄우고 [아이디] 입력
	--------------------
	<2단계> [아이디]가 "abc"일 경우 <3단계> 이동, 
			2회 까지 아닐 경우 <1단계>로 이동
			3회 까지 아닐 경우 웹화면에 "로그인 실패" 출력하고 중단.
	--------------------
	<3단계> prompt 상자 띄우고 [암호] 입력
	--------------------
	<4단계> [암호]가 "123"일 경우 <5단계> 이동.
			2회 까지 아닐 경우 <3단계>로 이동.
			3회 까지 아닐 경우 웹화면에 "로그인 실패" 출력하고 중단.
	--------------------
	<5단계> 웹 화면에 "로그인 성공..." 출력
 -->


    <!DOCTYPE html>
    <html>
    <meta charset="utf-8">
    <head>
      <title></title>
          <script type="text/javascript">
		
		//-------------------------
		// 아이디를 체크하는 함수 선언.
		// 아이디를 잘못 입력하면 계속 아이디를 입력하라고 한다.
		//-------------------------
		var idErrorCnt= 0;
		var pwdErrorCnt=0;
		var id_lastChance=3;
		var pwd_lastChance=3;

		function check_id(){
			// prompt 상자를 띄우고 아이디를 입력 받아 변수에 저장하기
			var id = prompt("아이디 입력 요망","");
			// 만약 아이디가 abc가 아니면 check_id()함수 호출하기
				
				//-----------------
				//만약 아이디가 abc 가 아니면
				//-----------------
				if(id!="abc"){
					//idErrorCnt 변수안의 데이터 1증가
					idErrorCnt++;
					//만약 idErrorCnt 변수안의 데이터가 id_lastChance 변수안의
					//데이터보다 미만이면 check_id() 함수 호출
					if(idErrorCnt<id_lastChance){
					check_id();
					}
				}
			
			}
		


		//-------------------------
		// 암호를 체크하는 함수 선언.
		// 암호를 잘못 입력하면 계속 아이디를 입력하라고 한다.
		//-------------------------
		
		function check_pwd(){
			// prompt 상자를 띄우고 아이디를 입력 받아 변수에 저장하기
			var pwd = prompt("암호 입력 요망","");
			// 만약 아이디가 abc가 아니면 check_id()함수 호출하기
			
				//-----------------
				// 만약 암호가 123이 아니면
				//-----------------
				if(pwd!="123"){
					//pwdErrorCnt 변수안의 데이터 1증가
					pwdErrorCnt++;
					//만약 pwdErrorCnt 변수안의 데이터가 id_lastChance 변수안의
					//데이터보다 미만이면 check_id() 함수 호출
					if(pwdErrorCnt<pwd_lastChance){
					check_pwd(); //자기가 자기함수를 부른다고 해서 [재귀함수호출]이라고 한다.
					}

				}
			}
		

		// check_id 함수를 호출하고 호출이 끝나면 check_pwd 함수 호출하고 호출이 끝나면
		// 로그인 성공 출력하는 함수 선언
		// 이 함수는 실질적으로 아이디, 암호를 체크하지는 않고 전체 프로그램의 컨트롤 역할만 하고 있다.
		//-----------------
		function controll(){
			
		//-----------------
			//check_id() 함수 호출로 아이디 체크하기
			// <주의> check_id() 함수가 완전히 끝나야 
			// 다음 코드가 실행된다.
			//-----------------
			check_id();
			//-----------------
			if (idErrorCnt==id_lastChance){
				document.write("[아이디]"+idErrorCnt+"회 잘못 입력으로 로그인실패...");
				return;
			}
			
			//-----------------
			//check_pwd() 함수 호출로 아이디 체크하기
			// <주의> check_pwd() 함수가 완전히 끝나야 다음 코드가 실행된다.
			//-----------------
			check_pwd();
			//-----------------
			//만약 pwdErrorCnt 변수안의 데이터가 pwd_lastChance 변수안의 숫자와 일치하면
			// 경고하고, 로그인 실패 메시지를 출력하고 함수중단
			//-----------------
			
			if (pwdErrorCnt==pwd_lastChance){
				document.write("[암호]" + pwdErrorCnt+"회 잘못 입력으로 로그인실패...");
				return;
			}
			// body 태그 안에 "로그인 성공" 문자열 출력. 
			document.write("로그인성공...");
		}
	</script>
    </head>
    <body>

      <script type="text/javascript">

        controll();	  



      </script>
    </body>
    </html>
<!-- 
------------------------------------------
<문1> control(); 코딩을 funtion check_id(){} 코딩 이전으로 옮기면?
    즉 함수 선언 이전에 함수 호출 코딩이 나온다면?
------------------------------------------
	에러 없이 그대로 호출이 된다.
	웹브라우저는 html 파일을 읽어들일 때 함수만 먼저 뽑아서 읽어들인다.
	그 이후 위에서 아래로 차례대로 읽어들인다.

     -->


   
~~~~~~~~~~~~~~~~~~~~~~~~~
##. js_09.html
~~~~~~~~~~~~~~~~~~~~~~~~~
    <!-- 
      Array 객체의 쓰임새를 공부한다.
      Array 객체는 자바의 [배열 객체]와 거의 동일하다.
      다량의 데이터를 한 곳에 저장하고자 할 때
      사용하는 것이 Array 객체이다.
      Array 객체의 각종 메소드를 사용하면 다량의 데이터를 원하는대로 가공할 수 있다.
     -->

    <!DOCTYPE html>
    <html>
    <meta charset="utf-8">
    <head>
      <title></title>
    </head>
    <body>
      <script type="text/javascript">
        //**************************
        // 변수 kors 선언하기
        // 다량의 국어 점수를 관리하기 위해
        // Array 객체 생성하고 객체의 메위주를 kors 에 저장하기.
        //**************************
        // <주의> 객체의 메위주를 가지고 객체의 [속성변수]나 [메소드]를 호출하여
        // 받는 이익이 상당하다. 
        // 즉 객체의 생성목적은 객체의 속성변수나 메소드의 호출이다.
        //**************************
        var kors = new Array();
        //**************************
        // Array 객체의 push(~) 라는 메소드를 호출하여 Array 객체에 데이터 5개를 저장하기
        // 저장된 데이터는 배열변수라는 곳에 저장된다.
        // 5개의 데이터를 저장했으면 [배열변수]도 5개 생성된다.
        // 이때 배열변수의 이름은 kors[0] ~kors[4]
        //**************************
        kors.push(80);
        kors.push(90);
        kors.push(70); 
        kors.push(60);
        kors.push(9);
        document.write("모든 국어 점수 출력 => ");

        for(var i=0; i<kors.length; i++){
        document.write(kors[i] + " ");
        }


        document.write("<hr>");


        //-----------------
        // join(문자열) 메소드?
        //-----------------
          // 모든 배열변수 안의 데이터를 모두 붙여서 문자열로 리턴한다.
          // 이때 매개변수로 전달되는 문자가 붙일 때 중간에 삽입되는 문자이다.
          // <참고> 메소드가 나오면 기억해야할 것 => 기능, 리턴값, 매개변수로 전달되는 데이터

        document.write("모든 국어 점수 출력 => " + kors.join(","));
        // 배열 변수안의 데이터 다 꺼내세요.
        // 문자로 붙여 
        // 근데 그 중간에 괄호안에 걸 집어 넣어
        // 문자열로 리턴해주는 메소드가 join 메소드



        // *******************************
        // 국어 점수를 오름차순으로 정렬하기
        // (=첫번째 배열변수 안에 제일 작은 데이터를 저장하고 차례대로 작은 데이터를 배열변수에 저장하기)
        // *******************************


        // *******************************
        // 배열변수 안의 데이터를 숫자 취급해서 오름차순으로 정렬하기
        // (=첫번째 배열변수 안에 제일 작은 데이터를 저장하고 차례대로 작은 데이터를 배열변수에 저장하자)
        // sort 메소드를 호출하면서 매개변수로 아래와 같은 익명함수를 던져주면 오름차순으로 바꾸는데
        // 이 익명함수를 사용한다.
        // function(left,right)(return left-right;)
        // *******************************

        kors.sort( function(left,right){return left-right;});




        // for( var i=0; i<kors.length-1 ; i++){
        // 	for(var j=i+1 ; j<kors.length; j++){

        // 		if(kors[i]>kors[j]){
        // 			var tmp = kors[i];
        // 			kors[i] =kors[j];
        // 			kor[j] = tmp;
        // 		}

        // 	}
        // }
        document.write("<hr>")
        document.write("오름차순 정렬 후 모든 국어점수출력 =>" + kors.join(""))

        // var xxx = function(left,right){return left-right;};

        // document.write(xxx(3,5));

        var engs = [99, 88, 77, 66, 55];
        engs.push(44) // 추가한다
        document.write("<hr>")
        document.write("모든 영어 점수 출력 => " + engs.join(""))


      </script>

      </body>
      </html>














