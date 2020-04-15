---
title: _searchenv, _wsearchenv
ms.date: 4/2/2020
api_name:
- _searchenv
- _wsearchenv
- _o__searchenv
- _o__wsearchenv
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
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
helpviewer_keywords:
- _wsearchenv function
- files [C++], finding
- _searchenv function
- tsearchenv function
- environment paths, searching for files
- _tsearchenv function
- wsearchenv function
- searchenv function
- environment paths
ms.assetid: 9c944a27-d326-409b-aee6-410e8762d9d3
ms.openlocfilehash: 22a8ca8fa7e56a84289d7e90ffb519073f006b5c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332381"
---
# <a name="_searchenv-_wsearchenv"></a>_searchenv, _wsearchenv

Používá cesty prostředí k vyhledání souboru. K dispozici jsou bezpečnější verze těchto funkcí. viz [_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
void _searchenv(
   const char *filename,
   const char *varname,
   char *pathname
);
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname
);
template <size_t size>
void _searchenv(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
void _wsearchenv(
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

## <a name="remarks"></a>Poznámky

Rutina **_searchenv** vyhledá cílový soubor v zadané doméně. Proměnná *varname* může být libovolná proměnná prostředí nebo uživatelem definovaná – například **PATH**, **LIB**nebo **INCLUDE**– která určuje seznam cest adresářů. Vzhledem k tomu, **že _searchenv** rozlišuje malá *a velká písmena, měl* by název var odpovídat velikosti písmen proměnné prostředí.

Rutina nejprve vyhledá soubor v aktuálním pracovním adresáři. Pokud soubor nenajde, prohledá adresáře určené proměnnou prostředí. Pokud je cílový soubor v jednom z těchto adresářů, nově vytvořená cesta se zkopíruje do *cesty*. Pokud soubor *názvu souboru* nebyl nalezen, *cesta* obsahuje prázdný řetězec s ukončeným hodnotou null.

Vyrovnávací paměť *cesty* by měla být alespoň **_MAX_PATH** znaky dlouhé, aby se přizpůsobily celé délce názvu postavené cesty. V opačném případě **_searchenv** může přetečit vyrovnávací paměť *cesty* a způsobit neočekávané chování.

**_wsearchenv** je verze **_searchenv**s širokými znaky a argumenty, které mají **_wsearchenv,** jsou řetězce s širokými znaky. **_wsearchenv** a **_searchenv** se chovají stejně jinak.

Pokud *název souboru* je prázdný řetězec, tyto funkce vrátí **ENOENT**.

Pokud je *název_souboru* nebo *cesta* **ukazatelem NULL,** je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce vrátí -1 a nastaví **errno** na **EINVAL**.

Další informace o **chybových** kódech a chybových kódech naleznete [v tématu errno Constants](../../c-runtime-library/errno-constants.md).

V jazyce C++ mají tyto funkce přetížení šablony, které vyvolávají novější, bezpečnější protějšky těchto funkcí. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_searchenv.c
// compile with: /W3
// This program searches for a file in
// a directory that's specified by an environment variable.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";

   // Search for file in PATH environment variable:
   _searchenv( searchfile, envvar, pathbuffer ); // C4996
   // Note: _searchenv is deprecated; consider using _searchenv_s
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 8\VC\BIN\CL.EXE
```

## <a name="see-also"></a>Viz také

[Řízení adresářů](../../c-runtime-library/directory-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
