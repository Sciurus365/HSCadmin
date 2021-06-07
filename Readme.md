Readme
================

在北大未名BBS (<https://bbs.pku.edu.cn/>) HSC
（医学部）版近期进行的三次版务申请投票中，三位不同背景的申请者因不同的原因被投票否决。
其中，第一名申请者ducker是19级医学部在读本科生，主要反对理由为该同学较为年轻，不能胜任。
第二名申请者ccmesongshu是校本部19届毕业生，有一定的版务管理经验，主要反对理由为该同学为非医学部且为毕业生，不能胜任。
第三名申请者accept是医学部16级在读长学制临床研究生，主要反对理由为该同学临床事务繁忙，不能胜任。

根据未名BBS规定，版务投票为记名投票，结果公开。根据此公开数据做如下整理：

``` r
library(tidyverse)
```

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.3     v purrr   0.3.4
    ## v tibble  3.1.1     v dplyr   1.0.6
    ## v tidyr   1.1.3     v stringr 1.4.0
    ## v readr   1.4.0     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
accept_result <- read_csv("accept.csv")
```

    ## 
    ## -- Column specification --------------------------------------------------------
    ## cols(
    ##   ID = col_character(),
    ##   IP = col_character(),
    ##   time = col_character(),
    ##   day = col_character(),
    ##   choice = col_character()
    ## )

``` r
ccmesongshu_result <- read_csv("ccmesongshu.csv")
```

    ## 
    ## -- Column specification --------------------------------------------------------
    ## cols(
    ##   ID = col_character(),
    ##   IP = col_character(),
    ##   time = col_character(),
    ##   day = col_character(),
    ##   choice = col_character()
    ## )

``` r
ducker_result <- read_csv("ducker.csv")
```

    ## 
    ## -- Column specification --------------------------------------------------------
    ## cols(
    ##   ID = col_character(),
    ##   IP = col_character(),
    ##   time = col_character(),
    ##   day = col_character(),
    ##   choice = col_character()
    ## )

``` r
all_result <- full_join(accept_result, ccmesongshu_result, by = "ID", suffix = c(".accept", ".ccmesongshu")) %>%
    full_join(ducker_result, by = "ID") %>%
    mutate(choice.ducker = choice) %>%
    select(ID, choice.accept, choice.ccmesongshu, choice.ducker)

knitr::kable(all_result)
```

| ID           | choice.accept | choice.ccmesongshu | choice.ducker |
|:-------------|:--------------|:-------------------|:--------------|
| accept       | A             | A                  | NA            |
| Admi         | A             | A                  | NA            |
| afurol       | A             | NA                 | NA            |
| amoykang     | A             | A                  | NA            |
| arzthxy      | B             | B                  | NA            |
| augatuniv    | A             | B                  | NA            |
| axtoxic      | A             | NA                 | A             |
| bailangdx    | A             | B                  | NA            |
| bananaskin   | A             | A                  | NA            |
| bias         | B             | B                  | NA            |
| bigdouble    | B             | B                  | NA            |
| biuJON       | A             | A                  | NA            |
| bjdoufei     | B             | B                  | NA            |
| blueflash    | A             | NA                 | NA            |
| bonfire      | B             | B                  | NA            |
| bradtido     | A             | A                  | NA            |
| bridgefly    | A             | A                  | NA            |
| Brielle      | B             | B                  | NA            |
| Briseis      | B             | B                  | NA            |
| bwcx         | B             | B                  | NA            |
| catalyze     | A             | A                  | NA            |
| ccmesongshu  | A             | NA                 | NA            |
| cgbdycz      | B             | B                  | NA            |
| cxaicx       | B             | B                  | NA            |
| Delusional   | A             | A                  | NA            |
| derive       | B             | B                  | NA            |
| desmondliang | A             | A                  | NA            |
| Destinii     | B             | B                  | NA            |
| docidaci     | B             | B                  | NA            |
| doctorfree   | A             | A                  | NA            |
| ducker       | A             | A                  | NA            |
| dvoraz       | A             | A                  | NA            |
| Eden         | B             | B                  | NA            |
| edenhazard   | A             | A                  | NA            |
| eeeKd        | B             | B                  | NA            |
| Einsieben    | A             | NA                 | A             |
| euio         | A             | A                  | NA            |
| EulerHuaji   | A             | A                  | NA            |
| EzawaTamiko  | A             | A                  | NA            |
| faruxue      | B             | B                  | NA            |
| Fireworks    | A             | A                  | NA            |
| fundamental  | A             | A                  | NA            |
| gaodi        | B             | B                  | NA            |
| gol          | A             | A                  | B             |
| Hangovers    | B             | B                  | NA            |
| hanhanmei    | B             | B                  | NA            |
| HANZPAN      | A             | A                  | A             |
| HelloOTS     | A             | NA                 | A             |
| hhhhhhhhhhh  | B             | B                  | NA            |
| himitsu      | A             | A                  | NA            |
| houbuhoua    | A             | A                  | NA            |
| hrcegg       | A             | A                  | NA            |
| hscxcb       | A             | A                  | NA            |
| idiocratic   | A             | A                  | NA            |
| Iowa         | A             | A                  | NA            |
| Iridaze      | A             | A                  | NA            |
| jennyG       | A             | NA                 | NA            |
| kanez        | A             | A                  | NA            |
| KennethPKU   | A             | A                  | NA            |
| kitdzlove    | B             | B                  | NA            |
| lemonlemon   | B             | B                  | NA            |
| leppapebc    | A             | A                  | NA            |
| LH           | A             | A                  | NA            |
| Lithium      | A             | A                  | NA            |
| lizx         | A             | A                  | NA            |
| lnpku        | A             | A                  | NA            |
| lohas        | B             | B                  | NA            |
| lxy          | A             | A                  | NA            |
| lyhsunny     | B             | B                  | NA            |
| maonster     | A             | A                  | NA            |
| mojave       | A             | A                  | NA            |
| Moony        | A             | A                  | NA            |
| motaguoke    | A             | A                  | NA            |
| MrWolffy     | A             | A                  | NA            |
| muktub       | B             | B                  | NA            |
| Nachtmusik   | A             | A                  | A             |
| nancycat     | B             | B                  | NA            |
| Noah         | B             | B                  | NA            |
| pangshuaige  | A             | A                  | NA            |
| pinellia     | B             | B                  | NA            |
| pkuerljh     | A             | A                  | NA            |
| Purpose      | A             | NA                 | NA            |
| puzhe        | A             | A                  | NA            |
| Qiiiiii      | A             | A                  | NA            |
| ququlongsha  | A             | A                  | NA            |
| RayPrime     | A             | A                  | NA            |
| Reines       | A             | A                  | NA            |
| RichardGreen | A             | A                  | NA            |
| rlcheng      | A             | A                  | NA            |
| Rorschach    | B             | B                  | NA            |
| ryanli       | A             | A                  | NA            |
| sanshan      | A             | A                  | NA            |
| shuchong     | A             | NA                 | NA            |
| sjwclwnayz   | A             | A                  | NA            |
| skygs        | B             | B                  | B             |
| soniaw       | B             | B                  | NA            |
| spiridempt   | A             | A                  | NA            |
| SQ           | A             | A                  | NA            |
| SrinceW      | A             | A                  | A             |
| ssssuuuu     | B             | B                  | NA            |
| stonez       | A             | A                  | NA            |
| survivor     | A             | A                  | NA            |
| sweetmonkey  | B             | B                  | NA            |
| Talutsai     | A             | A                  | A             |
| tangmo       | A             | A                  | A             |
| Tavstar      | A             | A                  | A             |
| Tool         | B             | B                  | NA            |
| Tranquilsun  | A             | A                  | NA            |
| tsiau        | A             | A                  | A             |
| Velpro       | B             | B                  | NA            |
| vitiger      | A             | A                  | NA            |
| viviss       | B             | B                  | NA            |
| vvvvic       | B             | B                  | NA            |
| watem        | A             | A                  | NA            |
| webberjian   | B             | B                  | NA            |
| wenxijc      | A             | NA                 | NA            |
| wky          | A             | A                  | NA            |
| woctordho    | A             | A                  | NA            |
| wuyuchuan    | A             | A                  | NA            |
| xiaohehe     | A             | A                  | NA            |
| XuLanTu      | A             | A                  | NA            |
| xuziling     | B             | B                  | NA            |
| yuanhuang    | A             | A                  | NA            |
| YvonneLLL    | A             | A                  | NA            |
| yydcj        | A             | A                  | NA            |
| zaiqiang     | A             | A                  | NA            |
| zaza         | A             | A                  | A             |
| ZBFSZX       | B             | A                  | B             |
| ZelmaYoung   | B             | B                  | B             |
| zinccat      | A             | A                  | NA            |
| ZQM          | A             | A                  | B             |
| moonl        | NA            | A                  | NA            |
| ARABBIT      | NA            | A                  | NA            |
| starlight    | NA            | A                  | NA            |
| docu         | NA            | A                  | NA            |
| dengrun      | NA            | A                  | NA            |
| thedoor      | NA            | B                  | NA            |
| enozi        | NA            | B                  | NA            |
| Pip          | NA            | B                  | NA            |
| lululux      | NA            | B                  | NA            |
| ckrenren     | NA            | A                  | NA            |
| monicany     | NA            | B                  | NA            |
| zhanyihe     | NA            | A                  | NA            |
| psychosocial | NA            | B                  | NA            |
| anotso       | NA            | NA                 | A             |
| astrolabe    | NA            | NA                 | B             |
| Chiilin      | NA            | NA                 | B             |
| conezy       | NA            | NA                 | A             |
| craneth      | NA            | NA                 | B             |
| dodobus      | NA            | NA                 | A             |
| echoes       | NA            | NA                 | B             |
| GuNai        | NA            | NA                 | B             |
| hnll         | NA            | NA                 | A             |
| HuayuSi      | NA            | NA                 | B             |
| idudu        | NA            | NA                 | A             |
| Keib         | NA            | NA                 | A             |
| kzhengPKU    | NA            | NA                 | A             |
| momohong     | NA            | NA                 | B             |
| nashishenme  | NA            | NA                 | B             |
| parsio       | NA            | NA                 | B             |
| pencilpop    | NA            | NA                 | B             |
| pkuhb        | NA            | NA                 | A             |
| qinwei       | NA            | NA                 | A             |
| qui          | NA            | NA                 | B             |
| Shadow       | NA            | NA                 | B             |
| SheeranYoung | NA            | NA                 | B             |
| Shirleen     | NA            | NA                 | B             |
| steveblade   | NA            | NA                 | A             |
| wenjiajia    | NA            | NA                 | A             |
| wuxian       | NA            | NA                 | A             |
| WZzzxxx      | NA            | NA                 | B             |
| xinglian     | NA            | NA                 | A             |
| yuewuzhen    | NA            | NA                 | B             |
| yxlixiang    | NA            | NA                 | A             |
| zhangercheng | NA            | NA                 | B             |
| zznizhidao   | NA            | NA                 | B             |

其中，各ID投下反对票的次数统计如下：

``` r
B_result <- all_result %>%
    rowwise() %>%
    mutate(B_num = sum(c(choice.accept, choice.ccmesongshu, choice.ducker) == "B", na.rm = T)) %>%
    ungroup() %>%
    arrange(-B_num)

knitr::kable(B_result)
```

| ID           | choice.accept | choice.ccmesongshu | choice.ducker | B\_num |
|:-------------|:--------------|:-------------------|:--------------|-------:|
| skygs        | B             | B                  | B             |      3 |
| ZelmaYoung   | B             | B                  | B             |      3 |
| arzthxy      | B             | B                  | NA            |      2 |
| bias         | B             | B                  | NA            |      2 |
| bigdouble    | B             | B                  | NA            |      2 |
| bjdoufei     | B             | B                  | NA            |      2 |
| bonfire      | B             | B                  | NA            |      2 |
| Brielle      | B             | B                  | NA            |      2 |
| Briseis      | B             | B                  | NA            |      2 |
| bwcx         | B             | B                  | NA            |      2 |
| cgbdycz      | B             | B                  | NA            |      2 |
| cxaicx       | B             | B                  | NA            |      2 |
| derive       | B             | B                  | NA            |      2 |
| Destinii     | B             | B                  | NA            |      2 |
| docidaci     | B             | B                  | NA            |      2 |
| Eden         | B             | B                  | NA            |      2 |
| eeeKd        | B             | B                  | NA            |      2 |
| faruxue      | B             | B                  | NA            |      2 |
| gaodi        | B             | B                  | NA            |      2 |
| Hangovers    | B             | B                  | NA            |      2 |
| hanhanmei    | B             | B                  | NA            |      2 |
| hhhhhhhhhhh  | B             | B                  | NA            |      2 |
| kitdzlove    | B             | B                  | NA            |      2 |
| lemonlemon   | B             | B                  | NA            |      2 |
| lohas        | B             | B                  | NA            |      2 |
| lyhsunny     | B             | B                  | NA            |      2 |
| muktub       | B             | B                  | NA            |      2 |
| nancycat     | B             | B                  | NA            |      2 |
| Noah         | B             | B                  | NA            |      2 |
| pinellia     | B             | B                  | NA            |      2 |
| Rorschach    | B             | B                  | NA            |      2 |
| soniaw       | B             | B                  | NA            |      2 |
| ssssuuuu     | B             | B                  | NA            |      2 |
| sweetmonkey  | B             | B                  | NA            |      2 |
| Tool         | B             | B                  | NA            |      2 |
| Velpro       | B             | B                  | NA            |      2 |
| viviss       | B             | B                  | NA            |      2 |
| vvvvic       | B             | B                  | NA            |      2 |
| webberjian   | B             | B                  | NA            |      2 |
| xuziling     | B             | B                  | NA            |      2 |
| ZBFSZX       | B             | A                  | B             |      2 |
| augatuniv    | A             | B                  | NA            |      1 |
| bailangdx    | A             | B                  | NA            |      1 |
| gol          | A             | A                  | B             |      1 |
| ZQM          | A             | A                  | B             |      1 |
| thedoor      | NA            | B                  | NA            |      1 |
| enozi        | NA            | B                  | NA            |      1 |
| Pip          | NA            | B                  | NA            |      1 |
| lululux      | NA            | B                  | NA            |      1 |
| monicany     | NA            | B                  | NA            |      1 |
| psychosocial | NA            | B                  | NA            |      1 |
| astrolabe    | NA            | NA                 | B             |      1 |
| Chiilin      | NA            | NA                 | B             |      1 |
| craneth      | NA            | NA                 | B             |      1 |
| echoes       | NA            | NA                 | B             |      1 |
| GuNai        | NA            | NA                 | B             |      1 |
| HuayuSi      | NA            | NA                 | B             |      1 |
| momohong     | NA            | NA                 | B             |      1 |
| nashishenme  | NA            | NA                 | B             |      1 |
| parsio       | NA            | NA                 | B             |      1 |
| pencilpop    | NA            | NA                 | B             |      1 |
| qui          | NA            | NA                 | B             |      1 |
| Shadow       | NA            | NA                 | B             |      1 |
| SheeranYoung | NA            | NA                 | B             |      1 |
| Shirleen     | NA            | NA                 | B             |      1 |
| WZzzxxx      | NA            | NA                 | B             |      1 |
| yuewuzhen    | NA            | NA                 | B             |      1 |
| zhangercheng | NA            | NA                 | B             |      1 |
| zznizhidao   | NA            | NA                 | B             |      1 |
| accept       | A             | A                  | NA            |      0 |
| Admi         | A             | A                  | NA            |      0 |
| afurol       | A             | NA                 | NA            |      0 |
| amoykang     | A             | A                  | NA            |      0 |
| axtoxic      | A             | NA                 | A             |      0 |
| bananaskin   | A             | A                  | NA            |      0 |
| biuJON       | A             | A                  | NA            |      0 |
| blueflash    | A             | NA                 | NA            |      0 |
| bradtido     | A             | A                  | NA            |      0 |
| bridgefly    | A             | A                  | NA            |      0 |
| catalyze     | A             | A                  | NA            |      0 |
| ccmesongshu  | A             | NA                 | NA            |      0 |
| Delusional   | A             | A                  | NA            |      0 |
| desmondliang | A             | A                  | NA            |      0 |
| doctorfree   | A             | A                  | NA            |      0 |
| ducker       | A             | A                  | NA            |      0 |
| dvoraz       | A             | A                  | NA            |      0 |
| edenhazard   | A             | A                  | NA            |      0 |
| Einsieben    | A             | NA                 | A             |      0 |
| euio         | A             | A                  | NA            |      0 |
| EulerHuaji   | A             | A                  | NA            |      0 |
| EzawaTamiko  | A             | A                  | NA            |      0 |
| Fireworks    | A             | A                  | NA            |      0 |
| fundamental  | A             | A                  | NA            |      0 |
| HANZPAN      | A             | A                  | A             |      0 |
| HelloOTS     | A             | NA                 | A             |      0 |
| himitsu      | A             | A                  | NA            |      0 |
| houbuhoua    | A             | A                  | NA            |      0 |
| hrcegg       | A             | A                  | NA            |      0 |
| hscxcb       | A             | A                  | NA            |      0 |
| idiocratic   | A             | A                  | NA            |      0 |
| Iowa         | A             | A                  | NA            |      0 |
| Iridaze      | A             | A                  | NA            |      0 |
| jennyG       | A             | NA                 | NA            |      0 |
| kanez        | A             | A                  | NA            |      0 |
| KennethPKU   | A             | A                  | NA            |      0 |
| leppapebc    | A             | A                  | NA            |      0 |
| LH           | A             | A                  | NA            |      0 |
| Lithium      | A             | A                  | NA            |      0 |
| lizx         | A             | A                  | NA            |      0 |
| lnpku        | A             | A                  | NA            |      0 |
| lxy          | A             | A                  | NA            |      0 |
| maonster     | A             | A                  | NA            |      0 |
| mojave       | A             | A                  | NA            |      0 |
| Moony        | A             | A                  | NA            |      0 |
| motaguoke    | A             | A                  | NA            |      0 |
| MrWolffy     | A             | A                  | NA            |      0 |
| Nachtmusik   | A             | A                  | A             |      0 |
| pangshuaige  | A             | A                  | NA            |      0 |
| pkuerljh     | A             | A                  | NA            |      0 |
| Purpose      | A             | NA                 | NA            |      0 |
| puzhe        | A             | A                  | NA            |      0 |
| Qiiiiii      | A             | A                  | NA            |      0 |
| ququlongsha  | A             | A                  | NA            |      0 |
| RayPrime     | A             | A                  | NA            |      0 |
| Reines       | A             | A                  | NA            |      0 |
| RichardGreen | A             | A                  | NA            |      0 |
| rlcheng      | A             | A                  | NA            |      0 |
| ryanli       | A             | A                  | NA            |      0 |
| sanshan      | A             | A                  | NA            |      0 |
| shuchong     | A             | NA                 | NA            |      0 |
| sjwclwnayz   | A             | A                  | NA            |      0 |
| spiridempt   | A             | A                  | NA            |      0 |
| SQ           | A             | A                  | NA            |      0 |
| SrinceW      | A             | A                  | A             |      0 |
| stonez       | A             | A                  | NA            |      0 |
| survivor     | A             | A                  | NA            |      0 |
| Talutsai     | A             | A                  | A             |      0 |
| tangmo       | A             | A                  | A             |      0 |
| Tavstar      | A             | A                  | A             |      0 |
| Tranquilsun  | A             | A                  | NA            |      0 |
| tsiau        | A             | A                  | A             |      0 |
| vitiger      | A             | A                  | NA            |      0 |
| watem        | A             | A                  | NA            |      0 |
| wenxijc      | A             | NA                 | NA            |      0 |
| wky          | A             | A                  | NA            |      0 |
| woctordho    | A             | A                  | NA            |      0 |
| wuyuchuan    | A             | A                  | NA            |      0 |
| xiaohehe     | A             | A                  | NA            |      0 |
| XuLanTu      | A             | A                  | NA            |      0 |
| yuanhuang    | A             | A                  | NA            |      0 |
| YvonneLLL    | A             | A                  | NA            |      0 |
| yydcj        | A             | A                  | NA            |      0 |
| zaiqiang     | A             | A                  | NA            |      0 |
| zaza         | A             | A                  | A             |      0 |
| zinccat      | A             | A                  | NA            |      0 |
| moonl        | NA            | A                  | NA            |      0 |
| ARABBIT      | NA            | A                  | NA            |      0 |
| starlight    | NA            | A                  | NA            |      0 |
| docu         | NA            | A                  | NA            |      0 |
| dengrun      | NA            | A                  | NA            |      0 |
| ckrenren     | NA            | A                  | NA            |      0 |
| zhanyihe     | NA            | A                  | NA            |      0 |
| anotso       | NA            | NA                 | A             |      0 |
| conezy       | NA            | NA                 | A             |      0 |
| dodobus      | NA            | NA                 | A             |      0 |
| hnll         | NA            | NA                 | A             |      0 |
| idudu        | NA            | NA                 | A             |      0 |
| Keib         | NA            | NA                 | A             |      0 |
| kzhengPKU    | NA            | NA                 | A             |      0 |
| pkuhb        | NA            | NA                 | A             |      0 |
| qinwei       | NA            | NA                 | A             |      0 |
| steveblade   | NA            | NA                 | A             |      0 |
| wenjiajia    | NA            | NA                 | A             |      0 |
| wuxian       | NA            | NA                 | A             |      0 |
| xinglian     | NA            | NA                 | A             |      0 |
| yxlixiang    | NA            | NA                 | A             |      0 |
