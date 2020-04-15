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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: afe9264351110bc062d6168ef803fa6fb796538a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341579"
---
# <a name="malloc"></a>malloc

Přiděluje bloky paměti.

## <a name="syntax"></a>Syntaxe

```C
void *malloc(
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Bajty přidělit.

## <a name="return-value"></a>Návratová hodnota

**malloc** vrátí ukazatel void přidělené místo nebo **NULL,** pokud není k dispozici dostatek paměti. Chcete-li vrátit ukazatel na jiný typ než **void**, použijte typ přetypované na vrácenou hodnotu. Úložný prostor, na který se vztahuje vrácená hodnota, je zaručeně vhodně zarovnán pro uložení libovolného typu objektu, který má požadavek na zarovnání menší nebo roven základnímu zarovnání. (V jazyce Visual C++ je základním zarovnáním zarovnání, které je vyžadováno pro **dvojité**nebo 8 bajtů. V kódu, který cílí na 64bitové platformy, je to 16 bajtů.) Pomocí [_aligned_malloc](aligned-malloc.md) přidělit úložiště pro objekty, které mají větší požadavek na zarovnání – `__declspec(align( n ))` například typy SSE [__m128](../../cpp/m128.md) a **__m256**a typy, které jsou deklarovány pomocí kde **n** je větší než 8. Pokud je *velikost* 0, **malloc** přiděluje položku nulové délky v haldě a vrátí platný ukazatel pro tuto položku. Vždy zkontrolujte návrat z **malloc**, i v případě, že množství požadované paměti je malý.

## <a name="remarks"></a>Poznámky

Funkce **malloc** přiděluje blok paměti o *velikosti* bajtů. Blok může být větší než *velikost* bajtů z důvodu místa, které je požadováno pro zarovnání a informace o údržbě.

**malloc** nastaví **errno** na **ENOMEM,** pokud se nezdaří přidělení paměti nebo pokud požadované množství paměti překročí **_HEAP_MAXREQ**. Informace o tomto a dalších kódech chyb naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Spouštěcí kód používá **malloc** k přidělení úložiště pro proměnné **_environ**, *envp*a *argv.* Následující funkce a jejich široké-charakter protějšky také volat **malloc**.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[_exec funkce](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[_spawn funkce](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[Printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[systém](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[getchar](getc-getwc.md)|[Staví](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[prohledává](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[získá](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

Funkce [_set_new_mode](set-new-mode.md) C++ nastaví nový režim obslužné rutiny pro **malloc**. Nový režim obslužné rutiny označuje, zda při selhání **malloc** volá novou rutinu obslužné rutiny nastavenou [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **malloc** nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Můžete přepsat toto výchozí chování tak, že když **malloc** selže přidělit paměť, **malloc** volá rutinu nové obslužné rutiny stejným způsobem, jako **nový** operátor, když se nezdaří ze stejného důvodu. Chcete-li přepsat výchozí, volejte `_set_new_mode(1)` v rané fázi programu nebo propojení s NEWMODE. OBJ (viz [Možnosti odkazu](../../c-runtime-library/link-options.md)).

Pokud je aplikace propojena s ladicí verzí knihoven run-time C, **malloc** překládá na [_malloc_dbg](malloc-dbg.md). Další informace o tom, jak je halda spravována během procesu ladění, naleznete v [tématu podrobnosti o ladění crt](/visualstudio/debugger/crt-debug-heap-details).

**malloc** je `__declspec(noalias)` `__declspec(restrict)`označen a ; to znamená, že je zaručeno, že funkce nebude měnit globální proměnné a že vrácený ukazatel není aliasován. Další informace naleznete v [tématu noalias](../../cpp/noalias.md) a [restrict](../../cpp/restrict.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**malloc**|\<stdlib.h> \<a malloc.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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
[Zdarma](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
