---
title: "přejmenovat, _wrename – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- rename
- _wrename
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
- _wrename
- _trename
- Rename
dev_langs: C++
helpviewer_keywords:
- trename function
- directories [C++], renaming
- renaming directories
- names [C++], changing file
- _trename function
- rename function
- wrename function
- files [C++], renaming
- _wrename function
- names [C++], changing directory
- renaming files
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5324b594631f0d45a49d04e771318a84d101fc32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rename-wrename"></a>rename, _wrename
Přejmenujte soubor nebo adresář.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int rename(  
   const char *oldname,  
   const char *newname   
);  
int _wrename(  
   const wchar_t *oldname,  
   const wchar_t *newname   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *oldname*  
 Ukazatel na starý název.  
  
 *newname*  
 Ukazatel na nový název.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrátí 0, pokud je úspěšné. Funkce vrátí nenulovou hodnotu, při chybě a nastaví `errno` na jednu z následujících hodnot:  
  
 `EACCES`  
 Soubor nebo adresář zadaný *newname* již existuje nebo nebylo možné vytvořit (neplatná cesta); nebo *oldname* je adresář a *newname* Určuje jinou cestu.  
  
 `ENOENT`  
 Soubor nebo cesta zadaná položkou *oldname* nebyl nalezen.  
  
 `EINVAL`  
 Název obsahuje neplatné znaky.  
  
 Možné vrácené hodnoty, najdete v části [_doserrno – _errno, syserrlist a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 **Přejmenovat** funkce přejmenuje soubor nebo adresář zadaný *oldname* na daný název podle *newname*. Starý název musí být cesta existující soubor nebo adresář. Nový název nesmí být název existující soubor nebo adresář. Můžete použít **přejmenovat** přesunout soubor z jednoho adresáře nebo zařízení do jiné tím, že jiné cestě *newname* argument. Ale nemůžete použít **přejmenovat** k přesunutí adresáře. Adresáře můžete přejmenovat, ale není přesunut.  
  
 `_wrename`široká charakterová verze **_rename**; argumenty, které mají `_wrename` jsou široká charakterová řetězce. `_wrename`a **_rename** chovat jinak shodně.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_trename`|**Přejmenování**|**Přejmenování**|`_wrename`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|**Přejmenování**|\<IO.h > nebo \<stdio.h >|  
|`_wrename`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_renamer.c  
/* This program attempts to rename a file named  
 * CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation  
 * to succeed, a file named CRT_RENAMER.OBJ must exist and  
 * a file named CRT_RENAMER.JBO must not exist.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   int  result;  
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";  
  
   /* Attempt to rename file: */  
   result = rename( old, new );  
   if( result != 0 )  
      printf( "Could not rename '%s'\n", old );  
   else  
      printf( "File '%s' renamed to '%s'\n", old, new );  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)