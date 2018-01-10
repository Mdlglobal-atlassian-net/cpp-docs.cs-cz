---
title: "_searchenv_s –, _wsearchenv_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "32"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6f1089aa1f772832417168a2262fa72069b3ede7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="searchenvs-wsearchenvs"></a>_searchenv_s, _wsearchenv_s
Vyhledá soubor pomocí cesty prostředí. Tyto verze nástroje [_searchenv –, _wsearchenv –](../../c-runtime-library/reference/searchenv-wsearchenv.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 [v]`filename`  
 Název souboru pro vyhledávání.  
  
 [v]`varname`  
 Prostředí pro vyhledávání.  
  
 [out]`pathname`  
 Vyrovnávací paměť pro uložení úplnou cestu.  
  
 [v]`numberOfElements`  
 Velikost `pathname` vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěšného; Kód chyby při selhání.  
  
 Pokud `filename` je řetězec prázdný, je vrácenou hodnotou `ENOENT`.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`filename`|`varname`|`pathname`|`numberOfElements`|Návratová hodnota|Obsah`pathname`|  
|----------------|---------------|----------------|------------------------|------------------|----------------------------|  
|všechny|všechny|`NULL`|všechny|`EINVAL`|není k dispozici|  
|`NULL`|všechny|všechny|všechny|`EINVAL`|nebyl změněn.|  
|všechny|všechny|všechny|<= 0|`EINVAL`|nebyl změněn.|  
  
 Pokud dojde k některé z těchto podmínek chyba, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `_searchenv_s` Rutiny hledá cílový soubor v zadané doméně. `varname` Proměnná může být jakýkoli prostředí nebo uživatelem definované proměnné, která určuje seznam cesty adresářů, jako například `PATH`, `LIB`, a `INCLUDE`. Protože `_searchenv_s` je malá a velká písmena, `varname` by měl malá a velká písmena proměnné prostředí. Pokud `varname` neodpovídá názvu proměnné prostředí definované v procesu prostředí, funkce vrátí hodnotu nula a `pathname` proměnné se nemění.  
  
 Rutiny nejprve hledá soubor v aktuálním pracovním adresáři. Pokud nenajde soubor, vypadá další prostřednictvím adresáře, určené proměnnou prostředí. Pokud cílový soubor je v některém z těchto adresářů, cesta k nově vytvořený zkopírován do `pathname`. Pokud `filename` soubor nebyl nalezen, `pathname` obsahuje prázdný řetězec ukončené hodnotou null.  
  
 `pathname` Vyrovnávací paměti by měla být minimálně `_MAX_PATH` znaků dlouhé zohlednit úplné délka sestavené cesta. V opačném `_searchenv_s` může přetečení `pathname` vyrovnávací paměti, což vede k neočekávanému chování.  
  
 `_wsearchenv_s`široká charakterová verze `_searchenv_s`; argumenty, které mají `_wsearchenv_s` jsou široká charakterová řetězce. `_wsearchenv_s`a `_searchenv_s` chovat jinak shodně.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsearchenv_s`|`_searchenv_s`|`_searchenv_s`|`_wsearchenv_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_searchenv_s`|\<stdlib.h >|  
|`_wsearchenv_s`|\<stdlib.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
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
 [Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)   
 [_searchenv –, _wsearchenv –](../../c-runtime-library/reference/searchenv-wsearchenv.md)   
 [GETENV –, _wgetenv –](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_putenv, _wputenv](../../c-runtime-library/reference/putenv-wputenv.md)