---
title: getenv, _wgetenv
ms.date: 11/04/2016
api_name:
- getenv
- _wgetenv
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
ms.openlocfilehash: 7cacd8588bcc74c6d064da370ce6254aada56c12
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955062"
---
# <a name="getenv-_wgetenv"></a>getenv, _wgetenv

Získá hodnotu z aktuálního prostředí. K dispozici jsou bezpečnější verze těchto funkcí; viz [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Název proměnné prostředí

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na položku tabulky prostředí obsahující *název_proměnné*. Není bezpečné upravovat hodnotu proměnné prostředí pomocí vráceného ukazatele. Pomocí funkce [_putenv](putenv-wputenv.md) můžete změnit hodnotu proměnné prostředí. Návratová hodnota má **hodnotu null** , pokud se v tabulce prostředí nenalezne *název_proměnné* .

## <a name="remarks"></a>Poznámky

Funkce **getenv** vyhledá v seznamu proměnných prostředí pro *název_proměnné*. **getenv** nerozlišuje velká a malá písmena v operačním systému Windows. **getenv** a **_putenv** používají kopii prostředí, na které odkazuje globální proměnná **_environ** pro přístup k prostředí. **getenv** funguje pouze v datových strukturách dostupných pro běhovou knihovnu, nikoli v prostředí segmentu vytvořeném pro proces operačním systémem. Proto programy, které používají argument *envp* pro [Main](../../cpp/main-program-startup.md) nebo [wmain](../../cpp/main-program-startup.md) , mohou načíst neplatné informace.

Pokud hodnota *název_proměnné* je **null**, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **hodnotu null**.

**_wgetenv** je **getenv**verze s velkým znakem; argument a návratová hodnota **_wgetenv** jsou řetězce s velkým počtem znaků. Globální proměnná **_wenviron** je verze **_environ**s velkým znakem.

V programu znakové sady MBCS (například v programu SBCS ASCII) je **_wenviron** zpočátku **null** , protože prostředí se skládá z řetězců vícebajtových znaků. Poté při prvním volání [_wputenv](putenv-wputenv.md)nebo při prvním volání **_wgetenv** , pokud již existuje prostředí (MBCS), je vytvořeno odpovídající prostředí řetězců s velkým znakem znaků a následně na něj odkazuje **_wenviron**.

Podobně v programu Unicode ( **_wmain**) je **_environ** zpočátku **null** , protože prostředí se skládá z řetězců s velkým počtem znaků. Pak při prvním volání **_putenv**nebo při prvním volání **getenv** Pokud již existuje prostředí (Unicode), vytvoří se odpovídající prostředí znakové sady MBCS a následně na něj odkazuje **_environ**.

V případě, že dvě kopie prostředí (MBCS a Unicode) existují současně v programu, musí operační systém uchovávat obě kopie, což má za následek pomalejší dobu provádění. Například pokaždé, když voláte **_putenv**, volání **_wputenv** je také provedeno automaticky, aby oba řetězce prostředí odpovídaly.

> [!CAUTION]
> Ve výjimečných případech platí, že když systém za běhu udržuje jak verzi Unicode, tak vícebajtovou verzi prostředí, tyto dvě verze prostředí nemusí přesně odpovídat. Důvodem je, že i když jakýkoliv jedinečný řetězec vícebajtových znaků mapuje na jedinečný řetězec v kódování Unicode, mapování z jedinečného řetězce Unicode na řetězec vícebajtových znaků není nutně jedinečné. Další informace najdete v tématu [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Řady funkcí **_putenv** a **_getenv** nejsou bezpečné pro přístup z více vláken. **_getenv** může vracet ukazatel na řetězec, zatímco **_putenv** upravuje řetězec a způsobuje náhodných selhání. Ujistěte se, že jsou volání těchto funkcí synchronizovaná.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

Chcete-li ověřit nebo změnit hodnotu proměnné prostředí **TZ** , použijte **getenv**, **_putenv** a **_tzset** podle potřeby. Další informace o **TZ**najdete v tématech [_tzset](tzset.md) a [_daylight, TimeZone a _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**getenv**|\<stdlib.h>|
|**_wgetenv**|\<Stdlib. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
