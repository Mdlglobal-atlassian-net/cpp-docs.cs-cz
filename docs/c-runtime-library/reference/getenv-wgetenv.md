---
title: getenv, _wgetenv
description: Popisuje knihovnu getenv a _wgetenv funkce za běhu microsoft c.
ms.date: 4/2/2020
api_name:
- getenv
- _wgetenv
- _o__wgetenv
- _o_getenv
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
no-loc:
- getenv
- _wgetenv
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
ms.openlocfilehash: c9d7f7e1a2c5d6b15aee2f7f972a30cc0c90115c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344256"
---
# <a name="getenv-_wgetenv"></a>getenv, _wgetenv

Získá hodnotu z aktuálního prostředí. K dispozici jsou bezpečnější verze těchto funkcí. viz [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*název var*<br/>
Název proměnné prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na položku tabulky prostředí obsahující *název varname*. Není bezpečné změnit hodnotu proměnné prostředí pomocí vráceného ukazatele. Pomocí [funkce _putenv](putenv-wputenv.md) můžete upravit hodnotu proměnné prostředí. Vrácená hodnota je **NULL,** pokud *název varnebyl* nalezen v tabulce prostředí.

## <a name="remarks"></a>Poznámky

Funkce **getenv** prohledá seznam proměnných prostředí pro *název varname*. **getenv** není malá a velká písmena v operačním systému Windows. **getenv** a **_putenv** používat kopii prostředí, na kterou poukazuje globální proměnná **_environ** pro přístup k životnímu prostředí. **getenv** pracuje pouze na datových strukturách přístupných pro run-time knihovnu a ne na "segmentu" prostředí vytvořeném pro proces operačním systémem. Proto programy, které používají *envp* argument [main](../../cpp/main-function-command-line-args.md) nebo [wmain](../../cpp/main-function-command-line-args.md) může načíst neplatné informace.

Pokud je *název varname* **NULL**, tato funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **hodnotu NULL**.

**_wgetenv** je širokoznaková verze **getenv**; argument a vrácená hodnota **_wgetenv** jsou řetězce širokých znaků. Globální proměnná **_wenviron** je verze **_environ**s širokými znaky .

V programu MBCS (například v programu SBCS ASCII) je **_wenviron** zpočátku **null,** protože prostředí se skládá z vícebajtových řetězců znaků. Potom při prvním volání [_wputenv](putenv-wputenv.md)nebo při prvním volání **_wgetenv** pokud prostředí (MBCS) již existuje, je vytvořeno odpovídající prostředí řetězce s širokými znaky a poté je odkazováno **_wenviron**.

Podobně v programu Unicode (**_wmain)** **je _environ** zpočátku **null,** protože prostředí se skládá z řetězců se širokými znaky. Potom při prvním volání **_putenv**nebo při prvním volání **getenv,** pokud (Unicode) prostředí již existuje, je vytvořen odpovídající prostředí MBCS a je pak odkazováno **_environ**.

Pokud v programu existují současně dvě kopie prostředí (MBCS a Unicode), musí systém za běhu udržovat obě kopie, což má za následek pomalejší dobu provádění. Například při každém volání **_putenv**je volání **_wputenv** také provedeno automaticky, takže dva řetězce prostředí odpovídají.

> [!CAUTION]
> Ve výjimečných případech, kdy systém run-time udržuje verzi Unicode i vícebajtovou verzi prostředí, nemusí tyto dvě verze prostředí přesně odpovídat. Je to proto, že i když každý jedinečný vícebajtový řetězec se mapuje na jedinečný řetězec Unicode, mapování z jedinečného řetězce Unicode na vícebajtový řetězec není nutně jedinečné. Další informace naleznete [v tématu _environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **Rodiny funkcí _putenv** a **_getenv** nejsou bezpečné pro přístup z více vláken. **_getenv** může vrátit ukazatel řetězce, zatímco **_putenv** upravuje řetězec, což způsobuje náhodné selhání. Ujistěte se, že volání těchto funkcí jsou synchronizovány.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

Chcete-li zkontrolovat nebo změnit hodnotu proměnné prostředí **TZ,** použijte **getenv**, **_putenv** a **_tzset** podle potřeby. Další informace o **TZ**naleznete [v tématu _tzset](tzset.md) a [_daylight, časové pásmo a _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**getenv**|\<stdlib.h>|
|**_wgetenv**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[Konstanty prostředí](../../c-runtime-library/environmental-constants.md)<br/>
