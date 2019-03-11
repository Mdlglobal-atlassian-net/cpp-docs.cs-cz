---
title: Klasifikace znaků
ms.date: 11/04/2016
f1_keywords:
- c.types.character
helpviewer_keywords:
- character classification routines
- characters, testing
ms.assetid: 3b6c8f0b-9701-407a-b384-9086698773f5
ms.openlocfilehash: 757eeac41ecd4e300b7aabef122a8dbdd7e79e11
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739762"
---
# <a name="character-classification"></a>Klasifikace znaků

Každá z těchto rutin testuje zadaný jednobajtový znak, široký znak nebo vícebajtový znaků na splnění podmínky. (Podle definice je znaková sada ASCII mezi 0 a 127 podmnožinou všech vícebajtových znakových sad jsou. Například japonská katakana zahrnuje ASCII i další ne ASCII znaky.)

Testovací podmínku jsou ovlivněny nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze těchto funkcí bez **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí místo něho předán v.

Tyto rutiny obvykle provádějí rychleji než testy, které můžete napíšete a musí jim být dána přednost. Například následující kód se provádí pomaleji, než volání `isalpha(c)`:

```C
if ((c >= 'A') && (c <= 'Z')) || ((c >= 'a') && (c <= 'z'))
    return TRUE;
```

## <a name="character-classification-routines"></a>Rutiny klasifikace znaku

|Rutina|Znak testovací podmínky|
|-------------|------------------------------|
|[isalnum iswalnum –, _isalnum_l – _iswalnum_l –](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md), [_ismbcalnum – _ismbcalnum_l –, _ismbcalpha –, _ismbcalpha_l –, _ismbcdigit –, _ismbcdigit_l –](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumerické znaky|
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Vícebajtové alfanumerické znaky|
|[isalpha iswalpha –, _isalpha_l – _iswalpha_l –](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md), [_ismbcalnum – _ismbcalnum_l –, _ismbcalpha –, _ismbcalpha_l –, _ismbcdigit –, _ismbcdigit_l –](../c-runtime-library/reference/ismbcalnum-functions.md)|Abecedy|
|[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|ASCII|
|[isblank iswblank, _isblank_l _iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md), [_ismbcsblank _ismbcsblank_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Prázdné (mezera nebo horizontální tabelátor)|
|[iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|Control|
|[iscsym, iscsymf, __iscsym, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|Písmeno, znak podtržení nebo číslice|
|[iscsym, iscsymf, __iscsym, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|Písmeno nebo znak podtržení|
|[IsDigit iswdigit –, _isdigit_l – _iswdigit_l –](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md), [_ismbcalnum – _ismbcalnum_l –, _ismbcalpha –, _ismbcalpha_l –, _ismbcdigit –, _ismbcdigit_l –](../c-runtime-library/reference/ismbcalnum-functions.md)|Desítková číslice|
|[isgraph iswgraph –, _isgraph_l – _iswgraph_l –](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md), [_ismbcgraph – _ismbcgraph_l –, _ismbcprint –, _ismbcprint_l –, _ismbcpunct –, _ismbcpunct_l –, _ismbcblank, _ismbcblank_l, _ismbcspace –, _ismbcspace_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Tisknutelný jiný než mezera|
|[islower iswlower –, _islower_l – _iswlower_l –](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md), [_ismbclower – _ismbclower_l –, _ismbcupper – _ismbcupper_l –](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Malá|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Hiragana|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Katakana|
|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Platné vícebajtové znaky|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Vícebajtový znak úrovně Japonsko 0|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Japonsko level 1 vícebajtového znaku|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Japonsko level 2 vícebajtového znaku|
|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Neabecední vícebajtové znakové|
|[isprint iswprint –, _isprint_l – _iswprint_l –](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md), [_ismbcgraph – _ismbcgraph_l –, _ismbcprint –, _ismbcprint_l –, _ismbcpunct –, _ismbcpunct_l –, _ismbcblank, _ismbcblank_l, _ismbcspace –, _ismbcspace_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Tisknutelný|
|[ispunct iswpunct –, _ispunct_l – _iswpunct_l –](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md), [_ismbcgraph – _ismbcgraph_l –, _ismbcprint –, _ismbcprint_l –, _ismbcpunct –, _ismbcpunct_l –, _ismbcblank, _ismbcblank_l, _ismbcspace –, _ismbcspace_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Interpunkční znaménka|
|[isspace iswspace –, _isspace_l – _iswspace_l –](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md), [_ismbcgraph – _ismbcgraph_l –, _ismbcprint –, _ismbcprint_l –, _ismbcpunct –, _ismbcpunct_l –, _ismbcblank, _ismbcblank_l, _ismbcspace –, _ismbcspace_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Prázdné znaky|
|[isupper iswupper –](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md), [_ismbclower – _ismbclower_l –, _ismbcupper – _ismbcupper_l –](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Velká písmena|
|[_isctype, iswctype, _isctype_l, _iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|Vlastnost určenou *desc* argument|
|[isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|Šestnáctková číslice|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Vrátí délku platného vícebajtového znaku. Výsledek závisí na **LC_CTYPE** nastavením kategorie aktuálního národního prostředí|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
