---
title: malloc
ms.date: 4/2/2020
api_name:
- malloc
- _o_malloc
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- malloc
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
ms.openlocfilehash: 4e699920f37139be40542ba91b3740cd9edef148
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917517"
---
# <a name="malloc"></a>malloc

Přidělí bloky paměti.

## <a name="syntax"></a>Syntaxe

```C
void *malloc(
   size_t size
);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Počet bajtů k přidělení.

## <a name="return-value"></a>Návratová hodnota

typ **\ vrátí ukazatel** void na přidělený prostor nebo **hodnotu null** , pokud není k dispozici dostatek paměti. Chcete-li vrátit ukazatel na jiný typ než **void**, použijte přetypování typu u vrácené hodnoty. Prostor úložiště, na který je odkazováno návratovou hodnotou, je zaručen vhodným způsobem pro úložiště libovolného typu objektu, který má požadavek na zarovnání menší nebo roven základnímu zarovnání. (V Visual C++ základní zarovnání je zarovnání vyžadované pro **Double**nebo 8 bajtů. V kódu, který cílí na 64 bitů, je 16 bajtů.) Použijte [_aligned_malloc](aligned-malloc.md) k přidělení úložiště pro objekty, které mají větší požadavek na zarovnání – například typy SSE [__m128](../../cpp/m128.md) a **__m256**a typy deklarované pomocí `__declspec(align( n ))` , kde **n** je větší než 8. Pokud je *Velikost* **0, hodnota** \ 0 přidělí položku s nulovou délkou v haldě a vrátí platný ukazatel na tuto položku. V případě, že je požadovaný objem paměti **malý, vždy**vraťte se změnami.

## <a name="remarks"></a>Poznámky

Funkce **malloc** prodělovat přiděluje blok paměti o *velikosti* alespoň bajtů. Blok může být větší než *Velikost* bajtů z důvodu místa, které je nutné pro informace o zarovnání a údržbě.

**errno** nastaví **ENOMEM** , pokud se nepovede **přidělit paměť** , nebo pokud je velikost požadované paměti větší než **_HEAP_MAXREQ**. Další informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Spouštěcí **kód používá pro přidělení úložiště pro proměnné** **_environ**, *envp*a *argv* . Následující funkce a jejich protějšky na jejich úrovni se **zavolají také**jako zastavení.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[funkce _exec](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[funkce _spawn](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[systém](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf –](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc –](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc –](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[GetChar](getc-getwc.md)|[zaskladnění](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf –](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[Získá](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

Funkce [_Set_new_mode](set-new-mode.md) jazyka C++ nastaví nový režim obslužné rutiny pro stav **".** Nový režim obslužné rutiny **označuje, zda je při** selhání zavolána nová rutina obslužné rutiny, jak je nastavena [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **malloc** nevolá hodnota \ nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby se při neúspěšném přidělení paměti nezdařila **volání nové** rutiny obslužné rutiny stejným způsobem jako operátor **New** , když dojde **k chybě ze** stejného důvodu. Chcete-li přepsat výchozí hodnotu `_set_new_mode(1)` , zavolejte na začátku v programu nebo se připojte pomocí NEWMODE. OBJ (viz [možnosti propojení](../../c-runtime-library/link-options.md)).

Když je aplikace propojená s ladicí verzí běhových knihoven jazyka C, **přeloží se** na [_malloc_dbg](malloc-dbg.md). Další informace o tom, jak je halda spravována během procesu ladění, naleznete v části [Podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**má označení** `__declspec(noalias)` `__declspec(restrict)`. To znamená, že funkce je zaručena, že nemění globální proměnné a že ukazatel, který vrátil, nemá alias. Další informace najdete [v tématech a](../../cpp/noalias.md) [omezení](../../cpp/restrict.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**malloc**|\<Stdlib. h> a \<. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[dost](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
