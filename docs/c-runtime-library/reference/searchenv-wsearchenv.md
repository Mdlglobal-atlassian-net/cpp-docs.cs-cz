---
title: _searchenv –, _wsearchenv – | Microsoft Docs
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
ms.openlocfilehash: 62e0fea9154801f850640234355af53dc1154160
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="searchenv-wsearchenv"></a>_searchenv, _wsearchenv

Cesty prostředí se používá k vyhledání souboru. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_searchenv_s –, _wsearchenv_s –](searchenv-s-wsearchenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Název souboru* název souboru pro vyhledávání.

*název_proměnné* prostředí pro vyhledávání.

*název cesty* vyrovnávací paměti k uložení úplnou cestu.

## <a name="remarks"></a>Poznámky

**_Searchenv –** rutiny hledá cílový soubor v zadané doméně. *Název_proměnné* proměnná může být jakýkoli prostředí nebo uživatelem definované proměnné – například **cesta**, **LIB**, nebo **zahrnout**– určující seznam cesty adresářů. Protože **_searchenv –** je malá a velká písmena, *název_proměnné* by měl malá a velká písmena proměnné prostředí.

Rutiny nejprve hledá soubor v aktuálním pracovním adresáři. Pokud nenajde soubor, vypadá prostřednictvím adresáře, které jsou určené proměnnou prostředí. Pokud cílový soubor je v některém z těchto adresářů, cesta k nově vytvořený zkopírován do *pathname*. Pokud *filename* soubor nebyl nalezen, *pathname* obsahuje prázdný řetězec ukončené hodnotou null.

*Pathname* vyrovnávací paměti by měla být minimálně **_max_path –** znaků dlouhé zohlednit úplné délka sestavené cesta. V opačném **_searchenv –** může přetečení *pathname* vyrovnávací paměti a způsobit neočekávané chování.

**_wsearchenv –** je verze široká charakterová **_searchenv –**a argumenty, které mají **_wsearchenv –** jsou široká charakterová řetězce. **_wsearchenv –** a **_searchenv –** chovat jinak shodně.

Pokud *filename* je řetězec prázdný, vrátí tyto funkce **enoent –**.

Pokud *filename* nebo *pathname* je **NULL** ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte **errno** k **einval –**.

Další informace o **errno** a kódy chyb, najdete v části [errno – konstanty](../../c-runtime-library/errno-constants.md).

V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější, bezpečnější svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv –**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
