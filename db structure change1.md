1.ask::what can be the new scoring system ?seeing that level system is to be removed is it that all questions carry equal marks or questions having different marks can appear in any level 2.see::move encrypted solution from ans.php(actually details.php) to database 3.see:api integeration --so this may mean we will have lesser fields in our db e.g. we don't have passwordfa Also used as container tags as in confirn::correct::confirm
--------------------------
## ****Table cm_user Old****##


--------------------------
    Field		data-type			comments

1. userid		int(4)	not-null	user-id used for login using the api
                                    auto-inc PRIMARY-KEY(check availabilty at registration
                                     
   2. username	varchar(50)	.		username 		 UNIQUE
   3. displayname varchar(50)	    the name to be displayed during the competition
                                    UNIQUE
   4. score		int(6)  default0    score awarded so far depending on level of problems solved 
                                    need to solve atleast three problems to move to the 
									next level
   5. level		int(1)  default1    level--increasing marks per question for each level
   
confirm::   6.timeid		varchar(16)         the time when the user last submitted a confirn::correct::correct solution//
   
   Other details:
   no password to be saved in the table as login is done using the api


-------------------------
Fields to be added
7.  attempts		int(3)//total number of problems attempted, same question not counted twice
8.  correct 		int(3)//problems correct, so that percentage correct can be determined
  
  
-----------------------------  
  

  
  

-----------------------------
## Table user_meta_table ##


-----------------------------
   1. id int(11) not-null auto-inc (PRIMARY KEY)   //id of the problem submission
   2. uid int(11) not-null,      //id of the user who submitted this solution
   3. meta varchar(30) not-null  //e.g.'problem' 
   4. value int(3) not-null      // e.g.'1'; value of the problem submitted by the user  as an answere.g. problem no.3 then value=3
   5. timeid timestamp           //timestamp of the time when the solution was submitted 
                                //e.g.'2010-03-10 20:06:55'
------------------------------	
   6. attempt      int(11)       //no of users attempted this question
   7. correct      int(11)     	//no of users who did this question correctly
   8. like 		  int(4)       //no of users who like this question(every user one like at max) 


-------------------------
## Table answers ##


------------------------
1.  prob		int(3)			(PRIMARY-KEY)not-null//problem value e.g. problem no.3
2. answer	varchar(32)     UNIQUE(normally only one answer possible)//sha1(md5(sol)) size  32 to take encryption into account

PRMARY KEY prob corresponds to value in user_meta_table
