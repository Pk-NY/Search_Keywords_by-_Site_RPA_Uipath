### [RPA 시장조사] ###

3개의 포털 사이트 (구글, 다음, 네이버)에서 RPA관련 키워드(Uipath, 인공지능, Automation Anywhere, RPA, Blue Prism)를 검색하여    

하루치의 뉴스제목과 뉴스URL을 수집하여 엑셀파일로 저장하는 과제


**[사전작업]**

Input 폴더 : Master.xlsx - 검색할 키워드와 사이트가 담긴 파일, VBA 코드 파일, 엑셀템플릿

Config.xlsx : input, output 폴더 경로, 결과파일 이름, 마스터파일 이름, 엑셀양식경로, VBA 코드파일


**[개인작업파일]**

  FolderPathExits - output폴더확인과 생성
  
  GetMasterFiles - 마스터 파일의 유무를 체크하고 불러와서 DT , array 변수 생성
  
  CopyTempleteFile - 엑셀템플릿파일확인과 복사해서 결과파일로 저장
  

### [작업과정] ###

1. **INITIALIZE PROCESS**
 + ./Framework/*InitiAllSettings* - Load configuration data from Config.xlsx file and from assets
 + ./Framework/*GetAppCredential* - Retrieve credentials from Orchestrator assets or local Windows Credential Manager
 + ./Framework/*InitiAllApplications* - Open and login to applications used throughout the process

2. **GET TRANSACTION DATA**
 + ./Framework/*GetTransactionData* - Fetches transactions from an Orchestrator queue defined by Config("OrchestratorQueueName") or any other configured data source

3. **PROCESS TRANSACTION**
 + *Process* - Process trasaction and invoke other workflows related to the process being automated 
 + ./Framework/*SetTransactionStatus* - Updates the status of the processed transaction (Orchestrator transactions by default): Success, Business Rule Exception or System Exception

4. **END PROCESS**
 + ./Framework/*CloseAllApplications* - Logs out and closes applications used throughout the process


### For New Project ###

1. Check the Config.xlsx file and add/customize any required fields and values
2. Implement InitiAllApplications.xaml and CloseAllApplicatoins.xaml workflows, linking them in the Config.xlsx fields
3. Implement GetTransactionData.xaml and SetTransactionStatus.xaml according to the transaction type being used (Orchestrator queues by default)
4. Implement Process.xaml workflow and invoke other workflows related to the process being automated
