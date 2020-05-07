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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 5dd21013c8910ba07e2d23606af49bc80458dbc6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918999"
---
# <a name="_searchenv_s-_wsearchenv_s"></a>_searchenv_s, _wsearchenv_s

Vyhledá soubor pomocí cest prostředí. Tyto verze [_searchenv mají _wsearchenv](searchenv-wsearchenv.md) vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Bitmap*<br/>
Název souboru, který se má vyhledat

*název_proměnné*<br/>
Prostředí, které se má hledat

*název*<br/>
Uložte úplnou cestu do vyrovnávací paměti.

*numberOfElements*<br/>
Velikost vyrovnávací paměti pro *cestu* .

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; chybový kód při selhání.

Pokud *filename* je prázdný řetězec, návratová hodnota je **ENOENT**.

### <a name="error-conditions"></a>Chybové stavy

|*Bitmap*|*název_proměnné*|*název*|*numberOfElements*|Návratová hodnota|Obsah *cesty*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|jakýmikoli|jakýmikoli|**PLATNOST**|jakýmikoli|**EINVAL**|neuvedeno|
|**PLATNOST**|jakýmikoli|jakýmikoli|jakýmikoli|**EINVAL**|nezměněno|
|jakýmikoli|jakýmikoli|jakýmikoli|<= 0|**EINVAL**|nezměněno|

Pokud dojde k některé z těchto chybových podmínek, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Rutina **_searchenv_s** vyhledává cílový soubor v zadané doméně. Proměnná *název_proměnné* může být libovolné prostředí nebo uživatelsky definovaná proměnná, která určuje seznam cest adresářů, jako je například **path**, **lib**a **include**. Vzhledem k tomu, že **_searchenv_s** rozlišuje velká a malá písmena, by měl pole *název_proměnné* odpovídat velikosti proměnné prostředí. Pokud hodnota *název_proměnné* neodpovídá názvu proměnné prostředí definované v prostředí procesu, vrátí funkce hodnotu nula a proměnná *cesty* zůstane beze změny.

Rutina nejprve vyhledá soubor v aktuálním pracovním adresáři. Pokud soubor nenajde, zobrazí se vedle adresářů určených proměnnou prostředí. Pokud je cílový soubor v jednom z těchto adresářů, nově vytvořená cesta je zkopírována do *cesty*. Pokud soubor *filename* není nalezen, *cesta* obsahuje prázdný řetězec zakončený hodnotou null.

Velikost vyrovnávací paměti pro *cestu* by měla být aspoň **_MAX_PATH** znaků dlouhá, aby se vešla úplná délka názvu konstruované cesty. V opačném případě **_searchenv_s** může přetečení vyrovnávací paměti *cesty* , což vede k neočekávanému chování.

**_wsearchenv_s** je verze **_searchenv_s**s velkým znakem; argumenty **_wsearchenv_s** jsou řetězce s libovolným znakem. **_wsearchenv_s** a **_searchenv_s** se chovají identicky jinak.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_searchenv_s**|\<Stdlib. h>|
|**_wsearchenv_s**|\<Stdlib. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Řízení adresáře](../../c-runtime-library/directory-control.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
