---
title: "getenv_s –, _wgetenv_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- getenv_s
- _wgetenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- getenv_s
- _tgetenv_s
- _wgetenv_s
dev_langs: C++
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
caps.latest.revision: "42"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d391e24a5b14bd015b43f88b2a687011d84d35fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="getenvs-wgetenvs"></a>getenv_s, _wgetenv_s
Získá hodnotu z aktuální prostředí. Tyto verze nástroje [getenv _wgetenv –](../../c-runtime-library/reference/getenv-wgetenv.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t getenv_s(   
   size_t *pReturnValue,  
   char* buffer,  
   size_t numberOfElements,  
   const char *varname   
);  
errno_t _wgetenv_s(   
   size_t *pReturnValue,  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *varname   
);  
template <size_t size>  
errno_t getenv_s(   
   size_t *pReturnValue,  
   char (&buffer)[size],  
   const char *varname   
); // C++ only  
template <size_t size>  
errno_t _wgetenv_s(   
   size_t *pReturnValue,  
   wchar_t (&buffer)[size],  
   const wchar_t *varname   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `pReturnValue`  
 Velikost vyrovnávací paměti, které je nutné, nebo 0, pokud není nalezena proměnná.  
  
 `buffer`  
 Vyrovnávací paměť k uložení hodnoty proměnné prostředí.  
  
 `numberOfElements`  
 Velikost `buffer`.  
  
 `varname`  
 Název proměnné prostředí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěšného; k chybě, jinak hodnota kódu při selhání.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`pReturnValue`|`buffer`|`numberOfElements`|`varname`|Návratová hodnota|  
|--------------------|--------------|------------------------|---------------|------------------|  
|`NULL`|všechny|všechny|všechny|`EINVAL`|  
|všechny|`NULL`|>0|všechny|`EINVAL`|  
|všechny|všechny|všechny|`NULL`|`EINVAL`|  
  
 Některé z těchto podmínek chyba vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, nastavte funkce `errno` k `EINVAL` a vrátí `EINVAL`.  
  
 Navíc pokud vyrovnávací paměť je příliš malá, vrátí tyto funkce `ERANGE`. Nevolejte obslužnou rutinu neplatný parametr. Se zapsat požadované vyrovnávací paměť v `pReturnValue`a tím povolit programy pro volání funkce s větší vyrovnávací paměť.  
  
## <a name="remarks"></a>Poznámky  
 `getenv_s` Funkce vyhledá seznamu proměnných prostředí pro `varname`. `getenv_s`není malá a velká písmena v operačním systému Windows. `getenv_s`a `_putenv_s` použít kopii prostředí, ve kterém je odkazoval na globální proměnnou `_environ` pro přístup k prostředí. `getenv_s`funguje pouze na datové struktury, které jsou k dispozici běhové knihovny a ne na prostředí "segment", který se vytvoří pro proces v operačním systému. Proto programy, které používají `envp` argument [hlavní](../../cpp/main-program-startup.md) nebo [wmain](../../cpp/main-program-startup.md) může načíst neplatné informace.  
  
 `_wgetenv_s`široká charakterová verze `getenv_s`; argument a vrátí hodnotu `_wgetenv_s` jsou široká charakterová řetězce. `_wenviron` – Globální proměnná je verze široká charakterová `_environ`.  
  
 V aplikaci sady MBCS (například v aplikaci SBCS ASCII) `_wenviron` je původně `NULL` protože prostředí se skládá z řetězců vícebajtových znaků. Poté, v prvním volání `_wputenv`, nebo při prvním volání `_wgetenv_s`, pokud prostředí (MBCS) již existuje, odpovídající široká charakterová řetězec prostředí se vytvoří a pak ukazuje `_wenviron`.  
  
 Podobně jako v typu Unicode `(_wmain`) programu, `_environ` je původně `NULL` protože prostředí se skládá z řetězce široká charakterová. Poté, v prvním volání `_putenv`, nebo při prvním volání `getenv_s` Pokud prostředí (Unicode) již existuje, odpovídající MBCS prostředí se vytvoří a pak ukazuje `_environ`.  
  
 Pokud dvě kopie prostředí (MBCS a Unicode) existují současně v programu, běhu systému musí zachovat obě kopie, a to způsobí, že pomalejší. čas provedení. Například při volání `_putenv`, volání `_wputenv` je také provést automaticky tak, aby odpovídají řetězce dvě prostředí.  
  
> [!CAUTION]
>  Ve výjimečných případech při běhu systému údržbu Unicode verze a vícebajtové verzi prostředí, prostředí dvě verze nemusí odpovídat přesně. K tomu dojde, protože i když všechny jedinečné řetězce vícebajtových znaků se mapuje na jedinečné řetězce Unicode, mapování z jedinečné řetězce Unicode do řetězce vícebajtových znaků není nutně jedinečný. Další informace najdete v tématu [_environ –, _wenviron –](../../c-runtime-library/environ-wenviron.md).  
  
> [!NOTE]
>  `_putenv_s` a `_getenv_s` řady funkcí nejsou bezpečné pro přístup z více vláken. `_getenv_s`může vrátit ukazatel řetězec při `_putenv_s` upravuje řetězec a tím způsobit náhodné chyby. Ujistěte se, že jsou synchronizovány volání na tyto funkce.  
  
 V jazyce C++ těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení můžete automaticky odvození délka vyrovnávací paměti a tím eliminovat potřeba zadat argument velikost. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tgetenv_s`|`getenv_s`|`getenv_s`|`_wgetenv_s`|  
  
 Zkontrolujte nebo změňte hodnotu `TZ` proměnné, použijte prostředí `getenv_s`, `_putenv`, a `_tzset`, podle potřeby. Další informace o `TZ`, najdete v části [_tzset –](../../c-runtime-library/reference/tzset.md) a [_daylight, _dstbias, _timezone a _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`getenv_s`|\<stdlib.h >|  
|`_wgetenv_s`|\<stdlib.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_getenv_s.c  
// This program uses getenv_s to retrieve  
// the LIB environment variable and then uses  
// _putenv to change it to a new value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char* libvar;  
   size_t requiredSize;  
  
   getenv_s( &requiredSize, NULL, 0, "LIB");  
   if (requiredSize == 0)  
   {  
      printf("LIB doesn't exist!\n");  
      exit(1);  
   }  
  
   libvar = (char*) malloc(requiredSize * sizeof(char));  
   if (!libvar)  
   {  
      printf("Failed to allocate memory!\n");  
      exit(1);  
   }  
  
   // Get the value of the LIB environment variable.  
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );  
  
   printf( "Original LIB variable is: %s\n", libvar );  
  
   // Attempt to change path. Note that this only affects  
   // the environment variable of the current process. The command  
   // processor's environment is not changed.  
   _putenv_s( "LIB", "c:\\mylib;c:\\yourlib" );  
  
   getenv_s( &requiredSize, NULL, 0, "LIB");  
  
   libvar = (char*) realloc(libvar, requiredSize * sizeof(char));  
   if (!libvar)  
   {  
      printf("Failed to allocate memory!\n");  
      exit(1);  
   }  
  
   // Get the new value of the LIB environment variable.   
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );  
  
   printf( "New LIB variable is: %s\n", libvar );  
  
   free(libvar);  
}  
```  
  
```Output  
Original LIB variable is: c:\vctools\lib;c:\vctools\atlmfc\lib;c:\vctools\PlatformSDK\lib;c:\vctools\Visual Studio SDKs\DIA Sdk\lib;c:\vctools\Visual Studio SDKs\BSC Sdk\lib  
New LIB variable is: c:\mylib;c:\yourlib  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [Konstanty prostředí](../../c-runtime-library/environmental-constants.md)   
 [_putenv –, _wputenv –](../../c-runtime-library/reference/putenv-wputenv.md)   
 [_dupenv_s –, _wdupenv_s –](../../c-runtime-library/reference/dupenv-s-wdupenv-s.md)