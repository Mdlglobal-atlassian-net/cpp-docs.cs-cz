---
title: "_unlink –, _wunlink – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _unlink
- _wunlink
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
- _tunlink
- _unlink
- wunlink
- _wunlink
dev_langs:
- C++
helpviewer_keywords:
- files [C++], deleting
- _wunlink function
- wunlink function
- unlink function
- _unlink function
- tunlink function
- files [C++], removing
- _tunlink function
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 394638d8e8115bb5b3dc9629669067f5f9158c77
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="unlink-wunlink"></a>_unlink, _wunlink
Odstranění souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _unlink(  
   const char *filename   
);  
int _wunlink(  
   const wchar_t *filename   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Název souboru k odebrání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí v případě úspěchu vrátí 0. Funkce, jinak vrátí hodnotu -1 a nastaví `errno` k `EACCES`, určuje soubor jen pro čtení, což znamená, že cesta nebo `ENOENT`, což znamená, soubor nebo cesta nebyla nalezena nebo cestu adresáře.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratové kódy.  
  
## <a name="remarks"></a>Poznámky  
 `_unlink` Funkce odstraní soubor určený touto `filename`. `_wunlink` široká charakterová verze `_unlink`; `filename` argument `_wunlink` je široká charakterová řetězec. Tyto funkce chovají stejně jako jinak.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tunlink`|`_unlink`|`_unlink`|`_wunlink`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_unlink`|\<IO.h > a \<stdio.h >|  
|`_wunlink`|\<IO.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="code-example"></a>Příklad kódu  
 Tento program používá _unlink – odstranit CRT_UNLINK. TXT.  
  
```  
// crt_unlink.c  
  
#include <stdio.h>  
  
int main( void )  
{  
   if( _unlink( "crt_unlink.txt" ) == -1 )  
      perror( "Could not delete 'CRT_UNLINK.TXT'" );  
   else  
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );  
}  
```  
  
### <a name="input-crtunlinktxt"></a>Vstup: crt_unlink.txt  
  
```  
This file will be deleted.  
```  
  
### <a name="sample-output"></a>Vzorový výstup  
  
```  
Deleted 'CRT_UNLINK.TXT'  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [_close –](../../c-runtime-library/reference/close.md)   
 [remove, _wremove](../../c-runtime-library/reference/remove-wremove.md)