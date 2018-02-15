---
title: "ctime_s –, _ctime32_s –, _ctime64_s –, _wctime_s –, _wctime32_s –, _wctime64_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
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
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
dev_langs:
- C++
helpviewer_keywords:
- _wctime32_s function
- ctime64_s function
- _tctime64_s function
- _wctime_s function
- tctime_s function
- _wctime64_s function
- ctime_s function
- ctime32_s function
- _ctime64_s function
- tctime64_s function
- wctime64_s function
- wctime_s function
- _tctime_s function
- tctime32_s function
- wctime32_s function
- time, converting
- _ctime32_s function
- _tctime32_s function
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 998046c0d59d12cd14d9091d9054312c5d1d48a2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ctimes-ctime32s-ctime64s-wctimes-wctime32s-wctime64s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s
Převést na řetězec hodnotu času a upravit nastavení místního časového pásma. Toto jsou verze [ctime _ctime64 –, _wctime –, _wctime64 –](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t ctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _ctime32_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _ctime64_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time64_t *time )  
;  
errno_t _wctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _wctime32_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _wctime64_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time64_t *time   
);  
template <size_t size>  
errno_t _ctime32_s(   
   char (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _ctime64_s(   
   char (&buffer)[size],  
   const __time64_t *time  
); // C++ only  
template <size_t size>  
errno_t _wctime32_s(   
   wchar_t (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _wctime64_s(   
   wchar_t (&buffer)[size],  
   const __time64_t *time   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `buffer`  
 Musí být dostatečně velký pro uložení 26 znaků. Ukazatel na výsledném řetězci znaků, nebo `NULL` pokud:  
  
-   `time` představuje datum před půlnoc, 1. ledna 1970 UTC.  
  
-   Pokud používáte `_ctime32_s` nebo `_wctime32_s` a `time` představuje datum po 23:59:59 18 leden 2038 UTC.  
  
-   Pokud používáte `_ctime64_s` nebo `_wctime64_s` a `time` představuje datum po 23:59:59, 31. prosince 3000, UTC.  
  
-   Pokud používáte `_ctime_s` nebo `_wctime_s`, tyto funkce jsou obálky na předchozí funkce. Najdete v části poznámky.  
  
 [in] `numberOfElements`  
 Velikost vyrovnávací paměti.  
  
 [in] `time`  
 Ukazatel na uložené čas.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu. Pokud dojde k chybě z důvodu neplatný parametr, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, je vrácena kód chyby. Kódy chyb jsou definovány v kód chyby. H; seznam těchto chybách naleznete v tématu [errno](../../c-runtime-library/errno-constants.md). V následující tabulce jsou uvedeny skutečné chybové kódy, vyvolána všechny chybové stavy.  
  
## <a name="error-conditions"></a>Chybové stavy  
  
|`buffer`|`numberOfElements`|`time`|Vrátí|Hodnota v `buffer`|  
|--------------|------------------------|------------|------------|-----------------------|  
|`NULL`|všechny|všechny|`EINVAL`|nedojde ke změně|  
|Není `NULL` (odkazuje na platný paměti)|0|všechny|`EINVAL`|nedojde ke změně|  
|není `NULL`|0 < velikost < 26|všechny|`EINVAL`|prázdný řetězec.|  
|není `NULL`|>= 26|NULL|`EINVAL`|prázdný řetězec.|  
|není `NULL`|>= 26|< 0|`EINVAL`|prázdný řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 `ctime_s` Funkce převede hodnotu čas, který je uložený jako [time_t](../../c-runtime-library/standard-types.md) struktura na řetězec znaků. `time` Hodnota se obvykle získávají z volání [čas](../../c-runtime-library/reference/time-time32-time64.md), která vrátí počet sekund uběhlých od půlnoci (00: 00:00), 1. ledna 1970, koordinovaný světový čas (UTC). Návratová hodnota řetězec obsahuje přesně 26 znaků a má tvar:  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 24 hodin se používá. Všechna pole mít konstantní šířky. Znak nového řádku (\n) a znak hodnoty null (\0) zabírají posledních dvou pozic řetězce.  
  
 Řetězec převedený znaků se také upraví podle nastavení zóny Místní čas. Najdete v článku `time`, [_ftime –](../../c-runtime-library/reference/ftime-ftime32-ftime64.md), a [localtime32_s –](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) funkce informace o konfiguraci místní čas a [_tzset –](../../c-runtime-library/reference/tzset.md) funkce informace o definování časové pásmo prostředí a globální proměnné.  
  
 `_wctime32_s` a `_wctime64_s` jsou verze široká charakterová `_ctime32_s` a `_ctime64_s`; ukazatel vrácením široká charakterová řetězec. V opačném `_ctime64_s`, `_wctime32_s`, a `_wctime64_s` chovají stejně jako na `_ctime32_s`.  
  
 `ctime_s` Vložená funkce, jehož výsledkem je `_ctime64_s` a `time_t` je ekvivalentní `__time64_t`. Pokud potřebujete vynutit kompilátoru interpretovat `time_t` jako starý 32bitovou verzi `time_t`, můžete definovat `_USE_32BIT_TIME_T`. Provedete to způsobí, že `ctime_s` k vyhodnocení `_ctime32_s`. Není doporučeno, protože vaše aplikace může selhat po 18. ledna 2038, a není povoleno na 64bitových platformách.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení lze odvodit délka vyrovnávací paměti automaticky, takže není nutné zadat argument velikost. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tctime_s`|`ctime_s`|`ctime_s`|`_wctime_s`|  
|`_tctime32_s`|`_ctime32_s`|`_ctime32_s`|`_wctime32_s`|  
|`_tctime64_s`|`_ctime64_s`|`_ctime64_s`|`_wctime64_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`ctime_s`, `_ctime32_s`, `_ctime64_s`|\<time.h>|  
|`_wctime_s`, `_wctime32_s`, `_wctime64_s`|\<Time.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_wctime_s.c  
/* This program gets the current  
 * time in time_t form and then uses _wctime_s to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
#define SIZE 26  
  
int main( void )  
{  
   time_t ltime;  
   wchar_t buf[SIZE];  
   errno_t err;  
  
   time( &ltime );  
  
   err = _wctime_s( buf, SIZE, &ltime );  
   if (err != 0)  
   {  
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);  
   }  
   wprintf_s( L"The time is %s\n", buf );  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
The time is Fri Apr 25 13:03:39 2003  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)