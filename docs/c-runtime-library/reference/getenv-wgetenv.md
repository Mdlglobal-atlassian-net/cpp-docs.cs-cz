---
title: getenv, _wgetenv
ms.date: 11/04/2016
apiname:
- getenv
- _wgetenv
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
- _wgetenv
- getenv
- _tgetenv
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
ms.openlocfilehash: 79c685fef8d6a4b966c53bb7d94b423d16971976
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568155"
---
# <a name="getenv-wgetenv"></a>getenv, _wgetenv

Získá hodnotu z aktuálního prostředí. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [getenv_s – _wgetenv_s –](getenv-s-wgetenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *getenv(
   const char *varname
);
wchar_t *_wgetenv(
   const wchar_t *varname
);
```

### <a name="parameters"></a>Parametry

*název_proměnné*<br/>
Název proměnné prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na vstupní tabulku prostředí obsahující *název_proměnné*. Není bezpečné ke změně hodnoty proměnné prostředí pomocí vrácenému ukazateli. Použití [_putenv](putenv-wputenv.md) funkce ke změně hodnoty proměnné prostředí. Vrácená hodnota je **NULL** Pokud *název_proměnné* nebyl nalezen v tabulce prostředí.

## <a name="remarks"></a>Poznámky

**Getenv** funkce prohledává seznam proměnných prostředí pro *název_proměnné*. **GETENV** není malá a velká písmena v operačním systému Windows. **GETENV** a **_putenv** použijte kopii prostředí, na které odkazuje globální proměnnou **_environ** pro přístup k prostředí. **GETENV** funguje pouze na datových strukturách dostupných knihovně runtime a ne na prostředí "segmentu" vytvořili pro proces operačním systémem. Proto programy, které používají *envp* argument [hlavní](../../cpp/main-program-startup.md) nebo [wmain](../../cpp/main-program-startup.md) může načíst neplatné informace.

Pokud *název_proměnné* je **NULL**, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí **NULL**.

**_wgetenv** je verze širokého znaku **getenv**; argument a návratová hodnota funkce **_wgetenv** jsou širokoznaké řetězce. **_Wenviron** globální proměnná je verze širokého znaku **_environ**.

V aplikaci znakové sady MBCS (například v programu SBCS ASCII) **_wenviron** je zpočátku **NULL** protože prostředí se skládá z vícebajtové znakové řetězce. Pak v prvním volání [_wputenv](putenv-wputenv.md), nebo při prvním volání **_wgetenv** Pokud prostředí (MBCS) již existuje, odpovídající prostředí řetězce širokého znaku se vytvoří a je následně odkázáno pomocí **_wenviron**.

Podobně jako v Unicode (**_wmain**) program, **_environ** je zpočátku **NULL** protože prostředí se skládá z řetězce širokého znaku. Pak v prvním volání **_putenv**, nebo při prvním volání **getenv** Pokud prostředí (Unicode) již existuje, odpovídající prostředí MBCS je vytvořen a je následně odkázáno pomocí **_ Environ**.

Pokud dvě kopie prostředí (znaková sada MBCS a Unicode) existují současně v programu v jazyce, za běhu systému, musíte mít obě kopie, což vede k času provádění. Například pokaždé, když voláte **_putenv**, volání **_wputenv** také provádí automaticky, takže odpovídají řetězce dvě prostředí.

> [!CAUTION]
> Ve výjimečných případech při údržbě systému za běhu Unicode verze a vícebajtová verze prostředí, tyto dvě prostředí verze nemusí odpovídat přesně. Důvodem je, že i když jakýkoli jedinečný řetězec vícebajtového znaku zakončeného mapuje na jedinečné řetězec znaků Unicode, mapování z jedinečný řetězec znaků Unicode na řetězec vícebajtového znaku není nutně jedinečné. Další informace najdete v tématu [_environ _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv** a **_getenv** rodinách funkcí nejsou vláknově bezpečné. **_getenv** může vrátit ukazatel řetězce při **_putenv** upravuje řetězec, což způsobí náhodná selhání. Ujistěte se, že volání těchto funkcí jsou synchronizována.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv –**|**GETENV**|**GETENV**|**_wgetenv**|

Zkontrolujte nebo změňte hodnotu **TZ** proměnné, použijte prostředí **getenv**, **_putenv** a **_tzset –** podle potřeby. Další informace o **TZ**, naleznete v tématu [_tzset –](tzset.md) a [_daylight, časové pásmo a _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**GETENV**|\<stdlib.h>|
|**_wgetenv**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_getenv.c
// compile with: /W3
// This program uses getenv to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *libvar;

   // Get the value of the LIB environment variable.
   libvar = getenv( "LIB" ); // C4996
   // Note: getenv is deprecated; consider using getenv_s instead

   if( libvar != NULL )
      printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects the environment
   // variable of the current process. The command processor's
   // environment is not changed.
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996
   // Note: _putenv is deprecated; consider using putenv_s instead

   // Get new value.
   libvar = getenv( "LIB" ); // C4996

   if( libvar != NULL )
      printf( "New LIB variable is: %s\n", libvar );
}
```

```Output
Original LIB variable is: C:\progra~1\devstu~1\vc\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[Konstanty prostředí](../../c-runtime-library/environmental-constants.md)<br/>
