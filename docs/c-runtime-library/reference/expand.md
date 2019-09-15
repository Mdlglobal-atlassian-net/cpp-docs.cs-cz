---
title: _expand
ms.date: 11/04/2016
api_name:
- _expand
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
ms.openlocfilehash: cb986d893bd862e61ae595317a890fb489c19919
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941561"
---
# <a name="_expand"></a>_expand

Změní velikost bloku paměti.

## <a name="syntax"></a>Syntaxe

```C
void *_expand(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatel na dříve přidělený blok paměti.

*hodnota*<br/>
Nová velikost v bajtech

## <a name="return-value"></a>Návratová hodnota

**_expand** vrátí ukazatel void na blok přerozdělené paměti. **_expand**, na rozdíl od **realokace**, nemůže přesunout blok, aby se změnila jeho velikost. Proto pokud je k dispozici dostatek paměti pro rozšíření bloku bez jeho přesunutí, parametr *memblock* na **_expand** je stejný jako návratová hodnota.

**_expand** vrací **hodnotu null** , pokud je zjištěna chyba během své operace. Například pokud se **_expand** používá ke zmenšení bloku paměti, může detekovat poškození v rámci malé blokující haldy nebo neplatný ukazatel na blok a vracet **hodnotu null**.

Pokud není k dispozici dostatek paměti pro rozšíření bloku na danou velikost, aniž by došlo k jeho přesunutí, funkce vrátí **hodnotu null**. **_expand** nikdy nevrací blok rozbalený na velikost menší než požadovaná hodnota. Pokud dojde k selhání, **errno** indikuje povahu selhání. Další informace o **errno**najdete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Vrácená hodnota odkazuje na prostor úložiště, který je zaručen vhodným způsobem pro uložení libovolného typu objektu. Chcete-li zjistit novou velikost položky, použijte **_msize**. Chcete-li získat ukazatel na jiný typ než **void**, použijte přetypování typu u vrácené hodnoty.

## <a name="remarks"></a>Poznámky

Funkce **_expand** změní velikost dříve přiděleného bloku paměti tím, že se pokusí zvětšit nebo sbalit blok bez přesunu jeho umístění do haldy. Parametr *memblock* odkazuje na začátek bloku. Parametr *Size* poskytuje novou velikost bloku v bajtech. Obsah bloku zůstane nezměněný na kratší z nových a starých velikostí. *memblock* by neměl být blok, který byl uvolněn.

> [!NOTE]
> Na 64y bitových platformech **_expand** nemusí zablokovat blok, pokud je nová velikost menší než aktuální velikost; Konkrétně, pokud byl blok menší než hodnota 16 KB a je tedy přidělena v haldě s nízkou fragmentaci, **_expand** opustí blok beze změny a vrátí *memblock*.

Pokud je aplikace propojena s ladicí verzí knihoven C Runtime, **_expand** se přeloží na [_expand_dbg](expand-dbg.md). Další informace o tom, jak je halda spravována během procesu ladění, naleznete v [haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Tato funkce ověří své parametry. Pokud je *memblock* ukazatel s hodnotou null, tato funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **hodnotu null**. Pokud je *Velikost* větší než **_HEAP_MAXREQ**, **errno** je nastaven na **ENOMEM** a funkce vrátí **hodnotu null**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_expand**|\<. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_expand.c

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   char *bufchar;
   printf( "Allocate a 512 element buffer\n" );
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )
      exit( 1 );
   printf( "Allocated %d bytes at %Fp\n",
         _msize( bufchar ), (void *)bufchar );
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )
      printf( "Can't expand" );
   else
      printf( "Expanded block to %d bytes at %Fp\n",
            _msize( bufchar ), (void *)bufchar );
   // Free memory
   free( bufchar );
   exit( 0 );
}
```

```Output
Allocate a 512 element buffer
Allocated 512 bytes at 002C12BC
Expanded block to 1024 bytes at 002C12BC
```

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
