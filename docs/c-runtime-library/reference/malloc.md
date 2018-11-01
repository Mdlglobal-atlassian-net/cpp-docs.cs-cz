---
title: malloc
ms.date: 11/04/2016
apiname:
- malloc
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
f1_keywords:
- malloc
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
ms.openlocfilehash: e6a007fb6f089ebf1c9f5fc9ce59cbcbf0b13888
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520364"
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

*Velikost*<br/>
Počet bajtů k přidělení.

## <a name="return-value"></a>Návratová hodnota

**malloc** vrací neplatný ukazatel do přiděleného místa nebo **NULL** Pokud není k dispozici dostatek paměti. Pro jiné než vrací ukazatel na typ **void**, použijte přetypování typu na návratovou hodnotu. Úložný prostor odkazovaný hodnotou return je zaručeno, že jako vhodně zarovnaný pro úložiště libovolného typu, který má požadavek na zarovnání nižší než nebo rovna na tento základní zarovnání. (V jazyce Visual C++ je je základní zarovnáním zarovnání, které je vyžadováno pro **double**, nebo 8 bajtů. V kódu, který cílí na 64bitové platformy je 16 bajtový.) Použití [_aligned_malloc](aligned-malloc.md) pro přidělení úložiště pro objekty, které mají větší požadavek na zarovnání – například typy SSE [__m128](../../cpp/m128.md) a **__m256**a typy, které jsou deklarovaná příkazem using `__declspec(align( n ))` kde **n** je větší než 8. Pokud *velikost* je 0, **malloc** přiděluje položku nulové délky v haldě a vrátí platný ukazatel na danou položku. Vždy zkontrolujte návrat z **malloc**, i když je velikost požadované paměti malá.

## <a name="remarks"></a>Poznámky

**Malloc** funkce přidělí blok paměti velikosti alespoň *velikost* bajtů. Blok může být větší než *velikost* bajtů z důvodu místa požadovaného pro informace o zarovnání a údržbě.

**malloc** nastaví **errno** k **ENOMEM** Pokud selhání přidělení paměti, nebo pokud požadované množství paměti překročí **_heap_maxreq –**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Spouštěcí kód používá **malloc** k přidělení úložiště pro **_environ**, *envp*, a *argv* proměnné. Následující funkce a jejich protějšky s širokými znaky také volat **malloc**.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf –](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[Funkce _exec](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[_spawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc –](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath –](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[Systém](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc –](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[GetChar](getc-getwc.md)|[Vloží](puts-putws.md)|[vfprintf –](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs –](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[Získá](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

C++ [_set_new_mode](set-new-mode.md) funkce nastaví nový režim obslužné rutiny pro **malloc**. Nový režim obslužné rutiny Určuje, zda je při selhání, **malloc** je volat nové rutiny obsluhy úmluvu [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **malloc** nevolá nové rutiny obsluhy při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby, když **malloc** selže přidělování paměti, **malloc** volá nové rutiny obsluhy ve stejném způsobu, jakým **nové** operátor Když selže ze stejného důvodu. Chcete-li přepsat výchozí hodnotu, zavolejte `_set_new_mode(1)` zpočátku v programu nebo propojení s knihovnou NEWMODE. OBJ (viz [možnosti propojení](../../c-runtime-library/link-options.md)).

Když je aplikace spojena s ladicí verzí knihovny run-time C **malloc** přeloží na [_malloc_dbg](malloc-dbg.md). Další informace o tom, jak je spravována halda během procesu ladění, naleznete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**malloc** je označen `__declspec(noalias)` a `__declspec(restrict)`; to znamená, že funkce je zaručeno, že neupraví globální proměnné a Vrácený ukazatel není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**malloc**|\<stdlib.h > a \<malloc.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
