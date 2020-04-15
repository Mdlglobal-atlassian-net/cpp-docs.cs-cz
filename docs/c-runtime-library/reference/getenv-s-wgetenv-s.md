---
title: getenv_s, _wgetenv_s
description: Popisuje knihovnu getenv_s a _wgetenv_s funkce za běhu microsoft c.
ms.date: 4/2/2020
api_name:
- getenv_s
- _wgetenv_s
- _o__wgetenv_s
- _o_getenv_s
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
no-loc:
- getenv_s
- _wgetenv_s
- _putenv_s
- main
- wmain
- errno
- EINVAL
- ERANGE
- _environ
- _wenviron
- _putenv
- _wputenv
- _tgetenv_s
- _tzset
- _dupenv_s
- _wdupenv_s
ms.openlocfilehash: 17c4e001f7f4637f6f66f218c94378368976901f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344278"
---
# <a name="getenv_s-_wgetenv_s"></a>getenv_s, _wgetenv_s

Získá hodnotu z aktuálního prostředí. Tyto verze [getenv, _wgetenv](getenv-wgetenv.md) mají vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Velikost vyrovnávací paměti, která je požadována, nebo 0, pokud proměnná nebyla nalezena.

*Vyrovnávací paměti*<br/>
Vyrovnávací paměť pro uložení hodnoty proměnné prostředí.

*numberOfElements*<br/>
Velikost *vyrovnávací paměti*.

*název var*<br/>
Název proměnné prostředí.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; v opačném případě kód chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*pReturnValue*|*Vyrovnávací paměti*|*numberOfElements*|*název var*|Návratová hodnota|
|--------------------|--------------|------------------------|---------------|------------------|
|**Null**|jakékoli|jakékoli|jakékoli|**EINVAL**|
|jakékoli|**Null**|> 0|jakékoli|**EINVAL**|
|jakékoli|jakékoli|jakékoli|**Null**|**EINVAL**|

Některý z těchto chybových stavů vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce nastavit **errno** na **EINVAL** a vrátit **EINVAL**.

Také pokud vyrovnávací paměť je příliš malý, tyto funkce vrátí **ERANGE**. Nevyvolávají neplatnou obslužnou rutinu parametru. Zapíší požadovanou velikost vyrovnávací paměti v *pReturnValue*a tím umožní programům znovu volat funkci s větší vyrovnávací pamětí.

## <a name="remarks"></a>Poznámky

Funkce **getenv_s** prohledá seznam proměnných prostředí pro *název varname*. **getenv_s** v operačním systému Windows nerozlišují malá a velká písmena. **getenv_s** a [_putenv_s](putenv-s-wputenv-s.md) používat kopii prostředí, na které se ukazuje globální proměnná **_environ** pro přístup k prostředí. **getenv_s** pracuje pouze na datové struktury, které jsou přístupné pro knihovnu run-time a nikoli na "segment" prostředí, který je vytvořen pro proces operačním systémem. Proto programy, které používají *envp* argument [main](../../cpp/main-function-command-line-args.md) nebo [wmain](../../cpp/main-function-command-line-args.md) může načíst neplatné informace.

**_wgetenv_s** je širokoznaková verze **getenv_s**; argument a vrácená hodnota **_wgetenv_s** jsou řetězce širokých znaků. Globální proměnná **_wenviron** je verze **_environ**s širokými znaky .

V programu MBCS (například v programu SBCS ASCII) je **_wenviron** zpočátku **null,** protože prostředí se skládá z vícebajtových řetězců znaků. Potom při prvním volání [_wputenv](putenv-wputenv.md)nebo při prvním volání **_wgetenv_s**, pokud prostředí (MBCS) již existuje, je vytvořeno odpovídající prostředí řetězce s širokými znaky a je pak odkazováno **_wenviron**.

Podobně v programu Unicode (**_wmain)** **je _environ** zpočátku **null,** protože prostředí se skládá z řetězců se širokými znaky. Potom při prvním volání [_putenv](putenv-wputenv.md)nebo při prvním volání **getenv_s** pokud prostředí (Unicode) již existuje, je vytvořeno odpovídající prostředí MBCS a poté je odkazováno **_environ**.

Pokud existují dvě kopie prostředí (MBCS a Unicode) současně v programu, musí systém za běhu udržovat obě kopie, což způsobuje pomalejší dobu provádění. Například při volání **_putenv**, volání **_wputenv** je také automaticky spuštěntak, aby dva řetězce prostředí odpovídají.

> [!CAUTION]
> Ve výjimečných případech, kdy systém run-time udržuje verzi Unicode i vícebajtovou verzi prostředí, nemusí dvě verze prostředí přesně odpovídat. K tomu dochází, protože i když každý jedinečný řetězec vícebajtových znaků mapuje na jedinečný řetězec Unicode, mapování z jedinečného řetězce Unicode na vícebajtový řetězec není nutně jedinečné. Další informace naleznete [v tématu _environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **Rodiny funkcí _putenv_s** a **_getenv_s** nejsou bezpečné pro přístup z více vláken. **_getenv_s** může vrátit ukazatel řetězce, zatímco **_putenv_s** upravuje řetězec a tím způsobit náhodné chyby. Ujistěte se, že volání těchto funkcí jsou synchronizovány.

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky a tím eliminovat potřebu zadat argument velikosti. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

Chcete-li zkontrolovat nebo změnit hodnotu proměnné prostředí **TZ,** použijte podle potřeby **getenv_s**, **_putenv**a **_tzset**. Další informace o **TZ**naleznete [v tématu _tzset](tzset.md) a [_daylight, _dstbias, _timezone a _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**getenv_s**|\<stdlib.h>|
|**_wgetenv_s**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[Environmentální konstanty](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
