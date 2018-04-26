---
title: GETENV –, _wgetenv – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
caps.latest.revision: 31
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f83ac7c044f019699556d69ddbf199cbfc02dc0
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="getenv-wgetenv"></a>getenv, _wgetenv

Získá hodnotu z aktuální prostředí. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [getenv_s –, _wgetenv_s –](getenv-s-wgetenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

Vrací ukazatel na položku tabulky prostředí obsahující *název_proměnné*. Není bezpečné změňte hodnotu proměnné prostředí pomocí Vrácený ukazatel. Použití [_putenv –](putenv-wputenv.md) funkce ke změně hodnoty proměnné prostředí. Vrácená hodnota je **NULL** Pokud *název_proměnné* nebyl nalezen v tabulce prostředí.

## <a name="remarks"></a>Poznámky

**GETENV –** funkce vyhledá seznamu proměnných prostředí pro *název_proměnné*. **GETENV –** není malá a velká písmena v operačním systému Windows. **GETENV –** a **_putenv –** použít kopii ukazující na globální proměnnou prostředí **_environ –** pro přístup k prostředí. **GETENV –** funguje pouze na datové struktury, které jsou přístupné pro běhové knihovny a ne na prostředí "segment", které jsou vytvořené pro proces operačního systému. Proto programy, které používají *envp –* argument [hlavní](../../cpp/main-program-startup.md) nebo [wmain](../../cpp/main-program-startup.md) může načíst neplatné informace.

Pokud *název_proměnné* je **NULL**, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **NULL**.

**_wgetenv –** je verze široká charakterová **GETENV –**; argument a vrátí hodnotu **_wgetenv –** jsou široká charakterová řetězce. **_Wenviron –** – globální proměnná je verze široká charakterová **_environ –**.

V aplikaci sady MBCS (například v aplikaci SBCS ASCII) **_wenviron –** je původně **NULL** protože prostředí se skládá z řetězců vícebajtových znaků. Poté, v prvním volání [_wputenv –](putenv-wputenv.md), nebo při prvním volání **_wgetenv –** Pokud prostředí (MBCS) již existuje, odpovídající široká charakterová řetězec prostředí se vytvoří a pak ukazuje **_wenviron –**.

Podobně jako v typu Unicode (**_wmain**) programu, **_environ –** je původně **NULL** protože prostředí se skládá z řetězce široká charakterová. Poté, v prvním volání **_putenv –**, nebo při prvním volání **GETENV –** Pokud prostředí (Unicode) již existuje, odpovídající MBCS prostředí se vytvoří a pak ukazuje **_ Environ –**.

Pokud dvě kopie prostředí (MBCS a Unicode) existují současně v programu, musíte udržovat běhu systému obě kopie, výsledkem je pomalejší dobu provádění. Například když zavoláte **_putenv –**, volání **_wputenv –** je také provést automaticky, takže odpovídají řetězce dvě prostředí.

> [!CAUTION]
> Ve výjimečných případech při běhu systému údržbu Unicode verze a vícebajtové verzi prostředí, tyto dvě prostředí verze nemusí odpovídat přesně. Je to proto, i když všechny jedinečné řetězce vícebajtových znaků se mapuje na jedinečné řetězce Unicode, mapování z jedinečné řetězce Unicode do řetězce vícebajtových znaků není nutně jedinečný. Další informace najdete v tématu [_environ –, _wenviron –](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv –** a **_getenv** řady funkcí nejsou bezpečné pro přístup z více vláken. **_getenv** může vrátit ukazatel řetězec při **_putenv –** upravuje řetězec, způsobuje náhodné chyby. Ujistěte se, že jsou synchronizovány volání na tyto funkce.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv –**|**GETENV –**|**GETENV –**|**_wgetenv**|

Zkontrolujte nebo změňte hodnotu **TZ** proměnné, použijte prostředí **GETENV –**, **_putenv –** a **_tzset –** podle potřeby. Další informace o **TZ**, najdete v části [_tzset –](tzset.md) a [_daylight, časové pásmo a _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**GETENV –**|\<stdlib.h>|
|**_wgetenv**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
