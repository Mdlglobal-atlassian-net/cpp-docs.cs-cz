---
title: calloc
description: Funkce knihovny runtime C calloc přiděluje paměť s nulovou inicializací.
ms.date: 4/2/2020
api_name:
- calloc
- _o_calloc
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
- calloc
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: fb4f7d6dc059023d34cb0b811edf5dfb48cb7a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333653"
---
# <a name="calloc"></a>calloc

Přidělí pole v paměti s prvky inicializovanými na 0.

## <a name="syntax"></a>Syntaxe

```C
void *calloc(
   size_t number,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Číslo*<br/>
Počet prvků.

*Velikost*<br/>
Délka v bajtů každého prvku.

## <a name="return-value"></a>Návratová hodnota

**calloc** vrátí ukazatel na přidělené místo. Úložný prostor, na který se vztahuje vrácená hodnota, je zaručeně vhodně zarovnán pro uložení libovolného typu objektu. Chcete-li získat ukazatel na jiný typ než **void**, použijte typ přetypované na vrácenou hodnotu.

## <a name="remarks"></a>Poznámky

Funkce **calloc** přiděluje úložný prostor pro pole *číselných* prvků, každý z bajtů *velikosti* délky. Každý prvek je inicializován na 0.

**calloc** nastaví **errno** na **ENOMEM,** pokud se nezdaří přidělení paměti nebo pokud požadované množství paměti překročí **_HEAP_MAXREQ**. Informace o tomto a dalších kódech chyb naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

V implementaci společnosti Microsoft, pokud *je číslo* nebo *velikost* nula, **calloc** vrátí ukazatel přiděleného bloku nenulové velikosti. Pokus o čtení nebo zápis prostřednictvím vráceného ukazatele vede k nedefinovanému chování.

**calloc** používá funkci [c++ _set_new_mode](set-new-mode.md) k nastavení *nového režimu obslužné rutiny*. Nový režim obslužné rutiny označuje, zda je při selhání **calloc** volání nové rutiny obslužné rutiny nastavené [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **calloc** nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby při **calloc** nezdaří přidělit paměť, volá rutinu nové obslužné rutiny stejným způsobem, jako **nový** operátor, když se nezdaří ze stejného důvodu. Chcete-li přepsat výchozí,

```C
_set_new_mode(1);
```

brzy ve vašem programu, nebo odkaz s *NEWMODE. OBJ* (viz [Možnosti odkazu](../../c-runtime-library/link-options.md)).

Pokud je aplikace propojena s ladicí verzí knihoven c run-time, **calloc** se překládá na [_calloc_dbg](calloc-dbg.md). Další informace o tom, jak haldy je spravována během procesu ladění, naleznete [v tématu HALDA ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** je `__declspec(noalias)` `__declspec(restrict)`označen a , což znamená, že funkce je zaručeno, že nezmění globální proměnné a že vrácený ukazatel není aliased. Další informace naleznete v [tématu noalias](../../cpp/noalias.md) a [restrict](../../cpp/restrict.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**calloc**|\<stdlib.h> \<a malloc.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[Zdarma](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
