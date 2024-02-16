# StataGMM
Stata Code - Generalized Method of Moments
 /Modelo 1 - Peridos antes das Crises: 1997-2006/
 
This work aims to identify the key drivers that have propelled infrastructure investment in the European Union. Using econometric analysis of panel data, we investigate the relative importance of macroeconomic, capital market, and institutional factors in determining infrastructure investment. All EU countries were selected (except Malta) and the data used are centered between the years 1997 and 2020. Specifically, we use the Generalized Method of Moments (GMM) command to estimate the parameters in dynamic panel models. The use of the GMM econometric command in this research ensures more accurate and robust results, allowing for the handling of endogeneity and unobserved heterogeneity problems that are commonly encountered in panel data analysis. The results achieved indicate that the macroeconomic variables overlap institutional issues and the level of maturity of the local capital market. Our findings shed light on the factors that are most relevant in driving infrastructure investment in the European Union and can inform the development of more effective public policies in this area. 


 /Modelo 1 - Peridos antes das Crises: 1997-2006/
 
xtset id year

  gen x11 = 0
  replace x11 = 1 if x6 == "AAA"
  replace x11 = 2 if x6 == "AA+"
  replace x11 = 3 if x6 == "AA"
  replace x11 = 4 if x6 == "AA-"
  replace x11 = 5 if x6 == "BBB+"
  replace x11 = 6 if x6 == "BBB-"
  replace x11 = 7 if x6 == "BBB"
  replace x11 = 8 if x6 == "BB+"
  replace x11 = 9 if x6 == "BB-"
  replace x11 = 10 if x6 == "BB"
  replace x11 = 11 if x6 == "B+"
  replace x11 = 12 if x6 == "B"
  replace x11 = 13 if x6 == "B-"
  replace x11 = 14 if x6 == "A+"
  replace x11 = 15 if x6 == "A"
  replace x11 = 16 if x6 == "A-"
  replace x11 = 17 if x6 == "CCC+"
  replace x11 = 18 if x6 == "CC"

rename id country


/* GMM estimation of linear dynamic panel data models */

/* xtdpdgmm: command for diff-GMM, sys-GMM, and GMM estimation with the Ahn and Schmidt (1995) nonlinear moment conditions. Sebastian */


/*One-step diff-GMM */

xtdpdgmm L(0/1).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) nocons vce(r)

xtdpdgmm L(0/1).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, d l(0 0))


/*One-step sys-GMM*/

xtdpdgmm L(0/2).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) nocons vce(r)

xtdpdgmm L(0/2).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, d l(0 0))


outreg2 using myregSys.xls, replace ctitle(Sys_GMM-1997-2006)


 /Modelo 2 - Peridos entre Crises: 2007-2014/
 
xtset id year

  gen x11 = 0
  replace x11 = 1 if x6 == "AAA"
  replace x11 = 2 if x6 == "AA+"
  replace x11 = 3 if x6 == "AA"
  replace x11 = 4 if x6 == "AA-"
  replace x11 = 5 if x6 == "BBB+"
  replace x11 = 6 if x6 == "BBB-"
  replace x11 = 7 if x6 == "BBB"
  replace x11 = 8 if x6 == "BB+"
  replace x11 = 9 if x6 == "BB-"
  replace x11 = 10 if x6 == "BB"
  replace x11 = 11 if x6 == "B+"
  replace x11 = 12 if x6 == "B"
  replace x11 = 13 if x6 == "B-"
  replace x11 = 14 if x6 == "A+"
  replace x11 = 15 if x6 == "A"
  replace x11 = 16 if x6 == "A-"
  replace x11 = 17 if x6 == "CCC+"
  replace x11 = 18 if x6 == "CC"

rename id country


/* GMM estimation of linear dynamic panel data models */

/* xtdpdgmm: command for diff-GMM, sys-GMM, and GMM estimation with the Ahn and Schmidt (1995) nonlinear moment conditions. Sebastian */


/*One-step diff-GMM */

xtdpdgmm L(0/1).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) nocons vce(r)

xtdpdgmm L(0/1).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, d l(0 0))


/*One-step sys-GMM*/

xtdpdgmm L(0/2).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) nocons vce(r)

xtdpdgmm L(0/2).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, d l(0 0))


outreg2 using myregSys.xls, append ctitle(Sys_GMM-2007-2014)


/Modelo 3 - Peridos entre Crises: 2015-2020/
 
xtset id year

  gen x11 = 0
  replace x11 = 1 if x6 == "AAA"
  replace x11 = 2 if x6 == "AA+"
  replace x11 = 3 if x6 == "AA"
  replace x11 = 4 if x6 == "AA-"
  replace x11 = 5 if x6 == "BBB+"
  replace x11 = 6 if x6 == "BBB-"
  replace x11 = 7 if x6 == "BBB"
  replace x11 = 8 if x6 == "BB+"
  replace x11 = 9 if x6 == "BB-"
  replace x11 = 10 if x6 == "BB"
  replace x11 = 11 if x6 == "B+"
  replace x11 = 12 if x6 == "B"
  replace x11 = 13 if x6 == "B-"
  replace x11 = 14 if x6 == "A+"
  replace x11 = 15 if x6 == "A"
  replace x11 = 16 if x6 == "A-"
  replace x11 = 17 if x6 == "CCC+"
  replace x11 = 18 if x6 == "CC"

rename id country


/* GMM estimation of linear dynamic panel data models */

/* xtdpdgmm: command for diff-GMM, sys-GMM, and GMM estimation with the Ahn and Schmidt (1995) nonlinear moment conditions. Sebastian */


/*One-step diff-GMM */

xtdpdgmm L(0/1).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) nocons vce(r)

xtdpdgmm L(0/1).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, d l(0 0))


/*One-step sys-GMM*/

xtdpdgmm L(0/2).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) nocons vce(r)

xtdpdgmm L(0/2).y x1 x2 x3 x4 x7 x8, gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, l(1 3) m(d)) gmm(L.y x1 x2 x3 x4 x5 x7 x8 x9 x11, d l(0 0))


outreg2 using myregSys.xls, append ctitle(Sys_GMM-2015-2020)
