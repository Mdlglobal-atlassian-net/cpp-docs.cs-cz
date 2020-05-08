---
title: getenv_s, _wgetenv_s
description: Popisuje knihovnu getenv_s a _wgetenv_s funkce modulu runtime jazyka Microsoft C.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 0713ed5735916c31edaab1a178a5e9b1b7cf5377
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913673"
---
# <a name="getenv_s-_wgetenv_s"></a>getenv_s, _wgetenv_s

Získá hodnotu z aktuálního prostředí. Tyto verze [getenv, _wgetenv](getenv-wgetenv.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Velikost vyrovnávací paměti, která je povinná, nebo 0, pokud proměnná nebyla nalezena.

*vyrovnávací paměti*<br/>
Vyrovnávací paměť pro uložení hodnoty proměnné prostředí

*numberOfElements*<br/>
Velikost *vyrovnávací paměti*.

*název_proměnné*<br/>
Název proměnné prostředí

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; v opačném případě chybový kód při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*pReturnValue*|*vyrovnávací paměti*|*numberOfElements*|*název_proměnné*|Návratová hodnota|
|--------------------|--------------|------------------------|---------------|------------------|
|**PLATNOST**|jakýmikoli|jakýmikoli|jakýmikoli|**EINVAL**|
|jakýmikoli|**PLATNOST**|> 0|jakýmikoli|**EINVAL**|
|jakýmikoli|jakýmikoli|jakýmikoli|**PLATNOST**|**EINVAL**|

Kterákoli z těchto chybových podmínek vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

Také pokud je vyrovnávací paměť příliš malá, vrátí tyto funkce **ERANGE**. Nevyvolávají neplatnou obslužnou rutinu parametru. Načítají požadovanou velikost vyrovnávací paměti v *pReturnValue*a umožní tak programům zavolat funkci znovu s větší vyrovnávací pamětí.

## <a name="remarks"></a>Poznámky

Funkce **getenv_s** vyhledá v seznamu proměnných prostředí pro *název_proměnné*. **getenv_s** nerozlišuje velká a malá písmena v operačním systému Windows. **getenv_s** a [_putenv_s](putenv-s-wputenv-s.md) použít kopii prostředí, na které ukazuje globální proměnná **_environ** pro přístup k prostředí. **getenv_s** funguje pouze v datových strukturách, které jsou přístupné pro běhovou knihovnu, nikoli v prostředí "segment", které je vytvořeno pro proces operačním systémem. Proto programy, které používají argument *envp* pro [Main](../../cpp/main-function-command-line-args.md) nebo [wmain](../../cpp/main-function-command-line-args.md) , mohou načíst neplatné informace.

**_wgetenv_s** je verze **getenv_s**s velkým znakem; argument a návratová hodnota **_wgetenv_s** jsou řetězce s velkým počtem znaků. **_Wenviron** globální proměnná je verze **_environ**s velkým znakem.

V programu znakové sady MBCS (například v programu SBCS ve STANDARDu SBCS) **_wenviron** má počáteční **hodnotu null** , protože prostředí se skládá z řetězců vícebajtových znaků. Pak při prvním volání [_wputenv](putenv-wputenv.md)nebo při prvním volání **_wgetenv_s**, pokud prostředí (MBCS) již existuje, je vytvořeno odpovídající prostředí řetězců s velkým znakem znaků a následně na něj odkazuje **_wenviron**.

Podobně v programu Unicode (**_wmain**) **_Environ** je zpočátku **null** , protože prostředí se skládá z řetězců s velkým počtem znaků. Pak při prvním volání [_putenv](putenv-wputenv.md)nebo při prvním volání **getenv_s** Pokud již existuje prostředí (Unicode), vytvoří se odpovídající prostředí znakové sady MBCS a následně na něj odkazuje **_environ**.

V případě, že dvě kopie prostředí (MBCS a Unicode) existují současně v programu, musí operační systém uchovávat obě kopie a to způsobí pomalejší dobu provádění. Například při volání **_putenv**, volání **_wputenv** je také provedeno automaticky, aby oba řetězce prostředí odpovídaly.

> [!CAUTION]
> Ve vzácných instancích platí, že když systém za běhu udržuje jak verzi Unicode, tak vícebajtovou verzi prostředí, tyto dvě verze prostředí nemusí přesně odpovídat. K tomu dochází, protože i když jakýkoliv jedinečný řetězec vícebajtových znaků mapuje na jedinečný řetězec Unicode, mapování z jedinečného řetězce Unicode na řetězec vícebajtových znaků není nutně jedinečné. Další informace najdete v tématu [_environ _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv_s** a **_getenv_s** rodin funkcí nejsou bezpečné pro přístup z více vláken. **_getenv_s** může vracet ukazatel na řetězec, zatímco **_putenv_s** upravuje řetězec, a proto způsobuje náhodné selhání. Ujistěte se, že jsou volání těchto funkcí synchronizovaná.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky, takže eliminují nutnost zadat argument Size. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

Chcete-li ověřit nebo změnit hodnotu proměnné prostředí **TZ** , použijte jako povinné **getenv_s**, **_putenv**a **_tzset**. Další informace o **TZ**najdete v tématu [_tzset](tzset.md) a [_daylight, _dstbias, _timezone a _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**getenv_s**|\<Stdlib. h>|
|**_wgetenv_s**|\<Stdlib. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
[Konstanty prostředí](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
