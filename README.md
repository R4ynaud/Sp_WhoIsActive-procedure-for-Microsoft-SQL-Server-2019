# sp_WhoIsActive Procedure For Microsoft SQL Server 2019.


Guide to Creating the sp_WhoIsActive Procedure in Microsoft SQL Server 2019.


![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/8cc3b2d6-88bc-4794-8045-26b2a0519040)


## What Is an sp_WhoIsActive ?  


• sp_WhoIsActive is a procedure used in SQL Server to effectively monitor active queries and processes. By utilizing information obtained from dynamic management views (DMVs) such as sys.dm_exec_requests and other relevant DMVs, sp_WhoIsActive allows you to track ongoing processes on the server in real-time.


The sp_WhoIsActive procedure provides the following information:


1-) List of running queries: It lists the queries currently executing on the server, along with detailed information such as process ID, query text, execution duration, waiting processes, and query plan.


2-) Process information: It lists the active processes on the server, including process ID, start time, end time, query plan, and session information.


3-) Blocking information: It indicates if the process is causing any blocks with other processes.


4-) Waiting processes: It shows what the queries are waiting for (e.g., locks, resources, network traffic, etc.).


5-) sp_WhoIsActive is a useful tool for diagnosing performance issues, optimizing queries, and monitoring server resource usage. It can also be used to monitor query performance in real-time in live environments. This procedure can be executed using SQL Server Management Studio or through a SQL query.


## sp_WhoIsActive Nedir ? Ne İşe Yarar ?   


• sp_WhoIsActive, SQL Server'da kullanılan bir prosedürdür. Bu prosedür, etkin bir şekilde çalışan sorguları ve işlemleri izlemek için kullanılır. sp_WhoIsActive, SQL Server'ın dinamik yönetim görünümü (DMV) olan sys.dm_exec_requests ve diğer DMV'lerden elde edilen bilgileri kullanarak, sunucuda gerçekleşen işlemleri anlık olarak takip etmenizi sağlar.


sp_WhoIsActive prosedürü, aşağıdaki bilgileri sağlar:


1-) Çalışan sorguların listesi: Proses kimliği, sorgu metni, çalışma süresi, bekleyen işlemler, sorgu planı gibi detaylı bilgilerle birlikte sunucuda çalışan sorguları listeler.


2-) İşlem bilgileri: İşlem kimliği, başlatma zamanı, bitiş zamanı, sorgu planı, oturum bilgileri gibi bilgilerle birlikte sunucuda çalışan işlemleri listeler.


3-) Blokaj bilgileri: Prosesin diğer işlemlerle olan blokaj durumunu gösterir.


4-) Bekleyen işlemler: Sorguların neyin beklenildiğini (örneğin, kilit, kaynak, ağ trafiği vb.) gösterir.


5-) sp_WhoIsActive, performans sorunlarını teşhis etmek, sorgu optimizasyonunu yapmak ve sunucu kaynaklarının kullanımını izlemek için oldukça yararlı bir araçtır. Ayrıca, canlı ortamlarda gerçek zamanlı olarak sorgu performansını izlemek için de kullanılabilir. Bu prosedür, SQL Server Management Studio veya SQL sorgusu aracılığıyla çalıştırılabilir. 


## Let's start creating the sp_WhoIsActive procedure in our database.


## Veritabanımızda sp_WhoIsActive prosedürünü oluşturmaya başlayalım. 


## 1-) Let's go to Adam Machanic's website (http://whoisactive.com) and download the latest version. 


## 1-) Adam Machanic'in web sitesine (http://whoisactive.com) giderek en son sürümü indiriyoruz.


#### 1 - 1
![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/0f4be187-b69c-4315-97fd-5dde4bcfa03b)


#### 1 - 2
![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/589f9f08-eb8a-46da-bf95-b84220387d5e)


#### 1 - 3
![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/4b8e9603-4a30-4112-8916-2f99ac69f2c8)


#### 1 - 4
![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/89a66676-6696-4f7b-9a4b-604ce657769b)


#### 1 - 5
![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/b7a8f255-ecfc-4690-9247-22bf9bd3d99b)


