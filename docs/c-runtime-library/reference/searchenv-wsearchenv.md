---
title: _searchenv, _wsearchenv
ms.date: 11/04/2016
api_name:
- _searchenv
- _wsearchenv
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
ms.openlocfilehash: a3139ab87335ba581ef65707602c5da1819ce4a1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948772"
---
# <a name="_searchenv-_wsearchenv"></a>_searchenv, _wsearchenv

Vyhledá soubor pomocí cest prostředí. K dispozici jsou bezpečnější verze těchto funkcí; viz [_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Bitmap*<br/>
Název souboru, který se má vyhledat

*název_proměnné*<br/>
Prostředí, které se má hledat

*pathname*<br/>
Uložte úplnou cestu do vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

Rutina **_searchenv** vyhledává cílový soubor v zadané doméně. Proměnná *název_proměnné* může být libovolné prostředí nebo uživatelsky definovaná proměnná – například **path**, **lib**nebo **include**– které určují seznam cest k adresáři. Vzhledem k tomu, že **_searchenv** rozlišuje velká a malá písmena, by měl pole *název_proměnné* odpovídat velikosti proměnné prostředí.

Rutina nejprve vyhledá soubor v aktuálním pracovním adresáři. Pokud soubor nenajde, prohledá adresáře, které jsou určeny proměnnou prostředí. Pokud je cílový soubor v jednom z těchto adresářů, nově vytvořená cesta je zkopírována do *cesty*. Pokud soubor *filename* není nalezen, *cesta* obsahuje prázdný řetězec zakončený hodnotou null.

Velikost vyrovnávací paměti pro *cestu* by měla být aspoň **_MAX_PATH** znaků dlouhá, aby se vešla úplná délka názvu konstruované cesty. V opačném případě může **_searchenv** přetečení vyrovnávací paměti *cest* a způsobit neočekávané chování.

**_wsearchenv** je verze **_searchenv**s libovolným znakem a argumenty pro **_wsearchenv** jsou řetězce s velkým počtem znaků. **_wsearchenv** a **_searchenv** se chovají stejně jinak.

Pokud *filename* je prázdný řetězec, vrátí tyto funkce **ENOENT**.

Pokud *název souboru* nebo *cesta* je ukazatel s **hodnotou null** , je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

Další informace o **errno** a chybových kódech naleznete v tématu [konstanty errno](../../c-runtime-library/errno-constants.md).

V C++nástroji mají tyto funkce přetížení šablony, které vyvolávají novější a bezpečnější protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<Stdlib. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
