---
title: "strtoull –, _strtoull_l –, wcstoull –, _wcstoull_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
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
- _wcstoull_l
- _tcstoull
- _tcstoull_l
- wcstoull
- _strtoull_l
- strtoull
dev_langs: C++
helpviewer_keywords:
- strtoull function
- _tcstoull_l function
- _tcstoull function
- _wcstoull_l function
- _strtoull_l function
- wcstoull function
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8af8a6c2d96eb0fa4fd37a41e7f022743ab78d7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="strtoull-strtoulll-wcstoull-wcstoulll"></a>strtoull, _strtoull_l, wcstoull, _wcstoull_l
Převede řetězce na nepodepsané long long celočíselnou hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned long long strtoull(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
unsigned long long _strtoull_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
unsigned long long wcstoull(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
unsigned long long _wcstoull_l(  
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
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 `strtoull`Vrátí převedenou hodnotu, pokud existuje, nebo `ULLONG_MAX` na přetečení. `strtoull`Vrátí hodnotu 0, pokud žádný převod lze provést. `wcstoull`Vrátí hodnoty analogicky na `strtoull`. Pro obě funkce `errno` je nastaven na `ERANGE` případě přetečení nebo podtečení.  
  
 Další informace o návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí převede vstupní řetězec `nptr` k `unsigned long long` celočíselnou hodnotu.  
  
 `strtoull`ukončí čtení řetězce `nptr` u prvního znaku nemůže rozpoznat jako součást číslo. To může být ukončující znak hodnoty null, nebo to může být první číselné znak, který je větší než nebo rovno `base`. Nastavení jazyka `LC_NUMERIC` kategorii národní prostředí určuje rozpoznávání základ – znak v `nptr`; Další informace najdete v tématu [setlocale _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md). `strtoull`a `wcstoull` použít aktuální národní prostředí; `_strtoull_l` a `_wcstoull_l` místo toho použijte národního prostředí, který se předává v, ale jsou identické jinak. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Pokud `endptr` není `NULL`, ukazatel na znak, který zastavena kontroly je uložený v umístění, které ukazuje `endptr`. Pokud žádný převod lze provést (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základní), hodnota `nptr` je uložený v umístění, které ukazuje `endptr`.  
  
 `wcstoull`široká charakterová verze `strtoull` a jeho `nptr` je argumentem široká charakterová řetězce. Tyto funkce, jinak hodnota chovají stejně jako.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstoull`|`strtoull`|`strtoull`|`wcstoull`|  
|`_tcstoull_l`|`strtoull_l`|`_strtoull_l`|`_wcstoull_l`|  
  
 `strtoull`očekává `nptr` tak, aby odkazoval na řetězec v následujícím formátu:  
  
 [`whitespace`] [{`+` &#124; `-`}] [`0` [{ `x` &#124; `X` }]] [`digits` &#124; [`letters`]]  
  
 A `whitespace` může obsahovat místa a karta znaků, které se mají ignorovat; `digits` jsou jeden nebo více desetinných míst; `letters` jsou jeden nebo více znaků 'a' přes 'z' (nebo 'A' až 'Z'). První znak, který se nevejde tento formulář zastaví kontroly. Pokud `base` mezi 2 a 36, je použita jako základní číslo. Pokud `base` 0, počáteční znaky řetězce, který ukazuje `nptr` se používají k určení ve znalostní bázi. Pokud je první znak '0' a druhá znak není 'x' nebo 'X', řetězec interpretována jako osmičková celé číslo. Pokud první znak je '0' a druhá znak je písmeno "x" nebo "X", řetězec interpretována jako hexadecimální celé číslo. Pokud je první znak ' 1' přes ' 9', řetězec interpretována jako desítkové celé číslo. Písmena 'a' do 'z' (nebo 'A' až 'Z') jsou přiřazeny hodnoty 10 až 35; pouze písmena, jejichž přiřazené hodnoty jsou menší než `base` jsou povoleny. První znak mimo rozsah základní zastaví kontroly. Například pokud `base` je 0 a první znak zkontrolovat je '0', osmičková celé číslo se předpokládá, a znak "8" nebo "9" zastaví kontroly. `strtoull`Umožňuje znaménko plus (`+`) nebo symbol mínus (`-`) předpona; úvodní minus znaménko udává, že je Negované návratovou hodnotu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strtoull`|\<stdlib.h >|  
|`wcstoull`|\<stdlib.h > nebo \<wchar.h >|  
|`_strtoull_l`|\<stdlib.h >|  
|`_wcstoull_l`|\<stdlib.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [strtod –](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [localeconv –](../../c-runtime-library/reference/localeconv.md)   
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Funkce řetězců na číselné hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod –, _strtod_l –, wcstod –, _wcstod_l –](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol –, wcstol –, _strtol_l –, _wcstol_l –](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul –, _strtoul_l –, wcstoul –, _wcstoul_l –](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [strtoll –, _strtoll_l –, wcstoll –, _wcstoll_l –](../../c-runtime-library/reference/strtoll-strtoll-l-wcstoll-wcstoll-l.md)   
 [atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)