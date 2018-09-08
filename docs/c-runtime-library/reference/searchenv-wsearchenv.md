---
title: _searchenv, _wsearchenv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _searchenv
- _wsearchenv
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
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afcd461446f98024e04e44e28facae4fba65b0aa
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100396"
---
# <a name="searchenv-wsearchenv"></a>_searchenv, _wsearchenv

Vyhledejte soubor pomocí cest prostředí. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [_searchenv_s – _wsearchenv_s –](searchenv-s-wsearchenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Název souboru*<br/>
Název souboru pro hledání.

*název_proměnné*<br/>
Prostředí pro vyhledávání.

*pathname*<br/>
Vyrovnávací paměť pro ukládání úplné cesty.

## <a name="remarks"></a>Poznámky

**_Searchenv** rutinní vyhledá cílový soubor v zadané doméně. *Název_proměnné* proměnná může být libovolného prostředí nebo uživatelem definované proměnné – například **cesta**, **LIB**, nebo **zahrnout**–, který určuje seznam cest adresáře. Protože **_searchenv** velká a malá písmena, *název_proměnné* by měl odpovídat proměnné prostředí.

Rutina nejprve hledá soubor v aktuálním pracovním adresáři. Pokud soubor nenajde, vyhledá prostřednictvím adresáře, které jsou určeny proměnnou prostředí. Pokud cílový soubor v jednom z těchto adresářů, nově vytvořená cesta je zkopírována do *pathname*. Pokud *filename* soubor není nalezen, *cesta* obsahuje prázdný řetězec zakončený hodnotou null.

*Cesta* vyrovnávací paměti musí být nejméně **_MAX_PATH** znaků dlouhá, aby k vešel úplný název vytvořené cesty. V opačném případě **_searchenv** může přetečení *cesta* vyrovnávací paměti a způsobí neočekávané chování.

**_wsearchenv** je verze širokého znaku **_searchenv**a argumenty, které mají **_wsearchenv** jsou širokoznaké řetězce. **_wsearchenv** a **_searchenv** se jinak chovají stejně.

Pokud *filename* je prázdný řetězec, vrátí tyto funkce **ENOENT**.

Pokud *filename* nebo *cesta* je **NULL** vyvolána ukazatel, obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL**.

Další informace o **errno** a kódy chyb, naleznete v tématu [errno – konstanty](../../c-runtime-library/errno-constants.md).

V jazyce C++ mají tyto funkce přetížení šablon, která vyvolávají novější, lépe zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv –**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
