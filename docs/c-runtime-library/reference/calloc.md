---
title: calloc
description: Funkce běhové knihovny jazyka C calloc přiděluje paměť s nulovou inicializací.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 76243342233ea895b947d4aa4a246b316aa8f405
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918726"
---
# <a name="calloc"></a>calloc

Přidělí pole v paměti prvky inicializovanými na hodnotu 0.

## <a name="syntax"></a>Syntaxe

```C
void *calloc(
   size_t number,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Automatické*<br/>
Počet elementů.

*hodnota*<br/>
Délka v bajtech každého elementu.

## <a name="return-value"></a>Návratová hodnota

**calloc** vrací ukazatel na přidělený prostor. Prostor úložiště, na který je odkazováno návratovou hodnotou, je zaručeně vhodně zarovnán pro úložiště libovolného typu objektu. Chcete-li získat ukazatel na jiný typ než **void**, použijte přetypování typu u vrácené hodnoty.

## <a name="remarks"></a>Poznámky

Funkce **calloc** přiděluje prostor úložiště pro pole *číselných* prvků, přičemž každý z nich má délku *velikosti* bajtů. Každý prvek je inicializován na hodnotu 0.

**calloc** nastaví **errno** na **ENOMEM** , pokud se přidělení paměti nepovede nebo pokud je velikost požadované paměti větší než **_HEAP_MAXREQ**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

V případě implementace od společnosti Microsoft, pokud je hodnota *Number* nebo *Size* nula, vrátí **calloc** ukazatel na přidělený blok nenulové velikosti. Pokus o čtení nebo zápis prostřednictvím vráceného ukazatele vede k nedefinovanému chování.

**calloc** používá funkci C++ [_set_new_mode](set-new-mode.md) k nastavení *nového režimu obslužné rutiny*. Nový režim obslužné rutiny označuje, zda je při selhání **calloc** volat novou rutinu obslužné rutiny, jak je nastaveno [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **calloc** nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, že když **calloc** nepomůže přidělit paměť, volá novou rutinu obslužné rutiny stejným způsobem jako operátor **New** při neúspěchu ze stejného důvodu. Chcete-li přepsat výchozí hodnotu, zavolejte

```C
_set_new_mode(1);
```

v rané fázi programu nebo se připojte pomocí *NEWMODE. OBJ* (viz [možnosti propojení](../../c-runtime-library/link-options.md)).

Pokud je aplikace propojena s ladicí verzí knihoven C Runtime, **calloc** překládá na [_calloc_dbg](calloc-dbg.md). Další informace o tom, jak je halda spravována během procesu ladění, naleznete v [haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** je `__declspec(noalias)` označena `__declspec(restrict)`jako, což znamená, že funkce zaručuje, že nemění globální proměnné a že ukazatel, který vrátil, není aliasem. Další informace najdete [v tématech a](../../cpp/noalias.md) [omezení](../../cpp/restrict.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**calloc**|\<Stdlib. h> a \<. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
[dost](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
