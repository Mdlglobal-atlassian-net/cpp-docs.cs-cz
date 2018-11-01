---
title: getenv_s, _wgetenv_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
ms.openlocfilehash: eac3c036e2f4f271c7bc2d77c8ae82bec28d3617
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546513"
---
# <a name="getenvs-wgetenvs"></a>getenv_s, _wgetenv_s

Získá hodnotu z aktuálního prostředí. Tyto verze [getenv _wgetenv](getenv-wgetenv.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Velikost vyrovnávací paměti, které je nutné, nebo 0, pokud není nalezena proměnné.

*Vyrovnávací paměti*<br/>
Vyrovnávací paměť pro ukládání hodnoty horní proměnné prostředí.

*numberOfElements*<br/>
Velikost *vyrovnávací paměti*.

*název_proměnné*<br/>
Název proměnné prostředí.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; v opačném případě chybu kódu při selhání.

### <a name="error-conditions"></a>Chybové podmínky

|*pReturnValue*|*Vyrovnávací paměti*|*numberOfElements*|*název_proměnné*|Návratová hodnota|
|--------------------|--------------|------------------------|---------------|------------------|
|**HODNOTU NULL**|Všechny|Všechny|Všechny|**EINVAL**|
|Všechny|**HODNOTU NULL**|>0|Všechny|**EINVAL**|
|Všechny|Všechny|Všechny|**HODNOTU NULL**|**EINVAL**|

Některé z těchto chybových stavů vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, funkce nastaví **errno** k **EINVAL** a vrátit **EINVAL**.

Také, pokud vyrovnávací paměť je příliš malá, vrátí tyto funkce **ERANGE**. Ne, vyvolat obslužnou rutinu neplatného parametru. Jejich zapsání velikost požadované vyrovnávací paměti v *pReturnValue*a tím programu povolit programy pro volání funkce s větší vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

**Getenv_s –** funkce prohledává seznam proměnných prostředí pro *název_proměnné*. **getenv_s –** není malá a velká písmena v operačním systému Windows. **getenv_s –** a [_putenv_s](putenv-s-wputenv-s.md) použijte kopii prostředí, které ukazuje globální proměnná **_environ** pro přístup k prostředí. **getenv_s –** funguje pouze na datové struktury, které jsou k dispozici ke knihovně runtime a ne na prostředí segmentu"", který je vytvořen pro proces operačním systémem. Proto programy, které používají *envp* argument [hlavní](../../cpp/main-program-startup.md) nebo [wmain](../../cpp/main-program-startup.md) může načíst neplatné informace.

**_wgetenv_s –** je verze širokého znaku **getenv_s –**; argument a návratová hodnota funkce **_wgetenv_s –** jsou širokoznaké řetězce. **_Wenviron** globální proměnná je verze širokého znaku **_environ**.

V aplikaci znakové sady MBCS (například v programu SBCS ASCII) **_wenviron** je zpočátku **NULL** protože prostředí se skládá z vícebajtové znakové řetězce. Pak v prvním volání [_wputenv](putenv-wputenv.md), nebo při prvním volání **_wgetenv_s –**, pokud prostředí (MBCS) již existuje, odpovídající prostředí řetězce širokého znaku se vytvoří a je následně odkázáno pomocí **_wenviron**.

Podobně jako v Unicode (**_wmain**) program, **_environ** je zpočátku **NULL** protože prostředí se skládá z řetězce širokého znaku. Pak v prvním volání [_putenv](putenv-wputenv.md), nebo při prvním volání **getenv_s –** Pokud prostředí (Unicode) již existuje, odpovídající prostředí MBCS je vytvořen a je následně odkázáno pomocí **_ Environ**.

Pokud dvě kopie prostředí (znaková sada MBCS a Unicode) existují současně v programu v jazyce, za běhu systému, musíte mít obě kopie a to způsobí, že času provádění. Například při volání **_putenv**, volání **_wputenv** je také spouštěny automaticky, takže odpovídají řetězce dvě prostředí.

> [!CAUTION]
> Ve výjimečných případech když Unicode verze a vícebajtová verze prostředí, za údržbu systému za běhu verze dvě prostředí nemusí odpovídat přesně. K tomu dochází proto, že i když jakýkoli jedinečný řetězec vícebajtového znaku zakončeného mapuje na jedinečné řetězec znaků Unicode, mapování z jedinečný řetězec znaků Unicode na řetězec vícebajtového znaku není nutně jedinečné. Další informace najdete v tématu [_environ _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv_s** a **_getenv_s** rodinách funkcí nejsou vláknově bezpečné. **_getenv_s** může vrátit ukazatel řetězce při **_putenv_s** upravuje řetězec a tím způsobí náhodná selhání. Ujistěte se, že volání těchto funkcí jsou synchronizována.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit velikost vyrovnávací paměti automaticky a tím eliminují potřebu zadat argument velikosti. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s –**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

Zkontrolujte nebo změňte hodnotu **TZ** proměnné, použijte prostředí **getenv_s –**, **_putenv**, a **_tzset –**, podle potřeby. Další informace o **TZ**, naleznete v tématu [_tzset –](tzset.md) a [_daylight, _dstbias, _timezone a _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**getenv_s**|\<stdlib.h>|
|**_wgetenv_s**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[Konstanty prostředí](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
