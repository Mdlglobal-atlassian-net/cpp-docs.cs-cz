---
title: "_access –, _waccess – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _access
- _waccess
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
- _waccess
- _access
- taccess
- waccess
- _taccess
dev_langs: C++
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c4d8c6d8caae8b36f372ce75b4fc91638f9e78e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="access-waccess"></a>_access, _waccess
Určuje, zda je soubor jen pro čtení, nebo ne. Bezpečnější verze jsou k dispozici. v tématu [_access_s –, _waccess_s –](../../c-runtime-library/reference/access-s-waccess-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _access(   
   const char *path,   
   int mode   
);  
int _waccess(   
   const wchar_t *path,   
   int mode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `path`  
 Cesta k souboru nebo adresáře.  
  
 `mode`  
 Atribut pro čtení a zápis.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jednotlivé funkce vrátí hodnotu 0, pokud má soubor daného režimu. Funkce vrátí hodnotu -1, pokud je soubor s názvem neexistuje nebo nemá daného režimu; v takovém případě `errno` je nastavit, jak je znázorněno v následující tabulce.  
  
 `EACCES`  
 Přístup byl odepřen: nastavení oprávnění souboru neumožňuje zadaný přístup.  
  
 `ENOENT`  
 Název souboru nebo cesta nebyla nalezena.  
  
 `EINVAL`  
 Neplatný parametr.  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 Při použití s soubory, `_access` funkce určuje, zda určený soubor nebo adresář existuje a má zadaný hodnotou atributy `mode`. Při použití s adresáře `_access` pouze určuje, zda existuje zadaný adresář; v [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] a novější operační systémy, všechny adresáře čtení a zápisu přístup.  
  
|`mode`Hodnota|Kontroly v souboru|  
|------------------|---------------------|  
|00|Pouze existence|  
|02|Jen pro zápis|  
|04|jen pro čtení|  
|06|Čtení a zápis|  
  
 Tato funkce pouze ověří, zda soubor a adresáře jsou jen pro čtení nebo Ne, nekontroluje nastavení zabezpečení systému souborů. Pro které budete potřebovat token přístupu. Další informace o zabezpečení systému souborů najdete v tématu [přístupové tokeny](http://msdn.microsoft.com/library/windows/desktop/aa374909). Třídy knihovny ATL existuje neposkytuje této funkce. v tématu [CAccessToken třída](../../atl/reference/caccesstoken-class.md).  
  
 `_waccess`široká charakterová verze `_access`; `path` argument `_waccess` je široká charakterová řetězec. `_waccess`a `_access` chovat jinak shodně.  
  
 Tato funkce ověří jeho parametry. Pokud `path` je `NULL` nebo `mode` neurčuje platný režim obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastaví funkci `errno` k `EINVAL` a vrátí hodnotu -1.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_taccess`|`_access`|`_access`|`_waccess`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|  
|-------------|---------------------|----------------------|  
|`_access`|\<IO.h >|\<errno.h >|  
|`_waccess`|\<wchar.h > nebo \<io.h >|\<errno.h >|  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `_access` zkontrolujte soubor s názvem crt_ACCESS. C toho, zda existuje a zda je povolen zápis.  
  
```  
// crt_access.c  
// compile with: /W1  
// This example uses _access to check the file named  
// crt_ACCESS.C to see if it exists and if writing is allowed.  
  
#include  <io.h>  
#include  <stdio.h>  
#include  <stdlib.h>  
  
int main( void )  
{  
    // Check for existence.  
    if( (_access( "crt_ACCESS.C", 0 )) != -1 )  
    {  
        printf_s( "File crt_ACCESS.C exists.\n" );  
  
        // Check for write permission.  
        // Assume file is read-only.  
        if( (_access( "crt_ACCESS.C", 2 )) == -1 )  
            printf_s( "File crt_ACCESS.C does not have write permission.\n" );  
    }  
}  
```  
  
```Output  
File crt_ACCESS.C exists.  
File crt_ACCESS.C does not have write permission.  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [_chmod –, _wchmod –](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_fstat –, _fstat32 –, _fstat64 –, _fstati64 –, _fstat32i64 –, _fstat64i32 –](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)   
 [_stat, _wstat – funkce](../../c-runtime-library/reference/stat-functions.md)