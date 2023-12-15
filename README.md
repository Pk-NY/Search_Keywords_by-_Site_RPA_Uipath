### [RPA 시장조사] ###

3개의 포털 사이트 (구글, 다음, 네이버)에서 RPA관련 키워드(Uipath, 인공지능, Automation Anywhere, RPA, Blue Prism)를 검색하여    

하루치의 뉴스제목과 뉴스URL을 수집하여 엑셀파일로 저장하는 과제


**[사전작업]**

Input 폴더 : Master.xlsx - 검색할 키워드와 사이트가 담긴 파일, VBA 코드 파일, 엑셀템플릿

Config.xlsx : input, output 폴더 경로, 결과파일 이름, 마스터파일 이름, 엑셀양식경로, VBA 코드파일


**[개인작업파일 Business 폴더]**

  FolderPathExits - output폴더확인과 생성
  
  GetMasterFiles - 마스터 파일의 유무를 체크하고 불러와서 DT , array 변수 생성
  
  CopyTempleteFile - 엑셀템플릿파일확인과 복사해서 결과파일로 저장
  

### [작업과정] ###

1. **INITIALIZE PROCESS**
   
    out폴더 체크, 마스터파일의 키워드, 사이트 시트 각각 DT생성, 템플릿파일 복사해서 결과파일 생성
  
2. **GET TRANSACTION DATA**

    Transaction Item : 사이트명,URL 타입은 Datarow

3. **PROCESS TRANSACTION**

    Flowchart에서 작업, 사이트명으로 분기 설정
   
    - 검색일자를 변수에 담기 -> 3개의 사이트 구글, 네이버, 다음 순으로 키워드별 날짜 작용해서 첫페이지의 뉴스만 엑셀에 작성
      
     * 다음은 자동변환 검색이 일어나는 경우가 있어서 원래 키워드 클릭시 날짜 적용을 다시 해줘야 하므로 날짜 적용을 따로 파일로 작성해서 invoke 해줌

4. **END PROCESS**
   
    결과파일에 VBA 적용하여 정리
   
