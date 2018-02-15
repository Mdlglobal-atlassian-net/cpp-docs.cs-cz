---
title: "setvbuf – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- setvbuf
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
f1_keywords:
- setvbuf
dev_langs:
- C++
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 072a1a9b1fca01dc8c6266f65232e4a8d8183580
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="setvbuf"></a>setvbuf
Ovládací prvky datového proudu do vyrovnávací paměti a velikost vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int setvbuf(  
   FILE *stream,  
   char *buffer,  
   int mode,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Ukazatel na `FILE` struktura.  
  
 `buffer`  
 Uživatel, který přidělené vyrovnávací paměti.  
  
 `mode`  
 Režim ukládání do vyrovnávací paměti.  
  
 `size`  
 Velikost vyrovnávací paměti v bajtech. Povolený rozsah: 2 < = `size` < = INT_MAX (2147483647). Interně hodnota zadaná pro `size` se zaokrouhlí směrem dolů na nejbližší násobek. 2.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu 0.  
  
 Pokud `stream` je `NULL`, nebo pokud `mode` nebo `size` je v rámci platný změn, není volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, tato funkce vrátí hodnotu -1 a nastaví je povoleno spuštění `errno` k `EINVAL`.  
  
 Informace o těchto a dalších kódy chyb naleznete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `setvbuf` Funkce umožňuje programu řídit i ukládání do vyrovnávací paměti a velikost vyrovnávací paměti `stream`. `stream` musí odkazovat na otevření souboru, který neprošel vstupně-výstupní operace, protože byl otevřen. Toto pole ukazuje `buffer` slouží jako vyrovnávací paměť, pokud je `NULL`, v takovém případě `setvbuf` používá automaticky přidělené vyrovnávací paměti o délce `size`/2 * 2 bajtů.  
  
 Musí být v režimu `_IOFBF`, `_IOLBF`, nebo `_IONBF`. Pokud `mode` je `_IOFBF` nebo `_IOLBF`, pak `size` se používá jako velikost vyrovnávací paměti. Pokud `mode` je `_IONBF`, datový proud je bez vyrovnávací paměti a `size` a `buffer` jsou ignorovány. Hodnoty pro `mode` a jejich významy jsou:  
  
 `_IOFBF`  
 Úplné ukládání do vyrovnávací paměti; To znamená `buffer` slouží jako vyrovnávací paměť a `size` se používá jako velikost vyrovnávací paměti. Pokud `buffer` je `NULL`, automaticky přiděleného vyrovnávací paměti `size` dlouho bajty se používá.  
  
 `_IOLBF`  
 U některých systémů tímto způsobem řádek ukládání do vyrovnávací paměti. Pro Win32 chování je však stejný jako `_IOFBF` -úplné ukládání do vyrovnávací paměti.  
  
 `_IONBF`  
 Žádné vyrovnávací paměť je použít, bez ohledu na to `buffer` nebo `size`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`setvbuf`|\<stdio.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_setvbuf.c  
// This program opens two streams: stream1  
// and stream2. It then uses setvbuf to give stream1 a  
// user-defined buffer of 1024 bytes and stream2 no buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char buf[1024];  
   FILE *stream1, *stream2;  
  
   if( fopen_s( &stream1, "data1", "a" ) == 0 &&  
       fopen_s( &stream2, "data2", "w" ) == 0 )  
   {  
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )  
         printf( "Incorrect type or size of buffer for stream1\n" );  
      else  
         printf( "'stream1' now has a buffer of 1024 bytes\n" );  
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )  
         printf( "Incorrect type or size of buffer for stream2\n" );  
      else  
         printf( "'stream2' now has no buffer\n" );  
      _fcloseall();  
   }  
}  
```  
  
```Output  
'stream1' now has a buffer of 1024 bytes  
'stream2' now has no buffer  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fclose –, _fcloseall –](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush –](../../c-runtime-library/reference/fflush.md)   
 [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md)   
 [setbuf](../../c-runtime-library/reference/setbuf.md)