# utl-error-checking-sql-and-exectuting-a-datastep-inside-sql-dosubl
Error checking sql and exectuting a datastep inside sql dosubl
    Error checking sql and exectuting a datastep inside sql dosubl;                                                               
                                                                                                                                  
    github                                                                                                                        
    https://tinyurl.com/yxpgwjub                                                                                                  
    https://github.com/rogerjdeangelis/utl-error-checking-sql-and-executing-a-datastep-inside-sql-dosubl                          
                                                                                                                                  
    SAS Forum                                                                                                                     
    https://tinyurl.com/y33glyyo                                                                                                  
    https://communities.sas.com/t5/SAS-Procedures/How-to-sum-the-specific-values-with-previous-observation-values/m-p/585757      
                                                                                                                                  
    Novinosrin profile                                                                                                            
    https://communities.sas.com/t5/user/viewprofilepage/user-id/138205                                                            
                                                                                                                                  
    *_                   _                                                                                                        
    (_)_ __  _ __  _   _| |_                                                                                                      
    | | '_ \| '_ \| | | | __|                                                                                                     
    | | | | | |_) | |_| | |_                                                                                                      
    |_|_| |_| .__/ \__,_|\__|                                                                                                     
            |_|                                                                                                                   
    ;                                                                                                                             
                                                                                                                                  
    data have;                                                                                                                    
    infile cards truncover;                                                                                                       
    input Date :yymmdd10.      Numbers      ;                                                                                     
    format date yymmdd10.;                                                                                                        
    cards4;                                                                                                                       
    20100101      233      233                                                                                                    
    20100102      271      271                                                                                                    
    20100103      350      350                                                                                                    
    20100104      738      745                                                                                                    
    20100105      2                                                                                                               
    20100106      1                                                                                                               
    20100107      2                                                                                                               
    20100108      1                                                                                                               
    20100109      1                                                                                                               
    20100110      413      413                                                                                                    
    20100111      710      710                                                                                                    
    20100113      575      575                                                                                                    
    20100114      543      545                                                                                                    
    20100115      2                                                                                                               
    20100116      296      296                                                                                                    
    20100117      369      369                                                                                                    
    20100118      735      735                                                                                                    
    20100119      616      616                                                                                                    
    20100120      571      571                                                                                                    
    20100122      458      460                                                                                                    
    20100123      1                                                                                                               
    20100124      1                                                                                                               
    20100125      664      664                                                                                                    
    20100126      575      575                                                                                                    
    20100127      574      574                                                                                                    
    20100129      415      415                                                                                                    
    20100130      269      269                                                                                                    
    20100131      360      362                                                                                                    
    20100201      2                                                                                                               
    ;;;;                                                                                                                          
    run;quit;                                                                                                                     
                                                                                                                                  
    *           _                                                                                                                 
     _ __ _   _| | ___  ___                                                                                                       
    | '__| | | | |/ _ \/ __|                                                                                                      
    | |  | |_| | |  __/\__ \                                                                                                      
    |_|   \__,_|_|\___||___/                                                                                                      
                                                                                                                                  
    ;                                                                                                                             
                                                                                                                                  
    WORK.HAVE total obs=29                                                                                                        
                             | RULES      |               |                                                                       
                             | Step 1     | Step 2        |  NEW_                                                                 
         DATE       NUMBERS  | Groups     |               |NUMBERS                                                                
                             |            |               |                                                                       
      2010-01-01      233    | 1          | 233           |  233                                                                  
      2010-01-02      271    | 2          | 271           |  271                                                                  
      2010-01-03      350    | 3          | 350           |  350                                                                  
                                                                                                                                  
      2010-01-04      738    | 4          | Sum grps      |  745                                                                  
      2010-01-05        2    | 4  <3      | 738+2+1+2+1+1 |    .                                                                  
      2010-01-06        1    | 4  retain  | = 745         |    .                                                                  
      2010-01-07        2    | 4          | .             |    .                                                                  
      2010-01-08        1    | 4          | . set <2 to   |    .                                                                  
      2010-01-09        1    | 4          | . missing     |    .                                                                  
                             |            |               |    .                                                                  
      2010-01-10      413    | 5          |               |  413                                                                  
      2010-01-11      710    | 6          |               |  710                                                                  
                                                                                                                                  
    *            _               _                                                                                                
      ___  _   _| |_ _ __  _   _| |_                                                                                              
     / _ \| | | | __| '_ \| | | | __|                                                                                             
    | (_) | |_| | |_| |_) | |_| | |_                                                                                              
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                             
                    |_|                                                                                                           
    ;                                                                                                                             
                                                                                                                                  
     WANT total obs=29                                                                                                            
                                                                                                                                  
                                 NEW_                                                                                             
         DATE       NUMBERS    NUMBERS                                                                                            
                                                                                                                                  
      2010-01-01      233        233                                                                                              
      2010-01-02      271        271                                                                                              
      2010-01-03      350        350                                                                                              
      2010-01-04      738        745                                                                                              
                                                                                                                                  
      2010-01-05        2          .                                                                                              
      2010-01-06        1          .                                                                                              
      2010-01-07        2          .                                                                                              
      2010-01-08        1          .                                                                                              
      2010-01-09        1          .                                                                                              
      2010-01-10      413        413                                                                                              
      2010-01-11      710        710                                                                                              
      2010-01-13      575        575                                                                                              
      2010-01-14      543        545                                                                                              
      2010-01-15        2          .                                                                                              
      ...                                                                                                                         
                                                                                                                                  
    *                                                                                                                             
     _ __  _ __ ___   ___ ___  ___ ___                                                                                            
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                                           
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                           
    | .__/|_|  \___/ \___\___||___/___/                                                                                           
    |_|                                                                                                                           
    ;                                                                                                                             
                                                                                                                                  
                                                                                                                                  
    proc sql;                                                                                                                     
                                                                                                                                  
       create                                                                                                                     
           table want (drop=grp) as                                                                                               
       select                                                                                                                     
           *                                                                                                                      
           ,ifn(numbers>=3,sum(numbers),.) as new_numbers                                                                         
       from                                                                                                                       
         tmp (where =(0=%sysfunc(dosubl('                                                                                         
            data tmp/view=tmp;                                                                                                    
              set have;                                                                                                           
              if numbers>=3 then grp+1;                                                                                           
            run;quit;                                                                                                             
            '))))                                                                                                                 
        group                                                                                                                     
          by grp                                                                                                                  
        order                                                                                                                     
         by date                                                                                                                  
                                                                                                                                  
    ;quit;                                                                                                                        
                                                                                                                                  
                                                                                                                                  
                                                                                                                                  
