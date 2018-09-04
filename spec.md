# Personal Identification Number Specification

_Version 0.1 (draft)_

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](http://www.ietf.org/rfc/rfc2119.txt).

The _Personal Identification Number Specification_ is licensed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) license.

## Overview

This document contains a technical specification for _Personal Identification Number_ (_<abbr title="Cod Numeric Personal">C.N.P.</abbr>_).

In [Romania](https://en.wikipedia.org/wiki/Romania), a C.N.P. is a unique 13 (thirteen) characters number, which is assigned to each person born in Romania and Romanian residents.

It was introduced in 1978 and it is used as an identifier in systems that needs to manage personal data and differentiate individuals.

## Terminology

When referring to _Personal Identification Number_, "C.N.P." abbreviation MUST be used. When the context doesn't allow the dots usage, like inside a code base where the syntax impose such limitation, "CNP" alternative abbreviation MAY be used.

"_Cod Numeric Personal_" and/or English translation "_Personal Identification Number_" SHOULD be used to explain "C.N.P." and "CNP" abbreviations.

**Sample**:
```html
<!-- For Romanian speakers -->
<abbr title="Cod Numeric Personal">C.N.P.</abbr>

<!-- For English speakers -->
<abbr title="Personal Identification Number">C.N.P.</abbr>
```

```cpp
/**
 * Validates Personal Identification Number for 
 * Romanian citizens and residents.
 */
int validateCNP(char cnp[13]) { /* the code */ }
```

## Legislation

The conditions, necessary documents for the issuance of identity documents and C.N.P. structure are regulated by:

- [OUG no. 97/2005][OUG 97/2005] regarding the evidence, domicile, residence and identity documents of the Romanian citizens, republished, with the subsequent modifications and completions.
- [H.G. no. 1.375/2006][H.G. 1.375/2006] for the approval of Methodological Norms for the unitary application of the legal provisions regarding the Romanian citizens identity, domicile, residence and identity documents, with the subsequent modifications and completions.
- [Law no. 122/2006][Law 122/2006] regarding asylum in Romania, with the subsequent modifications and completions.
- [H.G. 1.251/2006][H.G. 1.251/2006] for the approval of the Methodological Norms on application of [Law no. 122/2006][Law 122/2006] regarding asylum in Romania.

## Issuance

Each C.N.P. for Romanian citizens is issued by _Directorate for Personal Records and Database Management_ ([<abbr title="Directia pentru Evidenta Persoanelor si Administrarea Bazelor de Date">D.E.P.A.B.D.</abbr>][DEPABD]), which is written on birth certificate, ID card and passport.  
Romanian residents receive their C.N.P. from _General Inspectorate for Immigration_ ([<abbr title="Inspectoratul General pentru Imigrari">I.G.I.</abbr>][IGI]) which is written on their resident permit.

## Structure

C.N.P is a 13 (thirteen) digit number, unique to each individual and consists of 7 (seven) components:

    [S][AA][LL][ZZ][JJ][NNN][C]

### S component

Component **S** represents the gender (_sex_) and the century in which the person was born and MUST have one of the following values:

- **1** = Male, born between 1900 - 1999
- **2** = Female, born between 1900 - 1999
- **3** = Male, born between 1800 - 1899 
- **4** = Female, born between 1800 - 1899
- **5** = Male, born between 2000 - 2099
- **6** = Female, born between 2000 - 2099
- **7** = Male resident (_century does not apply_)
- **8** = Female resident (_century does not apply_)

### AA component

Component **AA** represents the last 2 (two) digits from the year of birth.

### LL component

Component **LL** represents the month of birth in 2 (two) digits format.

### ZZ component

Component **ZZ** represents the day of birth in 2 (two) digits format.

### JJ component

Component **JJ** is formed by 2 (two) digits and represents the County code (_and District number for Bucharest_) in which the person was born or
where (s)he was domiciled at the time when papers were issued.

County code (*JJ*) MUST have one of the following values:

- 01 = Alba
- 02 = Arad
- 03 = Argeş
- 04 = Bacău
- 05 = Bihor
- 06 = Bistriţa-Năsăud
- 07 = Botoşani
- 08 = Braşov
- 09 = Brăila
- 10 = Buzău
- 11 = Caraş-Severin
- 12 = Cluj
- 13 = Constanţa
- 14 = Covasna
- 15 = Dâmboviţa
- 16 = Dolj
- 17 = Galaţi
- 18 = Gorj
- 19 = Harghita
- 20 = Hunedoara
- 21 = Ialomiţa
- 22 = Iaşi
- 23 = Ilfov
- 24 = Maramureş
- 25 = Mehedinţi
- 26 = Mureş
- 27 = Neamţ
- 28 = Olt
- 29 = Prahova
- 30 = Satu Mare
- 31 = Sălaj
- 32 = Sibiu
- 33 = Suceava
- 34 = Teleorman
- 35 = Timiş
- 36 = Tulcea
- 37 = Vaslui
- 38 = Vâlcea
- 39 = Vrancea
- 40 = Bucureşti
- 41 = Bucureşti District 1
- 42 = Bucureşti District 2
- 43 = Bucureşti District 3 
- 44 = Bucureşti District 4
- 45 = Bucureşti District 5
- 46 = Bucureşti District 6
- 47 = Bucureşti District 7 (_now defunct_)
- 48 = Bucureşti District 8 (_now defunct_)
- 51 = Călăraşi
- 52 = Giurgiu

Regarding Bucharest's Districts, there have been some changes since Personal Identification Number was introduced in 
1978, as follows:

- Bucharest District 3 was merged with District 2 in 1979 and resulted current District 2
- Bucharest District 4 is known as District 3 since 1979
- Bucharest District 5 is known as District 4 since 1979
- Bucharest District 6 is known as District 5 since 1979
- Bucharest District 7 is known as District 6 since 1979
- Bucharest District 8 was merged with District 1 in 1979 and resulted current District 1

Implementing (_now defunct_) Districts 7 and 8 is OPTIONAL.  
If Districts 7 and 8 are implemented, their usage SHALL be limited to dates prior to December 19, 1979[^1]. Any C.N.P. with one of these two districts and a date which succeeds December 19, 1979[^1] MUST NOT validate successfully.

### NNN component

Component **NNN** represents a sequential number in range of `001` - `999`, which differentiates individuals of same gender, born in the same place and at the same date (_i.e: AALLZZ_).

### C component

Component **C** represents the control number ([checksum](https://en.wikipedia.org/wiki/Checksum)), used to detect potential errors which may have been introduced during typing, transmission and/or storage.

## Validation

Validation of a C.N.P. consists of calculating the control number (_C component_) and comparing it with the one provided. If they are not equal, validation SHALL NOT be successful.

This control number SHALL be calculated using the constant `279146358279` as follows:

- Each digit from the first 12 (twelve) digits of the C.N.P. SHALL be multiplied with its correspondent from the constant.
- Resulting sums MUST be added together and the grand total MUST be divided by 11
- If the division remainder is less than 10 (ten), that MUST be used as control number (**C**)
- If the division remainder is 10 (ten), the control number (**C**) MUST be 1 (one)

## Changing the C.N.P. of an individual

A new C.N.P. is assigned to the same individual only in one of the following situations:

- Birth certificate was rectified and one of the information that is part of the C.N.P. was changed.
- The birth certificate entry for C.N.P. has been erroneously written.
- C.N.P. was wrongly assigned.
- The applicant had a sex change.
- There are inconsistencies regarding C.N.P.

[OUG 97/2005]: http://www.cdep.ro/pls/legis/legis_pck.htp_act_text?idt=65141
[H.G. 1.375/2006]: http://www.cdep.ro/pls/legis/legis_pck.htp_act?ida=67474
[Law 122/2006]: http://www.cdep.ro/pls/legis/legis_pck.htp_act?ida=64543
[H.G. 1.251/2006]: http://www.cdep.ro/pls/legis/legis_pck.htp_act?ida=67142
[DEPABD]: http://depabd.mai.gov.ro/index_eng.html
[IGI]: http://igi.mai.gov.ro/en
[^1]: Great National Assembly. Law no. 31/1979 for the approval of the Decree of the Council of State no. 284/1979 on the establishment of Bucharest's districts. Romania: Official Bulletin no. 103/1979, 1979.
