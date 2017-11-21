---
title: "_searchenv –, _wsearchenv – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "33"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 553d51363479a220b5850af2a7ff3ad880c31878
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="searchenv-wsearchenv"></a>_searchenv, _wsearchenv
Cesty prostředí se používá k vyhledání souboru. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_searchenv_s –, _wsearchenv_s –](../../c-runtime-library/reference/searchenv-s-wsearchenv-s.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Název souboru pro vyhledávání.  
  
 `varname`  
 Prostředí pro vyhledávání.  
  
 `pathname`  
 Vyrovnávací paměť pro uložení úplnou cestu.  
  
## <a name="remarks"></a>Poznámky  
 `_searchenv` Rutiny hledá cílový soubor v zadané doméně. `varname` Proměnná může být jakýkoli prostředí nebo uživatelem definované proměnné – například `PATH`, `LIB`, nebo `INCLUDE`– určující seznam cesty adresářů. Protože `_searchenv` je malá a velká písmena, `varname` by měl malá a velká písmena proměnné prostředí.  
  
 Rutiny nejprve hledá soubor v aktuálním pracovním adresáři. Pokud nenajde soubor, vypadá prostřednictvím adresáře, které jsou určené proměnnou prostředí. Pokud cílový soubor je v některém z těchto adresářů, cesta k nově vytvořený zkopírován do `pathname`. Pokud `filename` soubor nebyl nalezen, `pathname` obsahuje prázdný řetězec ukončené hodnotou null.  
  
 `pathname` Vyrovnávací paměti by měla být minimálně `_MAX_PATH` znaků dlouhé zohlednit úplné délka sestavené cesta. V opačném `_searchenv` může přetečení `pathname` vyrovnávací paměti a způsobit neočekávané chování.  
  
 `_wsearchenv`široká charakterová verze `_searchenv`a argumenty, které mají `_wsearchenv` jsou široká charakterová řetězce. `_wsearchenv`a `_searchenv` chovat jinak shodně.  
  
 Pokud `filename` je řetězec prázdný, vrátí tyto funkce `ENOENT`.  
  
 Pokud `filename` nebo `pathname` je `NULL` ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte `errno` k `EINVAL`.  
  
 Další informace o `errno` a kódy chyb, najdete v části [errno – konstanty](../../c-runtime-library/errno-constants.md).  
  
 V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější, bezpečnější svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsearchenv`|`_searchenv`|`_searchenv`|`_wsearchenv`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_searchenv`|\<stdlib.h >|  
|`_wsearchenv`|\<stdlib.h > nebo \<wchar.h >|  
  
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
 [Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)   
 [GETENV –, _wgetenv –](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_putenv –, _wputenv –](../../c-runtime-library/reference/putenv-wputenv.md)   
 [_searchenv_s –, _wsearchenv_s –](../../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)