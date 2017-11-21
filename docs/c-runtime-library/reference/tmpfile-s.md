---
title: "tmpfile_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: tmpfile_s
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
f1_keywords: tmpfile_s
dev_langs: C++
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7e3864d3d2c63c9ef1b83d1e01252ad3f3ce3eee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tmpfiles"></a>tmpfile_s
Vytvoří dočasný soubor. Je verzi [tmpfile –](../../c-runtime-library/reference/tmpfile.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t tmpfile_s(  
   FILE** pFilePtr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pFilePtr`  
 Adresa ukazatel k uložení adresu generovaného ukazatele na datový proud.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu 0, pokud bylo úspěšné, kód chyby při selhání.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`pFilePtr`|**Návratová hodnota**|**Obsah**  `pFilePtr`|  
|----------------|----------------------|---------------------------------|  
|`NULL`|`EINVAL`|nebyl změněn.|  
  
 Pokud dojde k chybě ověření výše uvedených parametrů, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a že návratová hodnota `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `tmpfile_s` Funkce vytvoří dočasný soubor a vloží do tohoto datového proudu v ukazatel `pFilePtr` argument. Dočasný soubor se vytvoří v kořenovém adresáři. Chcete-li vytvořit dočasný soubor v adresáři, než je kořenový adresář, použijte [tmpnam_s –](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md) nebo [tempnam –](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) ve spojení s [fopen –](../../c-runtime-library/reference/fopen-wfopen.md).  
  
 Pokud soubor nelze otevřít, `tmpfile_s` zapíše `NULL` k `pFilePtr` parametr. Toto dočasný soubor bude odstraněn automaticky při zavření souboru, když program ukončí normálně, nebo když `_rmtmp` je volána, za předpokladu, že aktuální pracovní adresář se nemění. Dočasný soubor je otevřen v `w+b` režimu (binární čtení a zápis).  
  
 Selhání může dojít, pokud se pokusíte více než `TMP_MAX_S` (viz STDIO. H) volání s`tmpfile_s.`  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`tmpfile_s`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
> [!NOTE]
>  Tento příklad vyžaduje administrativní oprávnění ke spouštění v systému Windows Vista.  
  
```  
// crt_tmpfile_s.c  
// This program uses tmpfile_s to create a  
// temporary file, then deletes this file with _rmtmp.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char tempstring[] = "String to be written";  
   int  i;  
   errno_t err;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      err = tmpfile_s(&stream);  
      if( err )  
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