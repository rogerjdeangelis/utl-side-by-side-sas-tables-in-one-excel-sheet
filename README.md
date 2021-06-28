# utl-side-by-side-sas-tables-in-one-excel-sheet
Side by side sas tables in one excel sheet 
    Side by side sas tables in one excel sheet

    This repo provides to to horizontally load multiple tables into an single excel sheet.

    You can also do this with R and Python, see related repos below.

    SAS Forum
    https://tinyurl.com/mrvssu52
    https://communities.sas.com/t5/SAS-Programming/SAS-Export-more-dataset-in-one-excel-sheet-with-two-columns/m-p/750108


    ChrisNZ
    https://communities.sas.com/t5/user/viewprofilepage/user-id/16961

    Related Repos
    https://tinyurl.com/4n47ksys
    https://github.com/rogerjdeangelis?tab=repositories&q=side+by+side&type=&language=&sort=

    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    * create space dataset;
    data space;

      label
        sp1=""
        sp2="";

        sp1="";
        sp2="";

    run;quit;

    data have;          /* spacer */
      merge sashelp.class space sashelp.cntainer;
    run;quit;

    /*
    Up to 40 obs WORK.HAVE total obs=19

    Obs    NAME       SEX    AGE    HEIGHT    WEIGHT    SP1    SP2    CRMETHOD    CONTNAME    MIRRNAME    SECURE

      1    Alfred      M      14     69.0      112.5                  DIRECT      MRRGSTRY                   0
      2    Alice       F      13     56.5       84.0                  DIRECT      CNTAINER                   0
      3    Barbara     F      13     65.3       98.0                  PERSIST     LIBRARY                    0
      4    Carol       F      14     62.8      102.5                  PERSIST     TABLE                      0
      5    Henry       M      14     63.5      102.5                  PERSIST     DYNATTR                    0
      6    James       M      12     57.3       83.0                  PERSIST     MDASSOC                    0
      7    Jane        F      12     59.8       84.5                  PERSIST     COLUMN                     0
      8    Janet       F      15     62.5      112.5                                                         .
      9    Jeffrey     M      13     62.5       84.0                                                         .
     10    John        M      12     59.0       99.5                                                         .
     11    Joyce       F      11     51.3       50.5                                                         .
     12    Judy        F      14     64.3       90.0                                                         .
     13    Louise      F      12     56.3       77.0                                                         .
     14    Mary        F      15     66.5      112.0                                                         .
     15    Philip      M      16     72.0      150.0                                                         .
     16    Robert      M      12     64.8      128.0                                                         .
     17    Ronald      M      15     67.0      133.0                                                         .
     18    Thomas      M      11     57.5       85.0                                                         .
     19    William     M      15     66.5      112.0                                                         .
    */

    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */


    %utlfkil(d:/xls/sideBySide.xlsx);

    ods listing;
    ods excel
         file='d:/xls/sideBySide.xlsx'
         style=minimal
         options(sheet_name="side2side");

    proc report data=have;
        label sp1='00'x sp2='00'x;
    run;quit;
    ods excel close;

    /*           _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| `_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    */

    d:/xls/sideBySide.xls

    +-------------------------------------------------------------------------------------------------+
    |  |   A     | B  |    C     |      D   |      E   |F | G|   H     |     I   |    J    |      K   |
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    |  | NAME    |SEX |       AGE|    HEIGHT|    WEIGHT|  |  | CRMETHOD| CONTNAME| MIRRNAME|    SECURE|
    |-------------------------------------------------------------------------------------------------|
    | 1| Alfred  | M  |        14|        69|     112.5|  |  | DIRECT  | MRRGSTRY|         |         0|
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    | 2| Alice   | F  |        13|      56.5|        84|  |  | DIRECT  | CNTAINER|         |         0|
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    | 3| Barbara | F  |        13|      65.3|        98|  |  | PERSIST | LIBRARY |         |         0|
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    | 4| Carol   | F  |        14|      62.8|     102.5|  |  | PERSIST | TABLE   |         |         0|
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    | 5| Henry   | M  |        14|      63.5|     102.5|  |  | PERSIST | DYNATTR |         |         0|
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    | 6| James   | M  |        12|      57.3|        83|  |  | PERSIST | MDASSOC |         |         0|
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    | 7| Jane    | F  |        12|      59.8|      84.5|  |  | PERSIST | COLUMN  |         |         0|
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    | 8| Janet   | F  |        15|      62.5|     112.5|  |  |         |         |         |         .|
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    | 9| Jeffrey | M  |        13|      62.5|        84|  |  |         |         |         |         .|
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    |10| John    | M  |        12|        59|      99.5|  |  |         |         |         |         .|
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    |11| Joyce   | F  |        11|      51.3|      50.5|  |  |         |         |         |         .|
    |--+---------+----+----------+----------+----------+--+--+---------+---------+---------+----------|
    |12| Judy    | F  |        14|      64.3|        90|  |  |         |         |         |         .|
    +-------------------------------------------------------------------------------------------------+

    [sideBySide]








