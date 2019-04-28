---
title: _searchenv_s, _wsearchenv_s
ms.date: 11/04/2016
apiname:
- _wsearchenv_s
- _searchenv_s
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
ms.openlocfilehash: 40c2d0c42a3d61f84db78015388eba19742af06e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356820"
---
# <a name="searchenvs-wsearchenvs"></a>_searchenv_s, _wsearchenv_s

Vyhledá soubor pomocí cest prostředí. Tyto verze [_searchenv, _wsearchenv](searchenv-wsearchenv.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Název souboru*<br/>
Název souboru pro hledání.

*varname*<br/>
Prostředí pro vyhledávání.

*pathname*<br/>
Vyrovnávací paměť pro ukládání úplné cesty.

*numberOfElements*<br/>
Velikost *cesta* vyrovnávací paměti.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; Kód chyby při selhání.

Pokud *filename* je prázdný řetězec, bude návratovou hodnotou **ENOENT**.

### <a name="error-conditions"></a>Chybové podmínky

|*Název souboru*|*varname*|*pathname*|*numberOfElements*|Návratová hodnota|Obsah *cesta*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|Všechny|Všechny|**NULL**|Všechny|**EINVAL**|není k dispozici|
|**NULL**|Všechny|Všechny|Všechny|**EINVAL**|nebyl změněn.|
|Všechny|Všechny|Všechny|<= 0|**EINVAL**|nebyl změněn.|

Pokud dojde k některé z těchto chybových stavů, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátit **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Searchenv_s –** rutinní vyhledá cílový soubor v zadané doméně. *Název_proměnné* proměnné může být jakýkoli prostředí nebo uživatelem definované proměnné, která určuje seznam cest adresáře, jako například **cesta**, **LIB**, a **zahrnutí** . Protože **_searchenv_s –** velká a malá písmena, *název_proměnné* by měl odpovídat proměnné prostředí. Pokud *název_proměnné* neodpovídá názvu proměnné prostředí definované v prostředí procesu, vrátí funkce hodnotu nula a *cesta* proměnná je beze změny.

Rutina nejprve hledá soubor v aktuálním pracovním adresáři. Pokud se nenajde soubor, hledá dále v adresářích určených proměnnou prostředí. Pokud cílový soubor v jednom z těchto adresářů, nově vytvořená cesta je zkopírována do *pathname*. Pokud *filename* soubor není nalezen, *cesta* obsahuje prázdný řetězec zakončený hodnotou null.

*Cesta* vyrovnávací paměti musí být nejméně **_MAX_PATH** znaků dlouhá, aby k vešel úplný název vytvořené cesty. V opačném případě **_searchenv_s –** může přetečení *cesta* vyrovnávací paměti, což vede k neočekávanému chování.

**_wsearchenv_s –** je verze širokého znaku **_searchenv_s –**; argumenty, které mají **_wsearchenv_s –** jsou širokoznaké řetězce. **_wsearchenv_s –** a **_searchenv_s –** se jinak chovají stejně.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
