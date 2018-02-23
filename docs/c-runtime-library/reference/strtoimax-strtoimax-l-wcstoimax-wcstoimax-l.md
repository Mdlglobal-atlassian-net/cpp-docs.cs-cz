---
title: "strtoimax, _strtoimax_l –, wcstoimax –, _wcstoimax_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- wcstoimax
- _wcstoimax_l
- _strtoimax_l
- strtoimax
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
- wcstoimax
- _tcstoimax
- strtoimax
- _wcstoimax_l
- _strtoimax_l
- _tcstoimax_l
dev_langs:
- C++
helpviewer_keywords:
- strtoimax funciton
- conversion functions
- _strtoimax_l function
- _wcstoimax_l function
- wcstoimax function
ms.assetid: 4530d3dc-aaac-4a76-b7cf-29ae3c98d0ae
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4125ebf922ed3525d5efd6a92b1273ca18d0fd7d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="strtoimax-strtoimaxl-wcstoimax-wcstoimaxl"></a>strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l
Převede řetězec na celočíselnou hodnotu typu největší podporovaná číslo se znaménkem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
intmax_t strtoimax(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
intmax_t wcstoimax(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
intmax_t _strtoimax_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
intmax_t _wcstoimax_l(  
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
 `strtoimax` Vrátí hodnotu, která je reprezentována v řetězci `nptr`, s výjimkou případů, kdy reprezentace by způsobilo přetečení – v takovém případě vrátí `INTMAX_MAX` nebo `INTMAX_MIN`, a `errno` je nastaven na `ERANGE`. Funkce vrátí hodnotu 0, pokud žádný převod lze provést. `wcstoimax` Vrátí hodnoty analogicky na `strtoimax`.  
  
 `INTMAX_MAX` a `INTMAX_MIN` jsou definovány v stdint.h.  
  
 Pokud `nptr` je `NULL` nebo `base` nenulový a je menší než 2 nebo vyšší než 36, `errno` je nastaven na `EINVAL`.  
  
 Další informace o návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `strtoimax` Funkce převede `nptr` k `intmax_t`. Široká charakterová verzi `strtoimax` je `wcstoimax`; jeho `nptr` je argumentem široká charakterová řetězce. Tyto funkce, jinak hodnota chovají stejně jako. Obě funkce Zastavit čtení řetězec `nptr` u prvního znaku nemůže rozpoznat jako součást číslo. To může být ukončující znak hodnoty null, nebo to může být první číselné znak, který je větší než nebo rovno `base`.  
  
 Jako národní prostředí `LC_NUMERIC` kategorie nastavení určuje rozpoznávání základ – znak v `nptr`; Další informace najdete v tématu [setlocale _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). Funkce, které nemají `_l` příponu použít aktuální národní prostředí; `_strtoimax_l` a `_wcstoimax_l` jsou stejné jako odpovídající funkce, které nemají `_l` přípona s tím rozdílem, že místo toho používají národní prostředí, je předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Pokud `endptr` není `NULL`, ukazatel na znak, který zastavena kontroly je uložený v umístění, které ukazuje `endptr`. Pokud žádný převod lze provést (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základní), hodnota `nptr` je uložený v umístění, které ukazuje `endptr`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstoimax`|`strtoimax`|`strtoimax`|`wcstoimax`|  
|`_tcstoimax_l`|`strtoimax_l`|`_strtoimax_l`|`_wcstoimax_l`|  
  
 `strtoimax` očekává `nptr` tak, aby odkazoval na řetězec v následujícím formátu:  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits` &#124; `letters`]  
  
 A `whitespace` může obsahovat místa a karta znaků, které se mají ignorovat; `digits` jsou jeden nebo více desetinných míst; `letters` jsou jeden nebo více znaků 'a' přes 'z' (nebo 'A' až 'Z'). První znak, který se nevejde tento formulář zastaví kontroly. Pokud `base` mezi 2 a 36, je použita jako základní číslo. Pokud `base` 0, počáteční znaky řetězce, na kterou odkazuje `nptr` se používají k určení ve znalostní bázi. Pokud je první znak '0' a druhá znak není 'x' nebo 'X', řetězec interpretována jako osmičková celé číslo. Pokud první znak je '0' a druhá znak je písmeno "x" nebo "X", řetězec interpretována jako hexadecimální celé číslo. Pokud je první znak ' 1' přes ' 9', řetězec interpretována jako desítkové celé číslo. Písmena 'a' do 'z' (nebo 'A' až 'Z') jsou přiřazeny hodnoty 10 až 35; pouze písmena, jejichž přiřazené hodnoty jsou menší než `base` jsou povoleny. První znak mimo rozsah základní zastaví kontroly. Například pokud `base` je 0 a první znak zkontrolovat je '0', osmičková celé číslo se předpokládá, a znak "8" nebo "9" by zastavit kontroly.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strtoimax`, `_strtoimax_l`, `wcstoimax`, `_wcstoimax_l`|\<inttypes.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [localeconv –](../../c-runtime-library/reference/localeconv.md)   
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Funkce řetězců na číselné hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod –, _strtod_l –, wcstod –, _wcstod_l –](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol –, wcstol –, _strtol_l –, _wcstol_l –](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul –, _strtoul_l –, wcstoul –, _wcstoul_l –](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l](../../c-runtime-library/reference/strtoumax-strtoumax-l-wcstoumax-wcstoumax-l.md)   
 [atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)