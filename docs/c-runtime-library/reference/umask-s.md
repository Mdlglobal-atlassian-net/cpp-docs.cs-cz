---
title: "_umask_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _umask_s
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
- unmask_s
- _umask_s
dev_langs: C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 67899d1dd082ffd023ca78ac8a4961288ffd0165
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="umasks"></a>_umask_s
Nastaví výchozí oprávnění souboru masku. Verzi [_umask –](../../c-runtime-library/reference/umask.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _umask_s(  
   int mode,  
   int * pOldMode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`mode`  
 Výchozí nastavení oprávnění.  
  
 [out]`oldMode`  
 Předchozí hodnotu nastavení oprávnění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí kód chyby, pokud `Mode` neurčuje platný režim nebo `pOldMode` ukazatel `NULL`.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`mode`|`pOldMode`|**Návratová hodnota**|**Obsah**  `oldMode`|  
|------------|----------------|----------------------|--------------------------------|  
|všechny|`NULL`|`EINVAL`|nedojde ke změně|  
|Neplatný režim|všechny|`EINVAL`|nedojde ke změně|  
  
 Pokud dojde k jedné z výše uvedených podmínek, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `_umask_s` vrátí `EINVAL` a nastaví `errno` k `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `_umask_s` Funkce nastaví oprávnění souborů maska aktuální proces do režimu určeného `mode`. Oprávnění souborů maska upraví nastavení oprávnění nových souborů vytvořených `_creat`, `_open`, nebo `_sopen`. Pokud bit do masky je 1, příslušné bity v hodnotě souboru požadované oprávnění nastavená na hodnotu 0 (zakázáno). Pokud bit v maska je 0, odpovídající bit je ponechán beze změny. Nastavení oprávnění pro vytvoření nového souboru není nastavena, dokud soubor se zavřel poprvé.  
  
 Celočíselný výraz `pmode` obsahuje jedno nebo obě následující manifestu konstanty definované v SYS\STAT. V:  
  
 `_S_IWRITE`  
 Zápis povolen.  
  
 `_S_IREAD`  
 Čtení povolené.  
  
 `_S_IREAD | _S_IWRITE`  
 Čtení a zápis povolen.  
  
 Pokud jsou zadány oba konstanty, jsou spojeny pomocí operátoru bitové operace OR ( `|` ). Pokud `mode` argument je `_S_IREAD`, čtení není povolen (soubor je jen pro zápis). Pokud `mode` argument je `_S_IWRITE`, není povolen zápis (soubor je jen pro čtení). Pokud je bit zápisu nastavený v masce, všechny nové soubory bude třeba jen pro čtení. Upozorňujeme, že MS-DOS a operační systémy Windows, jsou všechny soubory čitelný; není možné udělit oprávnění jen pro zápis. Proto nastavení čtení bit s `_umask_s` nemá žádný vliv na režimy v souboru.  
  
 Pokud `pmode` není kombinace jednoho z manifestu konstanty nebo zahrnuje alternativní sady konstant, funkce bude ignorovat ty.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_umask_s`|\<IO.h > a \<sys/stat.h > a \<sys/types.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_umask_s.c  
/* This program uses _umask_s to set  
 * the file-permission mask so that all future  
 * files will be created as read-only files.  
 * It also displays the old mask.  
 */  
  
#include <sys/stat.h>  
#include <sys/types.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int oldmask, err;  
  
   /* Create read-only files: */  
   err = _umask_s( _S_IWRITE, &oldmask );  
   if (err)  
   {  
      printf("Error setting the umask.\n");  
      exit(1);  
   }  
   printf( "Oldmask = 0x%.4x\n", oldmask );  
}  
```  
  
```Output  
Oldmask = 0x0000  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)   
 [_chmod –, _wchmod –](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_creat –, _wcreat –](../../c-runtime-library/reference/creat-wcreat.md)   
 [_mkdir –, _wmkdir –](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)   
 [_umask –](../../c-runtime-library/reference/umask.md)