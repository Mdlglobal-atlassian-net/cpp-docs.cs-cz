---
title: "tmpfile – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: tmpfile
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords: tmpfile
dev_langs: C++
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4a5fa4d74e9d83cfce5063f66a1c123b0f96209d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tmpfile"></a>tmpfile
Vytvoří dočasný soubor. Tato funkce je zastaralý, protože bezpečnější verze je k dispozici. v tématu [tmpfile_s –](../../c-runtime-library/reference/tmpfile-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FILE *tmpfile( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného `tmpfile` vrací ukazatel datového proudu. Funkce `NULL` ukazatel.  
  
## <a name="remarks"></a>Poznámky  
 `tmpfile` Funkce vytvoří dočasný soubor a vrátí ukazatel do tohoto datového proudu. Dočasný soubor se vytvoří v kořenovém adresáři. Chcete-li vytvořit dočasný soubor v adresáři, než je kořenový adresář, použijte [tmpnam –](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) nebo [tempnam –](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) ve spojení s [fopen –](../../c-runtime-library/reference/fopen-wfopen.md).  
  
 Pokud soubor nelze otevřít, `tmpfile` vrátí `NULL` ukazatel. Toto dočasný soubor bude odstraněn automaticky při zavření souboru, když program ukončí normálně, nebo když `_rmtmp` je volána, za předpokladu, že aktuální pracovní adresář se nemění. Dočasný soubor je otevřen v `w+b` režimu (binární čtení a zápis).  
  
 Selhání může dojít, pokud se pokusíte více než tmp_max – (viz STDIO. H) volání s `tmpfile`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`tmpfile`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
> [!NOTE]
>  Tento příklad vyžaduje administrativní oprávnění ke spouštění v systému Windows Vista.  
  
```  
// crt_tmpfile.c  
// compile with: /W3  
// This program uses tmpfile to create a  
// temporary file, then deletes this file with _rmtmp.  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   int  i;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      if( (stream = tmpfile()) == NULL ) // C4996  
      // Note: tmpfile is deprecated; consider using tmpfile_s instead  
         perror( "Could not open new temporary file\n" );  
      else  
         printf( "Temporary file %d was created\n", i );  
   }  
  
   // Remove temporary files.  
   printf( "%d temporary files deleted\n", _rmtmp() );  
}  
```  
  
```Output  
Temporary file 1 was created  
Temporary file 2 was created  
Temporary file 3 was created  
3 temporary files deleted  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [_rmtmp –](../../c-runtime-library/reference/rmtmp.md)   
 [_tempnam –, _wtempnam –, tmpnam –, _wtmpnam –](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)