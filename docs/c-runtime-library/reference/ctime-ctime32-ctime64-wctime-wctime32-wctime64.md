---
title: "CTime –, _ctime32 –, _ctime64 –, _wctime –, _wctime32 –, _wctime64 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
dev_langs: C++
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 42b5e0e222dd3b182ac6ea203d37a3f97450fd20
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctime-ctime32-ctime64-wctime-wctime32-wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
Převést na řetězec hodnotu času a upravit nastavení místního časového pásma. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [ctime_s –, _ctime32_s –, _ctime64_s –, _wctime_s –, _wctime32_s –, _wctime64_s –](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *ctime(   
   const time_t *timer   
);  
char *_ctime32(   
   const __time32_t *timer )  
;  
char *_ctime64(   
   const __time64_t *timer )  
;  
wchar_t *_wctime(   
   const time_t *timer   
);  
wchar_t *_wctime32(   
   const __time32_t *timer  
);  
wchar_t *_wctime64(   
   const __time64_t *timer   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `timer`  
 Ukazatel na uložené čas.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na výsledném řetězci znaků. `NULL`bude vrácen, pokud:  
  
-   `time`představuje datum před půlnoc, 1. ledna 1970 UTC.  
  
-   Pokud používáte `_ctime32` nebo `_wctime32` a `time` představuje datum po 23:59:59 18 leden 2038 UTC.  
  
-   Pokud používáte `_ctime64` nebo `_wctime64` a `time` představuje datum po 23:59:59, 31. prosince 3000, UTC.  
  
 `ctime`Vložená funkce, jehož výsledkem je `_ctime64` a `time_t` je ekvivalentní `__time64_t`. Pokud potřebujete vynutit kompilátoru interpretovat `time_t` jako starý 32bitovou verzi `time_t`, můžete definovat `_USE_32BIT_TIME_T`. Provedete to způsobí, že `ctime` k vyhodnocení `_ctime32`. Není doporučeno, protože vaše aplikace může selhat po 18. ledna 2038, a není povoleno na 64bitových platformách.  
  
## <a name="remarks"></a>Poznámky  
 `ctime` Funkce převede hodnotu čas, který je uložený jako [time_t](../../c-runtime-library/standard-types.md) hodnotu na řetězec znaků. `timer` Hodnota se obvykle získávají z volání [čas](../../c-runtime-library/reference/time-time32-time64.md), která vrátí počet sekund uběhlých od půlnoci (00: 00:00), 1. ledna 1970, koordinovaný světový čas (UTC). Návratová hodnota řetězec obsahuje přesně 26 znaků a má tvar:  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 24 hodin se používá. Všechna pole mít konstantní šířky. Znak nového řádku (\n) a znak hodnoty null (\0) zabírají posledních dvou pozic řetězce.  
  
 Řetězec převedený znaků se také upraví podle nastavení zóny Místní čas. Najdete v článku `time`, [_ftime –](../../c-runtime-library/reference/ftime-ftime32-ftime64.md), a [místní čas](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) funkce informace o konfiguraci místní čas a [_tzset –](../../c-runtime-library/reference/tzset.md) funkce podrobné informace o definování časové pásmo prostředí a globální proměnné.  
  
 Volání `ctime` upraví jedné staticky přidělené vyrovnávací paměti používané `gmtime` a `localtime` funkce. Každé volání na jednu z těchto rutin zničí výsledek předchozí volání. `ctime`sdílí statické vyrovnávací paměti s `asctime` funkce. Proto volání `ctime` zničí výsledky všech předchozích volání `asctime`, `localtime`, nebo `gmtime`.  
  
 `_wctime`a `_wctime64` jsou verze široká charakterová `ctime` a `_ctime64`; ukazatel vrácením široká charakterová řetězec. V opačném `_ctime64`, `_wctime`, a `_wctime64` chovají stejně jako na `ctime`.  
  
 Tyto funkce ověřit jejich parametrů. Pokud `timer` je ukazatel s hodnotou null, nebo pokud je hodnota časovače záporná, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, vrátí funkce `NULL` a nastavte `errno` k `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tctime`|`ctime`|`ctime`|`_wctime`|  
|`_tctime32`|`_ctime32`|`_ctime32`|`_wctime32`|  
|`_tctime64`|`_ctime64`|`_ctime64`|`_wctime64`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`ctime`|\<Time.h >|  
|`_ctime32`|\<Time.h >|  
|`_ctime64`|\<Time.h >|  
|`_wctime`|\<Time.h > nebo \<wchar.h >|  
|`_wctime32`|\<Time.h > nebo \<wchar.h >|  
|`_wctime64`|\<Time.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_ctime64.c  
// compile with: /W3  
/* This program gets the current  
 * time in _time64_t form, then uses ctime to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   __time64_t ltime;  
  
   _time64( &ltime );  
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996  
   // Note: _ctime64 is deprecated; consider using _ctime64_s  
}  
```  
  
```Output  
The time is Wed Feb 13 16:04:43 2002  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [asctime –, _wasctime –](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime_s –, _ctime32_s –, _ctime64_s –, _wctime_s –, _wctime32_s –, _wctime64_s –](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [_ftime – _ftime32 –, _ftime64 –](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime – _gmtime32 –, _gmtime64 –](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [místní čas, _localtime32 –, _localtime64 –](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [čas, _time32 –, _time64 –](../../c-runtime-library/reference/time-time32-time64.md)