002-Regular expressions
==========

002.정규표현식 세미나

[정규표현식 테스트 URL](http://www.regexr.com)
[정규표현식 도식화 URL](http://www.regexper.com)

### 2.Javascript Syntax
    var str = "#id";
    var re = /^(?:#([\w-]+)|(\w+)|\.([\w-]+))$/g;
    var re = new RegExp("^(?:#([\\w-]+)|(\\w+)|\\.([\\w-]+))$", "g");
    console.log(re.exec(str));
    console.log(str.match(re));
    console.log(re.test(str));
    
    var str = "abc de";
    console.log(str.split(/\s+/));	

### 4. “\”(Backslash)
    ("$12$ \-\ $25$").match(/^$/g);
    ("$12$ \-\ $25$").match(/\$/g);
    ("$12$ \\-\\ $25$").match(/^\$/g);    
    ("$12$ \\-\\ $25$").match(/\$$/g);
    ("$12$ \\-\\ $25$").match(/\\/g); 

### 5. “.”(Point)    
    ("Regular expressions are powerful!!! O.K.").match(/./g);     
    ("Regular expressions are powerful!!! O.K.").match(/....../g);
    ("Regular expressions are powerful!!! O.K.").match(/\./g);       
    ("Regular expressions are powerful!!! O.K.").match(/\..\./g);    

### 6. “[]”(Square brackets)
    ("How do you do?").match(/[oyu]/g);
    ("How do you do?").match(/[hH]./g);
    ("How do you do?").match(/[owy][yow]/g);

### 7. “[-]”(Square brackets)  
    ("ABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyz 0123456789").match(/[C-K]/g);
    ("ABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyz 0123456789").match(/[C-Ka-d2-6]/g);
  
### 8. “[^]”  
    ("ABCDEFGHIJKLMNOPQRSTUVWXYZ abcdefghijklmnopqrstuvwxyz 0123456789").match(/[^CDW-Zghi45]/g);
  
### 9. “|”(Separate)
    ("Monday Tuesday Friday").match(/(on|ues|rida)/g);      
    ("Monday Tuesday Friday").match(/(Mon|Tues|Fri)day/g);
    ("Monday Tuesday Friday").match(/..(id|esd|nd)ay/g);
    
### 10. “*”&“+”&“?”
    ("aabc abc bc").match(/a*b/g);
    ("aabc abc bc").match(/a+b/g);
    ("aabc abc bc").match(/a?b/g);
    
    ("-@- *** -- \"*\" -- *** -@-").match(/.*/g);
    ("-@- *** -- \"*\" -- *** -@-").match(/-A*-/g);
    ("-@- *** -- \"*\" -- *** -@-").match(/[-@]*/g);

    ("-@@@- * ** - - \"*\" -- * ** -@@@-").match(/\*+/g);
    ("-@@@- * ** - - \"*\" -- * ** -@@@-").match(/-@+-/g);
    ("-@@@- * ** - - \"*\" -- * ** -@@@-").match(/[^ ]+/g);

    ("--XX-@-XX-@@-XX-@@@-XX-@@@@-XX-@@-@@-").match(/-X?XX?X/g); 
    ("--XX-@-XX-@@-XX-@@@-XX-@@@@-XX-@@-@@-").match(/-@?@?@?-/g); 
    ("--XX-@-XX-@@-XX-@@@-XX-@@@@-XX-@@-@@-").match(/[^@]@?@/g);
                           
    “\” 다음에 나오는 문자는 문자로 인식        
    “[^]” 괄호안에 문자가 아닌것을 표현        
    “*” 앞문자의 개수를 의미 0~n개를  표현     
    “+” 앞문자의 개수를 의미 1+n개를 표현      
    “?” 앞문자의 개수를 의미 0+1개를 표현      

### 11. “{}”    
    ("One ring to bring them all and in the darkness bind them").match(/.{5}/g); 
    ("One ring to bring them all and in the darkness bind them").match(/[els]{1,3}/g); 
    ("One ring to bring them all and in the darkness bind them").match(/[a-z]{3,}/g); 

    ("AA ABA ABBA ABBBA").match(/AB{0,}A/g);
    ("AA ABA ABBA ABBBA").match(/AB{1,}A/g);
    ("AA ABA ABBA ABBBA").match(/AB{0,1}A/g);

### 12. “*?”&“+?”&“??”
    ("One ring to bring them all and in the darkness bind them").match(/r.*/g);  
    ("One ring to bring them all and in the darkness bind them").match(/r.*?/g); 
    ("One ring to bring them all and in the darkness bind them").match(/r.+/g);                                                                           
    ("One ring to bring them all and in the darkness bind them").match(/r.+?/g); 
    ("One ring to bring them all and in the darkness bind them").match(/r.?/g);  
    ("One ring to bring them all and in the darkness bind them").match(/r.??/g); 
    
    ("<div>test1</div> <div>test2</div> <div></div> <div></div>").match(/<div>.*<\/div>/g); 
    ("<div>test1</div> <div>test2</div> <div></div> <div></div>").match(/<div>.*?<\/div>/g);
    ("<div>test1</div> <div>test2</div> <div></div> <div></div>").match(/<div>.+<\/div>/g);
    ("<div>test1</div> <div>test2</div> <div></div> <div></div>").match(/<div>.+?<\/div>/g);
    ("<div>test1</div> <div>test2</div> <div></div> <div></div>").match(/<div>.?<\/div>/g);
    ("<div>test1</div> <div>test2</div> <div></div> <div></div>").match(/<div>.??<\/div>/g);

    Greedy quantifier(탐욕적인 수량자) vs. Lazy quantifier(게으른 수량자)
    “\” 다음에 나오는 문자는 문자로 인식                                  
    “[^]” 괄호안에 문자가 아닌것을 표현                                  
    “*” 앞문자의 개수를 의미 0~n개를  표현                               
    “+” 앞문자의 개수를 의미 1~n개를 표현                                
    “?” 앞문자의 개수를 의미 0~1개를 표현                                

### 13. “\w”(word)    
    ("A1 B2 c3 d_4 e:5 ffGG77--__--").match(/\w/g);
    ("A1 B2 c3 d_4 e:5 ffGG77--__--").match(/\w+/g);
    ("A1 B2 c3 d_4 e:5 ffGG77--__--").match(/[a-z]\w*/g);
    ("A1 B2 c3 d_4 e:5 ffGG77--__--").match(/\w{5}/g);

### 14. “\W”(not word)
    ("AS _34:AS11.23 @#$ %12^*").match(/\W/g);

### 15.“\s”&“\S”(Space)
    ("One ring to bring them all and in the darkness bind them").match(/\s/g);
    ("One ring to bring them all and in the darkness bind them").match(/\S/g);
    ("One ring to bring them all and in the darkness bind them").match(/\S+/g);

### 16.“\d”&“\D”(Decimal)
    ("Page 123; published: 1234 id=12#24@112").match(/\d/g);
    ("Page 123; published: 1234 id=12#24@112").match(/\D/g);
    
### 17.“\b”(Boundary)
    ("One ring to bring them all and in the darkness bind them").match(/\b\w/g);
    ("One ring to bring them all and in the darkness bind them").match(/\w\b/g);
    ("One ring to bring them all and in the darkness bind them").match(/\b\w+/g);
    ("cat cats tomcat").match(/\bcat/g);
    ("cat cats tomcat").match(/cat\b/g);

### 18.“\B”(Boundary)
    ("cat cats tomcat").match(/\B./g);
    ("cat cats tomcat").match(/\B.\B./g);


### 20.“(?=<pattern>)”
    ("AAAX---aaax---111").match(/\w+(?=X)/g);
    ("AAAX---aaax---111").match(/\w+(?=\w)/g);

### 21.“(?!<pattern>)”
    ("AAAX---AAA").match(/AAA(?!X)/g);
    ("AAAX---AAA").match(/AAA/g);
    ("AAAX---AAAY---AAA").match(/AAA(?!\w)/g);

### 22.Example
    ("http://www.kbstar.com/abc/ddd/a.jsp").match(/https?:\/\/[\w-]+\.(?:[\w-]+|)(?:(?:\.)[\w-]+(?:\.|)[\w-]+|)/);
    /^([a-z]+):\/\/((?:[a-z\d\-]{2,}\.)+[a-z]{2,})(:\d{1,5})?(\/[^\?]*)?(\?.+)?$/i.exec("https://www.ksnet.co.kr/abc.jsp");

    ("SELECT").match(/^(?:input|select|textarea|button)$/i);
    ("H4").match(/^h\d$/i);
    ("#id").match(/^(?:#([\w-]+)|(\w+)|\.([\w-]+))$/);

    /^(?:\+\d+-|)\d{2,3}-\d{3,4}-\d{4}$/.exec("010-2757-7127");
    /^(?:\+(\d+)-|)(\d{2,3})-(\d{3,4})-(\d{4})$/.exec("+81-010-2757-7127");
