---
title: "_access_s –, _waccess_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _access_s
- _waccess_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- waccess_s
- access_s
- _waccess_s
- _access_s
dev_langs: C++
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f562d62f3edb1f09fe6d7ebe7b509411ad2dc8c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="accesss-waccesss"></a>_access_s, _waccess_s
Určuje oprávnění pro čtení a zápis souborů. Toto je verze [_access –, _waccess –](../../c-runtime-library/reference/access-waccess.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _access_s(   
   const char *path,   
   int mode   
);  
errno_t _waccess_s(   
   const wchar_t *path,   
   int mode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `path`  
 Cesta k souboru nebo adresáře.  
  
 `mode`  
 Nastavení oprávnění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jednotlivé funkce vrátí hodnotu 0, pokud má soubor daného režimu. Funkce vrátí kód chyby, pokud uvedeného souboru neexistuje nebo není dostupný v daném režimu. V takovém případě funkce vrátí kód chyby ze sady takto a také nastaví `errno` na stejnou hodnotu.  
  
 `EACCES`  
 Přístup byl odepřen. Nastavení oprávnění souboru neumožňuje zadaný přístup.  
  
 `ENOENT`  
 Název souboru nebo cesta nebyla nalezena.  
  
 `EINVAL`  
 Neplatný parametr.  
  
 Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 Při použití s soubory, `_access_s` funkce určuje, zda zadaný soubor existuje a je přístupný jako zadaný hodnotou `mode`. Při použití s adresáře `_access_s` pouze určuje, zda zadaný adresář existuje. V [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] a novější operační systémy, všechny adresáře čtení a zápisu přístup.  
  
|Hodnota režimu|Kontroly v souboru|  
|----------------|---------------------|  
|00|Pouze existence.|  
|02|Oprávnění zapisovat.|  
|04|Oprávnění ke čtení.|  
|06|Oprávnění ke čtení a zápisu.|  
  
 Oprávnění pro čtení nebo zápis souboru není dostatek zajistit možnost otevření souboru. Například pokud soubor uzamčen jiným procesem, nemusí být dostupné i když `_access_s` vrátí hodnotu 0.  
  
 `_waccess_s`široká charakterová verze `_access_s`, kde `path` argument `_waccess_s` je široká charakterová řetězec. V opačném `_waccess_s` a `_access_s` chovají stejně jako.  
  
 Tyto funkce ověřit jejich parametrů. Pokud `path` je `NULL` nebo `mode` neurčuje platný režim obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_taccess_s`|`_access_s`|`_access_s`|`_waccess_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_access_s`|\<IO.h >|\<errno.h >|  
|`_waccess_s`|\<wchar.h > nebo \<io.h >|\<errno.h >|  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `_access_s` zkontrolujte soubor s názvem crt_access_s.c toho, zda existuje a zda je povolen zápis.  
  
```  
// crt_access_s.c  
  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
    errno_t err = 0;  
  
    // Check for existence.   
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )  
    {  
        printf_s( "File crt_access_s.c exists.\n" );  
  
        // Check for write permission.   
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )  
        {  
            printf_s( "File crt_access_s.c does have "  
                      "write permission.\n" );  
        }  
        else  
        {  
            printf_s( "File crt_access_s.c does not have "  
                      "write permission.\n" );  
        }  
    }  
    else  
    {  
        printf_s( "File crt_access_s.c does not exist.\n" );  
    }  
}  
```  
  
```Output  
File crt_access_s.c exists.  
File crt_access_s.c does not have write permission.  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [_access –, _waccess –](../../c-runtime-library/reference/access-waccess.md)   
 [_chmod –, _wchmod –](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_fstat –, _fstat32 –, _fstat64 –, _fstati64 –, _fstat32i64 –, _fstat64i32 –](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)   
 [_stat, _wstat – funkce](../../c-runtime-library/reference/stat-functions.md)