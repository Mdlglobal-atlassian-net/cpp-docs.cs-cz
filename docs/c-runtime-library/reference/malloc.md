---
title: "malloc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords: malloc
dev_langs: C++
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72dd949aa8d894ba49f53a6440de20beea070e2b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="malloc"></a>malloc
Přiděluje bloky paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *malloc(  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `size`  
 Počet bajtů přidělit.  
  
## <a name="return-value"></a>Návratová hodnota  
 `malloc`vrací neplatný ukazatel na přidělené místo nebo `NULL` Pokud není k dispozici dostatek paměti. Jiné než vrátit ukazatel typu `void`, používat typ, který přetypovat na návratovou hodnotu. Prostor úložiště ukazuje návratovou hodnotu záruku, že vhodně zarovnána pro ukládání libovolného typu objektu, který má zarovnání požadavek menší než nebo rovna k u základní zarovnání. (V jazyce Visual C++, je základní zarovnání zarovnání, který se vyžaduje `double`, nebo 8 bajtů. V kódu, která je cílena 64bitové platformy je 16 bajtů.) Použití [_aligned_malloc –](../../c-runtime-library/reference/aligned-malloc.md) se přidělit úložiště pro objekty, které mají větší požadavek zarovnání – například typy SSE [__m128](../../cpp/m128.md) a `__m256`a typy, které jsou deklarovány s použitím `__declspec(align( n ))`kde `n` je větší než 8. Pokud `size` 0, `malloc` přiděluje položku nulové délky v haldě a vrací neplatný ukazatel na danou položku. Vždy zkontrolujte návratový z `malloc`i v případě, že je malá velikost paměti požadované.  
  
## <a name="remarks"></a>Poznámky  
 `malloc` Funkce přiděluje blok paměti alespoň `size` bajtů. Blok může být větší než `size` bajtů z důvodu místa, které je nutné pro informace o zarovnání a údržby.  
  
 `malloc`Nastaví `errno` k `ENOMEM` Pokud selže přidělení paměti nebo velikost paměti požadované překračuje `_HEAP_MAXREQ`. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Kód spuštění používá `malloc` se přidělit úložiště pro `_environ`, `envp`, a `argv` proměnné. Následující funkce a jejich protějšky široká charakterová také zavolat `malloc`.  
  
|||||  
|-|-|-|-|  
|[calloc –](../../c-runtime-library/reference/calloc.md)|[fscanf –](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw –](../../c-runtime-library/reference/getw.md)|[setvbuf –](../../c-runtime-library/reference/setvbuf.md)|  
|[_exec – funkce](../../c-runtime-library/exec-wexec-functions.md)|[fseek](../../c-runtime-library/reference/fseek-fseeki64.md)|[_popen –](../../c-runtime-library/reference/popen-wpopen.md)|[_spawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)|  
|[fgetc –](../../c-runtime-library/reference/fgetc-fgetwc.md)|[fsetpos –](../../c-runtime-library/reference/fsetpos.md)|[printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_strdup –](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)|  
|[_fgetchar –](../../c-runtime-library/reference/fgetc-fgetwc.md)|[_fullpath –](../../c-runtime-library/reference/fullpath-wfullpath.md)|[putc –](../../c-runtime-library/reference/putc-putwc.md)|[systém](../../c-runtime-library/reference/system-wsystem.md)|  
|[fgets –](../../c-runtime-library/reference/fgets-fgetws.md)|[fwrite –](../../c-runtime-library/reference/fwrite.md)|[putchar –](../../c-runtime-library/reference/putc-putwc.md)|[_tempnam –](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](../../c-runtime-library/reference/getc-getwc.md)|[_putenv –](../../c-runtime-library/reference/putenv-wputenv.md)|[ungetc –](../../c-runtime-library/reference/ungetc-ungetwc.md)|  
|[fputc –](../../c-runtime-library/reference/fputc-fputwc.md)|[GetChar](../../c-runtime-library/reference/getc-getwc.md)|[Vloží](../../c-runtime-library/reference/puts-putws.md)|[vfprintf –](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[_fputchar –](../../c-runtime-library/reference/fputc-fputwc.md)|[_getcwd –](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[_putw –](../../c-runtime-library/reference/putw.md)|[vprintf –](../../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|  
|[fputs –](../../c-runtime-library/reference/fputs-fputws.md)|[_getdcwd –](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)||  
|[fread –](../../c-runtime-library/reference/fread.md)|[Získá](../../c-runtime-library/gets-getws.md)|[_searchenv –](../../c-runtime-library/reference/searchenv-wsearchenv.md)||  
  
 C++ [_set_new_mode –](../../c-runtime-library/reference/set-new-mode.md) funkce nastaví nový režim obslužné rutiny pro `malloc`. Nový režim obslužná rutina označuje, jestli při selhání, `malloc` je volat nové rutiny obslužných rutin jako sady pomocí [_set_new_handler –](../../c-runtime-library/reference/set-new-handler.md). Ve výchozím nastavení `malloc` nevyvolá nové rutiny ovladače při selhání při přidělování paměti. Toto výchozí chování můžete přepsat tak, aby, když `malloc` nepodaří přidělit paměť, `malloc` volání nové rutiny obslužná rutina ve stejné způsobem, jako `new` operátor nepodporuje, když se nezdaří ze stejného důvodu. Chcete-li přepsat výchozí nastavení, volejte `_set_new_mode(1)` časná v aplikaci nebo odkaz s NEWMODE. OBJ (viz [možnosti odkazů](../../c-runtime-library/link-options.md)).  
  
 Když aplikace je spojená s verzí ladicí běhové knihovny jazyka C, `malloc` přeloží na [_malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md). Další informace o spravováni haldě ladění během najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `malloc`je označena `__declspec(noalias)` a `__declspec(restrict)`; to znamená, že funkce záruku, že není k úpravě globálních proměnných, a že ukazatele vrátí není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`malloc`|\<stdlib.h > a \<malloc.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_malloc.c  
// This program allocates memory with  
// malloc, then frees the memory with free.  
  
#include <stdlib.h>   // For _MAX_PATH definition  
#include <stdio.h>  
#include <malloc.h>  
  
int main( void )  
{  
   char *string;  
  
   // Allocate space for a path name  
   string = malloc( _MAX_PATH );  
  
   // In a C++ file, explicitly cast malloc's return.  For example,   
   // string = (char *)malloc( _MAX_PATH );  
  
   if( string == NULL )  
      printf( "Insufficient memory available\n" );  
   else  
   {  
      printf( "Memory space allocated for path name\n" );  
      free( string );  
      printf( "Memory freed\n" );  
   }  
}  
```  
  
```Output  
Memory space allocated for path name  
Memory freed  
```  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [calloc –](../../c-runtime-library/reference/calloc.md)   
 [Uvolněte](../../c-runtime-library/reference/free.md)   
 [realloc –](../../c-runtime-library/reference/realloc.md)   
 [_aligned_malloc –](../../c-runtime-library/reference/aligned-malloc.md)
