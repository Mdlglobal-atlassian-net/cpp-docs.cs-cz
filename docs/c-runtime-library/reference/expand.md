---
title: _expand
ms.date: 11/04/2016
apiname:
- _expand
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
ms.openlocfilehash: c1606bedbb1264bddb7674c829fe456f506d6584
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335201"
---
# <a name="expand"></a>_expand

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
Ukazatele na blok paměti dříve přidělené.

*Velikost*<br/>
Nová velikost v bajtech.

## <a name="return-value"></a>Návratová hodnota

**_rozšířit** vrací neplatný ukazatel na blok znovu přidělit paměti. **_rozšířit**, na rozdíl od **realloc**, nelze přesunout ke změně jeho velikosti bloku. Proto, pokud není dostatek paměti k dispozici bez přesouvání, rozbalte bloku *memblock* parametr **_expand** je stejný jako návratovou hodnotu.

**_rozšířit** vrátí **NULL** při rozpoznání chyby během jeho operace. Například pokud **_expand** se používá pro zmenšení blok paměti, může zjišťování poškození haldy malých bloku nebo ukazatel neplatný blok a vrátit **NULL**.

Pokud není dostatek paměti k dispozici bez přesouvání ji rozbalte bloku na danou velikost, funkce vrátí **NULL**. **_rozšířit** nikdy nevrátí blok rozšířené na velikost menší než požadovaný. Pokud dojde k selhání, **errno** označuje podstatu tohoto selhání. Další informace o **errno**, naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Návratová hodnota odkazuje na prostor úložiště, která je zaručeně jako vhodně zarovnaný pro úložiště libovolného typu objektu. Chcete-li zkontrolovat velikost nové položky, použijte **_msize –**. Získání ukazatele na typ jiný než **void**, použijte přetypování typu na návratovou hodnotu.

## <a name="remarks"></a>Poznámky

**_Expand** funkce změní velikost blok paměti dříve přidělené tak, že zkusíte rozbalit nebo sbalit blok bez přesouvání jeho umístění v haldě. *Memblock* parametr odkazuje na začátku bloku. *Velikost* parametr poskytuje novou velikost bloku, v bajtech. Obsah bloku je až po kratší velikostí novém i starém beze změny. *memblock* by neměl být blok, který byl uvolněn.

> [!NOTE]
> Na 64bitových platformách **_expand** nemusí smlouvy bloku, pokud nová velikost je menší než aktuální velikost; zejména, pokud blok byl menší než 16 kB a proto přidělených haldu s nízkou fragmentací **_expand**  opustí blok beze změny a vrátí *memblock*.

Když je aplikace spojena s ladicí verzí knihovny run-time C **_expand** přeloží na [_expand_dbg –](expand-dbg.md). Další informace o tom, jak je spravována halda během procesu ladění, naleznete v tématu [haldy pro ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

Tato funkce ověřuje své parametry. Pokud *memblock* je ukazatel s hodnotou null, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **NULL**. Pokud *velikost* je větší než **_heap_maxreq –**, **errno** je nastavena na **ENOMEM** a funkce vrátí **NULL**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