## 2-) After downloading the file, we open the " sp_WhoIsActive.sql " file located inside the folder in SQL Server Management Studio. 


## 2-) Dosyayı indirdikten sonra SQL Server Management Studio'da klasör içerisinde yer alan " sp_WhoIsActive.sql " dosyasını açıyoruz.


![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/29e2b9b0-29a0-476c-ac3d-11b3bddfe631)


## 3-) In SQL Server Management Studio, we execute the "sp_WhoIsActive.sql" file that we opened by selecting the schema in which we want to run it (Execute or F5).


## 3-) SQL Server Management Studio'da açtığımız 'sp_WhoIsActive.sql' dosyasını çalıştırmak istediğimiz şemayı seçerek çalıştırıyoruz (Execute veya F5).


![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/fe55ec87-6920-4e88-9cd6-2754ad249307)


![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/d6cbd111-39c0-4494-aae7-0a93b4ce1213)


## 4-) After successfully creating our procedure, we run the "EXEC sp_whoisactive" command to check it.


## 4-) Prosedürümüzü başarıyla oluşturduktan sonra kontrol etmek için "EXEC sp_whoisactive" komutunu çalıştırıyoruz.


> EXEC sp_whoisactive 


![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/7ac75d60-de0c-449a-814e-88823fdd6048)


![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/3fe546f4-ede7-4209-8199-e0f2c2c41262)


## We need to schedule our "sp_WhoIsActive" procedure with the "SQL Server Agent" to run every 59 seconds. This process will allow us to gather information about the SQL queries executed on the database and provide us with the ability to monitor and review these queries.


## Oluşturduğumuz "sp_WhoIsActive" prosedürümüzü "SQL Server Agent" ile 59 saniyede bir çalışacak şekilde schedule etmemiz gerekiyor, bu işlem veritabanında çalıştırılan SQL sorguları hakkında bilgi toplamamızı ve bu sorguları izleme ve inceleme olanağı sağlayacaktır bize.


## 1-) Let's navigate to SQL Server Agent and click on the "New" -> "Job" tab.


## 1-) SQL Server Agent'a gelin ve "New" -> "Job" sekmesine tıklayalım.


![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/a6fac921-e872-454e-b390-741c6aca2cf4)


![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/dd1456f7-b447-4391-803f-cce68571dd35)


## 2-) In the opened tab, enter the name of the job you are creating in the "Name" field.


## 2-) Açılan sekmede "Name" alanına oluşturacağımız job'ın adını giriyoruz.


![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/326ec78d-1157-4071-b66d-4fe33dda9b65)


## 3-) Click on the "New" button in the "Steps" tab to define the "EXEC sp_whoisactive" command that will be executed by the job.


## 3-) "Steps" sekmesinden "New" butonuna tıklayarak "EXEC sp_whoisactive" komutunu çalıştıracağımız job'a tanımlıyoruz.


![image](https://github.com/R4ynaud/Sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019-TEST/assets/93924485/339faaf8-12a4-421a-9870-55f91bff91e5)


## 4-) Click on the "New" button in the "Schedules" tab to configure the job to trigger automatically, running every 59 seconds.


## 4-) "Schedules" sekmesinden "New" butonuna tıklayarak job'ı her 59 saniyede otomatik olarak çalışması tektikleyecek şekilde ayarlıyoruz.


![image](https://github.com/R4ynaud/sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019/assets/93924485/022b6523-be16-4e8e-b93a-2d80e0b83086)


![image](https://github.com/R4ynaud/sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019/assets/93924485/7a48b809-142f-4311-839e-5f2fb46ce448)


## 5-) Finally, click on the "View History" tab to review the logs and verify that the job we created is running successfully.


## 5-) Son olarak "View History" sekmesine tıklayıp logları incelediğimiz oluşturduğumuz job'ın sorunsuz çalıştığını görebiliyoruz.


![image](https://github.com/R4ynaud/sp_WhoIsActive-procedure-for-Microsoft-SQL-Server-2019/assets/93924485/d1d22369-2348-458b-9f3a-dc80c122c465)



























