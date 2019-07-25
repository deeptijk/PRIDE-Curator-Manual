##### ---------- To get the Number of Submissions/month ----------

    select  to_char(SUBMISSION_DATE, 'YYYY-MM') AS months,count(*) AS NumberOfSubmissions
    from PRIDEARCH.PROJECT
    GROUP BY to_char(SUBMISSION_DATE, 'YYYY-MM')
    ORDER BY 1
   
##### ---------- To get the count of species ----------  

    SELECT cv.ACCESSION, cv.NAME, count(DISTINCT PCV.PROJECT_FK) AS "PROJECT_COUNT"
    FROM PRIDEARCH.CV_PARAM cv 
    JOIN PROJECT_CVPARAM pcv
    ON cv.CV_PARAM_PK = PCV.CV_PARAM_FK
    WHERE cv.CV_LABEL = 'NEWT' 
    GROUP BY cv.ACCESSION, cv.NAME
    ORDER BY cv.NAME
    
##### ---------- To get the total size of the whole dataset ----------

    select  SUM(pf.FILE_SIZE)/(1024*1024*1024*1024)
    from PRIDEARCH.PROJECT_FILES pf

##### ---------- To get the total number of public data ---------- 

    SELECT COUNT(ACCESSION)
    FROM PRIDEARCH.PROJECT 
    WHERE IS_PUBLIC = 1

##### ---------- To get the total number of private data ---------- 

    SELECT COUNT(ACCESSION)
    FROM PRIDEARCH.PROJECT 
    WHERE IS_PUBLIC = 0

##### ---------- To know the datasets from perticular duration ---------- 

    SELECT *
    from PRIDEARCH.PROJECT
    where SUBMISSION_DATE 
    BETWEEN to_date('01-Jan-19','DD-MON-YY') 
    AND to_date('31-May-19','DD-MON-YY'); 

##### ---------- To know the datasets from every month ---------- 

    select  to_char(SUBMISSION_DATE, 'YYYY-MM') AS months,count(*) AS NumberOfSubmissions
    from PRIDEARCH.PROJECT
    where SUBMISSION_DATE 
    BETWEEN to_date('01-OCT-18','DD-MON-YY') 
    AND to_date('25-MAR-19','DD-MON-YY')
    GROUP BY to_char(SUBMISSION_DATE, 'YYYY-MM')
    ORDER BY 1

                                          OR

    select  to_char(SUBMISSION_DATE - 7/24,'IYYY'), to_char(SUBMISSION_DATE - 7/24,'IW'),count(*)
    from PRIDEARCH.PROJECT
    where SUBMISSION_DATE 
    BETWEEN to_date('01-OCT-18','DD-MON-YY') 
    AND to_date('25-MAR-19','DD-MON-YY')
    GROUP BY to_char(SUBMISSION_DATE - 7/24,'IYYY'), to_char(SUBMISSION_DATE - 7/24,'IW')
    ORDER BY 1


##### ---------- To get the number of distinct user emails representing the individual submitters ---------- 

    SELECT count(distinct(u.email)) from PRIDE_USERS u
    join project p on (u.USER_PK = p.SUBMITTER_FK)

##### ---------- To get the number of distinct user emails representing the individual lab head ---------- 

    select count(distinct(lh.email)) from project p 
    join lab_head lh on (p.PROJECT_PK = lh.PROJECT_FK) 

