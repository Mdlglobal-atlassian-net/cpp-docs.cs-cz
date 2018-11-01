---
title: calloc
ms.date: 11/04/2016
apiname:
- calloc
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
- calloc
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: 59aa535136cf32ea5dd68b8917ec969eee41e2ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666970"
---
# <a name="calloc"></a>calloc

Pole v paměti přidělí s prvky inicializovány na hodnotu 0.

## <a name="syntax"></a>Syntaxe

```C
void *calloc(
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Číslo*<br/>
Počet prvků.

*Velikost*<br/>
Délka v bajtech každého prvku.

## <a name="return-value"></a>Návratová hodnota

**calloc** vrací ukazatel do přiděleného místa. Úložný prostor odkazovaný hodnotou return je zaručeno, že jako vhodně zarovnaný pro úložiště libovolného typu objektu. Získání ukazatele na typ jiný než **void**, použijte přetypování typu na návratovou hodnotu.

## <a name="remarks"></a>Poznámky

**Calloc** funkce přiděluje místo pro celou řadu *číslo* prvky, každý o délce *velikost* bajtů. Každý prvek je inicializován na hodnotu 0.

**calloc** nastaví **errno** k **ENOMEM** Pokud selhání přidělení paměti, nebo pokud požadované množství paměti překročí **_heap_maxreq –**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**calloc** volání **malloc** použití jazyka C++ [_set_new_mode](set-new-mode.md) funkce nastavíte nový režim obslužné rutiny. Nový režim obslužné rutiny Určuje, zda je při selhání, **malloc** je volat nové rutiny obsluhy úmluvu [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **malloc** nevolá nové rutiny obsluhy při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby, když **calloc** selže přidělování paměti, **malloc** volá nové rutiny obsluhy ve stejném způsobu, jakým **nové** operátor Když selže ze stejného důvodu. Chcete-li přepsat výchozí hodnotu, zavolejte

```C
_set_new_mode(1);
```

zpočátku v programu nebo propojení s knihovnou NEWMODE. OBJ (viz [možnosti propojení](../../c-runtime-library/link-options.md)).

Když je aplikace spojena s ladicí verzí knihovny run-time C **calloc** přeloží na [_calloc_dbg –](calloc-dbg.md). Další informace o tom, jak je spravována halda během procesu ladění, naleznete v tématu [haldy pro ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** je označen `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce je zaručeno, že neupraví globální proměnné a Vrácený ukazatel není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**calloc**|\<stdlib.h > a \<malloc.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_calloc.c
// This program uses calloc to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>

int main( void )
{
   long *buffer;

   buffer = (long *)calloc( 40, sizeof( long ) );
   if( buffer != NULL )
      printf( "Allocated 40 long integers\n" );
   else
      printf( "Can't allocate memory\n" );
   free( buffer );
}
```

```Output
Allocated 40 long integers
```

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
