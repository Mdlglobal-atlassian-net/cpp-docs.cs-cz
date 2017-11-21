---
title: "Použití mapování obecného textu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _UNICODE
dev_langs: C++
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f4067e9555200805631fb72fe3e40afa09c168e3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-generic-text-mappings"></a>Použití mapování obecného textu
**Konkrétní Microsoft**  
  
 Pro zjednodušení vývoj kódu pro různé mezinárodní trhy, běhové knihovny Microsoft poskytuje mapování "obecného textu" specifické pro společnost Microsoft pro mnoho typů dat, rutiny a jiné objekty. Tato mapování jsou definovány v Tchar –. H. Tato mapování názvu můžete použít k zápisu obecný kód, který může být zkompilovány pro všechny tři druhy znakových sad: ASCII (SBCS), MBCS nebo Unicode, v závislosti na manifestu konstanta definovat pomocí `#define` příkaz. Mapování obecného textu jsou rozšíření Microsoft, které nejsou kompatibilní ANSI.  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>Preprocesor – direktivy pro mapování obecného textu  
  
|#define – direktiva|Kompilované verze|Příklad|  
|--------------|----------------------|-------------|  
|`_UNICODE`|Unicode (široké znaky)|`_tcsrev`se mapuje na`_wcsrev`|  
|`_MBCS`|Vícebajtových znaků|`_tcsrev`se mapuje na`_mbsrev`|  
|Žádný (výchozí: ani `_UNICODE` ani `_MBCS` definované)|SBCS (ASCII)|`_tcsrev`se mapuje na`strrev`|  
  
 Například funkce obecného textu `_tcsrev`, definované v Tchar –. H, se mapuje na `mbsrev` Pokud `MBCS` byla definována v programu, nebo na `_wcsrev` Pokud `_UNICODE` byla definována. V opačném případě `_tcsrev` mapuje `strrev`.  
  
 Typ obecné textové datové `_TCHAR`, je také definován Tchar –. H, se mapuje na typ `char` Pokud `_MBCS` je definován na typ `wchar_t` Pokud `_UNICODE` definované a na typ `char` Pokud je definována žádná konstanta. Tchar – jsou součástí jiných mapování datového typu. H pro programování jednoduchost, ale `_TCHAR` je typ, který je velmi užitečné.  
  
### <a name="generic-text-data-type-mappings"></a>Mapování obecného textu datového typu  
  
|Název typu datového obecného textu|SBCS (_UNICODE, není definována _MBCS)|_MBCS definováno|_UNICODE definováno|  
|----------------------------------|--------------------------------------------|--------------------|-----------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T`nebo`_TEXT`|Neplatí (odebraná pomocí preprocessor)|Neplatí (odebraná pomocí preprocessor)|`L`(převede následující znak nebo řetězec k jeho protějšku Unicode)|  
  
 Úplný seznam mapování obecného textu rutin, proměnné a další objekty, najdete v části [mapování obecného textu](../c-runtime-library/generic-text-mappings.md).  
  
 Následující fragmenty kódu ilustrují použití `_TCHAR` a `_tcsrev` pro mapování MBCS, kódování Unicode a SBCS modely.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Pokud `MBCS` byla definována, preprocesor namapuje předchozím fragmentu na následující kód:  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Pokud `_UNICODE` byla definována, preprocesor namapuje stejného fragmentu na následující kód:  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Pokud ani `_MBCS` ani `_UNICODE` byla definována, preprocesor mapuje fragment kódu jednobajtové ASCII, následujícím způsobem:  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 Proto můžete napsat, udržovat a zkompilovat soubor jednoho zdrojového kódu ke spuštění rutiny, které jsou specifické pro všechny tři druhy znakových sad.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Mapování obecného textu](../c-runtime-library/generic-text-mappings.md)   
 [Mapování datového typu](../c-runtime-library/data-type-mappings.md)   
 [Mapování konstant a globálních proměnných](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [Mapování rutiny](../c-runtime-library/routine-mappings.md)   
 [Ukázka programu obecného textu](../c-runtime-library/a-sample-generic-text-program.md)