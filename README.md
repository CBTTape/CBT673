# CBT673
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 673 is from Tom Sipusic and contains a program called     *   FILE 673
//*           CCFDELET which will delete datasets using JCL.  In    *   FILE 673
//*           addition, CCFDELET will delete HSM archived datasets  *   FILE 673
//*           without having to recall them.  Detailed description  *   FILE 673
//*           follows below.                                        *   FILE 673
//*                                                                 *   FILE 673
//*           email: sipusic@georgetown.edu                         *   FILE 673
//*           phone: 202-687-3934                                   *   FILE 673
//*           address: Thomas Sipusic                               *   FILE 673
//*                    Georgetown University Information Services   *   FILE 673
//*                    Box 571138                                   *   FILE 673
//*                    St. Mary's Hall 304D                         *   FILE 673
//*                    Washingtion, DC 20057                        *   FILE 673
//*                                                                 *   FILE 673
//*                    Notes and Commentary                         *   FILE 673
//*                                                                 *   FILE 673
//*     Georgetown University uses the homegrown utility            *   FILE 673
//*     CCFDELET for ensuring that a data set is deleted prior      *   FILE 673
//*     to running a step that will reallocate it. It has some      *   FILE 673
//*     advantages over the following alternatives:                 *   FILE 673
//*                                                                 *   FILE 673
//*     1) IEFBR14 with a "MOD,DELETE" DD card. Unfortunately,      *   FILE 673
//*        if the data set is in migrated status, DFHSM will        *   FILE 673
//*        first restore it before deleting it. There is no         *   FILE 673
//*        restore with CCFDELET.                                   *   FILE 673
//*                                                                 *   FILE 673
//*     2) IDCAMS. The need to use control cards is the             *   FILE 673
//*        disadvantage here. With CCFDELET, you (can) specify      *   FILE 673
//*        the data set to delete in the PARM field of the EXEC     *   FILE 673
//*        card.                                                    *   FILE 673
//*                                                                 *   FILE 673
//*     CCFDELET has the good points of IEFBR14 without the         *   FILE 673
//*     disadvantage of recalling migrated data sets. The data      *   FILE 673
//*     set to delete is visible in the JCL. It works with JCL      *   FILE 673
//*     procedures and JCL symbols.                                 *   FILE 673
//*                                                                 *   FILE 673
//*     CCFDELET deletes data sets by invoking IDCAMS and           *   FILE 673
//*     supplying control cards to it. The appendix "Invoking       *   FILE 673
//*     Access Method Services from Your Program" in the Access     *   FILE 673
//*     Method Services manual taught me how to do this.  The       *   FILE 673
//*     program has not changed since 1994. What was assembled      *   FILE 673
//*     and linked then has continued to work up through OS/390     *   FILE 673
//*     2.10, which is the release that Georgetown currently        *   FILE 673
//*     runs.                                                       *   FILE 673
//*                                                                 *   FILE 673
//*     You are getting the source Georgetown uses with one         *   FILE 673
//*     exception noted below.  You should probably review it       *   FILE 673
//*     before you put it into production.  It works at             *   FILE 673
//*     Georgetown but no guarantee is made that it will work       *   FILE 673
//*     anywhere else. Use it at your own risk.  The one change     *   FILE 673
//*     to the source is a commented out entry of the text unit     *   FILE 673
//*     pointer list that starts at the label TUPTRLST.             *   FILE 673
//*     Comments there indicate why.                                *   FILE 673
//*                                                                 *   FILE 673
//*     JOBSTREAM Example:                                          *   FILE 673
//*                                                                 *   FILE 673
//*     //STEP1 EXEC PGM=CCFDELET                                   *   FILE 673
//*     //SYSPRINT DD SYSOUT=*                                      *   FILE 673
//*     //SYSIN DD *                                                *   FILE 673
//*     CCF.DELETE.DSN1                                             *   FILE 673
//*     CCF.DELETE.DSN2                                             *   FILE 673
//*     CCF.DELETE.DSN3                                             *   FILE 673
//*     /*                                                          *   FILE 673
//*                                                                 *   FILE 673
//*     PROC Example:                                               *   FILE 673
//*                                                                 *   FILE 673
//*     //STEP1 EXEC PGM=CCFDELET,PARM='CCF.DELETE.DSN1'            *   FILE 673
//*     //STEP2 EXEC PGM=CCFDELET,PARM='CCF.DELETE.DSN2'            *   FILE 673
//*     //STEP3 EXEC PGM=CCFDELET,PARM='CCF.DELETE.DSN3'            *   FILE 673
//*                                                                 *   FILE 673
```
