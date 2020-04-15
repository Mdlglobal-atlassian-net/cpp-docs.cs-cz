---
title: _searchenv_s, _wsearchenv_s
ms.date: 4/2/2020
api_name:
- _wsearchenv_s
- _searchenv_s
- _o__searchenv_s
- _o__wsearchenv_s
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
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
helpviewer_keywords:
- tsearchenv_s function
- files [C++], finding
- buffers [C++], buffer overruns
- environment paths, searching for files
- wsearchenv_s function
- searchenv_s function
- _tsearchenv_s function
- buffer overruns
- buffers [C++], avoiding overruns
- _wsearchenv_s function
- _searchenv_s function
- environment paths
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
ms.openlocfilehash: 3d526c546e1496b3b13b14a12c9025cbd0347cd2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332404"
---
# <a name="_searchenv_s-_wsearchenv_s"></a>_searchenv_s, _wsearchenv_s

Hledá soubor pomocí cest prostředí. Tyto verze [_searchenv, _wsearchenv](searchenv-wsearchenv.md) mají vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char *pathname,
   size_t numberOfElements
);
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname,
   size_t numberOfElements
);
template <size_t size>
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t (&pathname)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*Název_souboru*<br/>
Název souboru, který chcete vyhledat.

*název var*<br/>
Prostředí k vyhledávání.

*Cesta*<br/>
Vyrovnávací paměť pro uložení úplné cesty.

*numberOfElements*<br/>
Velikost vyrovnávací paměti *cesty.*

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; kód chyby při selhání.

Pokud je *název souboru* prázdný řetězec, vrácená hodnota je **ENOENT**.

### <a name="error-conditions"></a>Chybové stavy

|*Název_souboru*|*název var*|*Cesta*|*numberOfElements*|Návratová hodnota|Obsah *cesty*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|jakékoli|jakékoli|**Null**|jakékoli|**EINVAL**|neuvedeno|
|**Null**|jakékoli|jakékoli|jakékoli|**EINVAL**|se nezměnilo|
|jakékoli|jakékoli|jakékoli|<= 0|**EINVAL**|se nezměnilo|

Pokud dojde k některé z těchto chybových stavů, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce nastavit **errno** na **EINVAL** a vrátit **EINVAL**.

## <a name="remarks"></a>Poznámky

Rutina **_searchenv_s** vyhledá cílový soubor v zadané doméně. Proměnná *varname* může být libovolné prostředí nebo uživatelem definovaná proměnná, která určuje seznam cest adresáře, například **PATH**, **LIB**a **INCLUDE**. Vzhledem k tomu, **že _searchenv_s** rozlišuje malá *a velká písmena, měl* by název var odpovídat velikosti písmen proměnné prostředí. Pokud *varname* neodpovídá názvu proměnné prostředí definované v prostředí procesu, funkce vrátí nulu a proměnná *cesty* se nezmění.

Rutina nejprve vyhledá soubor v aktuálním pracovním adresáři. Pokud soubor nenajde, zobrazí se dále prostřednictvím adresářů určených proměnnou prostředí. Pokud je cílový soubor v jednom z těchto adresářů, nově vytvořená cesta se zkopíruje do *cesty*. Pokud soubor *názvu souboru* nebyl nalezen, *cesta* obsahuje prázdný řetězec s ukončeným hodnotou null.

Vyrovnávací paměť *cesty* by měla být alespoň **_MAX_PATH** znaky dlouhé, aby se přizpůsobily celé délce názvu postavené cesty. V opačném případě **_searchenv_s** může přetečit vyrovnávací paměť *cesty,* což vede k neočekávanému chování.

**_wsearchenv_s** je širokoznaková verze **_searchenv_s**; argumenty, které mají **_wsearchenv_s,** jsou řetězce s širokými znaky. **_wsearchenv_s** a **_searchenv_s** se chovají stejně jinak.

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky (eliminuje potřebu zadat argument velikosti) a mohou automaticky nahradit starší, nezabezpečené funkce s jejich novější, bezpečné protějšky. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_searchenv_s.c
/* This program searches for a file in
* a directory specified by an environment variable.
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";
   errno_t err;

   /* Search for file in PATH environment variable: */
   err = _searchenv_s( searchfile, envvar, pathbuffer, _MAX_PATH );
   if (err != 0)
   {
      printf("Error searching the path. Error code: %d\n", err);
   }
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 2010\VC\BIN\CL.EXE
```

## <a name="see-also"></a>Viz také

[Řízení adresářů](../../c-runtime-library/directory-control.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
