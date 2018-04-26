---
title: Znak klasifikace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.types.character
dev_langs:
- C++
helpviewer_keywords:
- character classification routines
- characters, testing
ms.assetid: 3b6c8f0b-9701-407a-b384-9086698773f5
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 40cc501e89b12b2d2c13f5e64d9e6bf8a6bc4a13
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="character-classification"></a>Klasifikace znaků

Každý z těchto rutin testy zadanou znakovou, široká znaková nebo vícebajtových znaků pro spokojenost podmínku. (Podle definice znaků ASCII nastavit rozsahu od 0 do 127, jsou podmnožinou všech vícebajtových znakových sad. Například japonské katakana obsahuje ASCII jako dobře jako jiné znaky než ASCII.)

 Podmínky testu se nastavení vztahuje **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná.

 Obecně tyto rutiny spouštět rychleji, než může zapsat a měl by být favored přes. Například následující kód provede něco pomalejší než volání `isalpha(c)`:

```C
if ((c >= 'A') && (c <= 'Z')) || ((c >= 'a') && (c <= 'z'))
    return TRUE;
```

## <a name="character-classification-routines"></a>Rutiny klasifikace znaků

|Rutina|Stav testu znak|
|-------------|------------------------------|
|[isalnum –, iswalnum –, _isalnum_l –, _iswalnum_l –](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md), [_ismbcalnum –, _ismbcalnum_l –, _ismbcalpha –, _ismbcalpha_l –, _ismbcdigit –, _ismbcdigit_l –](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumerické|
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumerické|
|[isalpha –, iswalpha –, _isalpha_l –, _iswalpha_l –](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md), [_ismbcalnum –, _ismbcalnum_l –, _ismbcalpha –, _ismbcalpha_l –, _ismbcdigit –, _ismbcdigit_l –](../c-runtime-library/reference/ismbcalnum-functions.md)|Abecedy|
|[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|ASCII|
|[zjistit, iswblank, _isblank_l, _iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md), [_ismbcsblank _ismbcsblank_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Prázdný (místo nebo vodorovné karty)|
|[iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|Ovládací prvek|
|[iscsym –, iscsymf –, __iscsym –, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l –, _iswcsym_l –, _iscsymf_l –, _iswcsymf_l –](../c-runtime-library/reference/iscsym-functions.md)|Písmeno, podtržítko nebo číslice|
|[iscsym –, iscsymf –, __iscsym –, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l –, _iswcsym_l –, _iscsymf_l –, _iswcsymf_l –](../c-runtime-library/reference/iscsym-functions.md)|Písmenem nebo podtržítkem|
|[IsDigit –, iswdigit –, _isdigit_l –, _iswdigit_l –](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md), [_ismbcalnum –, _ismbcalnum_l –, _ismbcalpha –, _ismbcalpha_l –, _ismbcdigit –, _ismbcdigit_l –](../c-runtime-library/reference/ismbcalnum-functions.md)|Desítková číslice|
|[isgraph –, iswgraph –, _isgraph_l –, _iswgraph_l –](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md), [_ismbcgraph –, _ismbcgraph_l –, _ismbcprint –, _ismbcprint_l –, _ismbcpunct –, _ismbcpunct_l –, _ismbcblank, _ismbcblank_l, _ismbcspace –, _ismbcspace_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Tisknutelná než místa|
|[islower –, iswlower –, _islower_l –, _iswlower_l –](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md), [_ismbclower –, _ismbclower_l –, _ismbcupper –, _ismbcupper_l –](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Malá|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Hiragana|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Katakana|
|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Právní vícebajtových znaků|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Japonsko úrovni 0 vícebajtových znaků|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Japonsko úroveň 1 vícebajtových znaků|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Japonsko úroveň 2 vícebajtových znaků|
|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Jiné než alfanumerické vícebajtových znaků|
|[isprint –, iswprint –, _isprint_l –, _iswprint_l –](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md), [_ismbcgraph –, _ismbcgraph_l –, _ismbcprint –, _ismbcprint_l –, _ismbcpunct –, _ismbcpunct_l –, _ismbcblank, _ismbcblank_l, _ismbcspace –, _ismbcspace_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Tisknutelná|
|[ispunct –, iswpunct –, _ispunct_l –, _iswpunct_l –](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md), [_ismbcgraph –, _ismbcgraph_l –, _ismbcprint –, _ismbcprint_l –, _ismbcpunct –, _ismbcpunct_l –, _ismbcblank, _ismbcblank_l, _ismbcspace –, _ismbcspace_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Interpunkční znaménka|[System::Char::IsPunctuation](https://msdn.microsoft.com/en-us/library/system.char.ispunctuation.aspx)|
|[isspace –, iswspace –, _isspace_l –, _iswspace_l –](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md), [_ismbcgraph –, _ismbcgraph_l –, _ismbcprint –, _ismbcprint_l –, _ismbcpunct –, _ismbcpunct_l –, _ismbcblank, _ismbcblank_l, _ismbcspace –, _ismbcspace_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Prázdné znaky|[System::Char::IsWhiteSpace](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)|
|[Isupper –, iswupper –](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md), [_ismbclower –, _ismbclower_l –, _ismbcupper –, _ismbcupper_l –](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Velká písmena|
|[_isctype, iswctype, _isctype_l, _iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|Vlastnost určeného *desc* argument|
|[isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|Šestnáctková číslice|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Vrátí délku platný vícebajtových znaků; Výsledek bude záviset na **LC_CTYPE –** kategorie nastavení aktuální národní prostředí|

## <a name="see-also"></a>Viz také

[Univerzální C runtime rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>