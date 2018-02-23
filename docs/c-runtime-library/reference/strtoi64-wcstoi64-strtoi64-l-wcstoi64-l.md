---
title: "_strtoi64 –, _wcstoi64 –, _strtoi64_l –, _wcstoi64_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _strtoi64
- _strtoi64_l
- _wcstoi64_l
- _wcstoi64
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strtoi64
- strtoi64
- _stroi64_l
- _wcstoi64_l
- wcstoi64_l
- _wcstoi64
- wcstoi64
- strtoi64_l
dev_langs:
- C++
helpviewer_keywords:
- _strtoi64 function
- _wcstoi64 function
- _strtoi64_l function
- string conversion, to integers
- _wcstoi64_l function
- strtoi64_l function
- wcstoi64 function
- strtoi64 function
- wcstoi64_l function
ms.assetid: ea2abc50-7bfe-420e-a46b-703c3153593a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a383d53c762f4bd15d7a45288bb2ef4e7e452ee
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="strtoi64-wcstoi64-strtoi64l-wcstoi64l"></a>_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l
Převést řetězec na `__int64` hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__int64 _strtoi64(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
__int64 _wcstoi64(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
__int64 _strtoi64_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
__int64 _wcstoi64_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nptr`  
 Řetězce ukončené hodnotou Null pro převod.  
  
 `endptr`  
 Ukazatel na znak, který zastaví kontroly.  
  
 `base`  
 Číslo základní k použití.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Funkce `_strtoi64` vrátí hodnotu představovanou řetězcem `nptr` s výjimkou případů, kdy by reprezentace způsobila přetečení. V takovém případě vrátí hodnotu `_I64_MAX` nebo `_I64_MIN`. Pokud žádný převod lze provést, vrátí funkce 0. `_wcstoi64` Vrátí hodnoty analogicky na `strtoi64`.  
  
 `_I64_MAX` a `_I64_MIN` jsou definovány v omezení. H.  
  
 Pokud `nptr` je `NULL` nebo `base` nenulový a je menší než 2 nebo vyšší než 36, `errno` je nastaven na `EINVAL`.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratové kódy.  
  
## <a name="remarks"></a>Poznámky  
 `_strtoi64` Funkce převede `nptr` k `__int64`. Obě funkce Zastavit čtení řetězec `nptr` u prvního znaku nemůže rozpoznat jako součást číslo. To může být ukončující znak hodnoty null, nebo to může být první číselné znak větší než nebo rovna hodnotě `base`. `_wcstoi64` široká charakterová verze `_strtoi64`; jeho `nptr` je argumentem široká charakterová řetězce. Tyto funkce chovají stejně jako jinak.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstoi64`|`_strtoi64`|`_strtoi64`|`_wcstoi64`|  
|`_tcstoi64_l`|`_strtoi64_l`|`_strtoi64_l`|`_wcstoi64_l`|  
  
 Jako národní prostředí `LC_NUMERIC` kategorie nastavení určuje rozpoznávání základ – znak v `nptr` *;* Další informace najdete v tématu [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). Funkce bez přípony _l použít aktuální národní prostředí; `_strtoi64_l` a `_wcstoi64_l` jsou stejné jako odpovídající funkce bez `_l` přípona s tím rozdílem, že používají místo předaná národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Pokud `endptr` není `NULL`, ukazatel na znak, který zastavena kontroly je uložený v umístění, na kterou odkazuje `endptr`. Pokud žádný převod lze provést (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základní), hodnota `nptr` je uložený v umístění, na kterou odkazuje `endptr`.  
  
 `_strtoi64` očekává `nptr` tak, aby odkazoval na řetězec v následujícím formátu:  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits`]  
  
 A `whitespace` může obsahovat místa a karta znaků, které se mají ignorovat; `digits` jsou jeden nebo více desetinných míst. První znak, který se nevejde tento formulář zastaví kontroly. Pokud `base` mezi 2 a 36, je použita jako základní číslo. Pokud `base` 0, počáteční znaky řetězce, na kterou odkazuje `nptr` se používají k určení ve znalostní bázi. Pokud první znak je 0 a druhý znak není 'x' nebo 'X', řetězec interpretována jako osmičková celé číslo. Pokud první znak je '0' a druhá znak je písmeno "x" nebo "X", řetězec interpretována jako hexadecimální celé číslo. Pokud je první znak ' 1' přes ' 9', řetězec interpretována jako desítkové celé číslo. Písmena 'a' do 'z' (nebo 'A' až 'Z') jsou přiřazeny hodnoty 10 až 35; pouze písmena, jejichž přiřazené hodnoty jsou menší než `base` jsou povoleny. První znak mimo rozsah základní zastaví kontroly. Například pokud `base` je 0 a první znak zkontrolovat je '0', osmičková celé číslo se předpokládá, a znak "8" nebo "9" zastaví kontroly.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_strtoi64`, `_strtoi64_l`|\<stdlib.h>|  
|`_wcstoi64`, `_wcstoi64_l`|\<stdlib.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [localeconv –](../../c-runtime-library/reference/localeconv.md)   
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Funkce řetězců na číselné hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod –, _strtod_l –, wcstod –, _wcstod_l –](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtoul –, _strtoul_l –, wcstoul –, _wcstoul_l –](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)