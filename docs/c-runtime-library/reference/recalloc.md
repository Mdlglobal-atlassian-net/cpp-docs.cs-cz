---
title: _recalloc
ms.date: 11/04/2016
api_name:
- _recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: f06631fe4dd0abcb0b18895ccb04e5b52cda6a2c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949451"
---
# <a name="_recalloc"></a>_recalloc

Kombinace **realokace** a **calloc**. Znovu přidělí pole v paměti a inicializuje jeho prvky na hodnotu 0.

## <a name="syntax"></a>Syntaxe

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatel na dříve přidělený blok paměti.

*Automatické*<br/>
Počet elementů.

*hodnota*<br/>
Délka v bajtech každého elementu.

## <a name="return-value"></a>Návratová hodnota

**_recalloc** vrátí ukazatel **void** na blok paměti realokováno (a případně přesunuto).

Pokud není dostatek dostupné paměti pro rozšíření bloku na danou velikost, původní blok zůstane beze změny a vrátí **hodnotu null** .

Pokud je požadovaná velikost nulová, pak je uvolněn blok, na který odkazuje *memblock* ; Vrácená hodnota je **null**a *memblock* vlevo odkazuje na uvolněný blok.

Vrácená hodnota odkazuje na prostor úložiště, který je zaručen vhodným způsobem pro uložení libovolného typu objektu. Chcete-li získat ukazatel na jiný typ než **void**, použijte přetypování typu u vrácené hodnoty.

## <a name="remarks"></a>Poznámky

Funkce **_recalloc** změní velikost přiděleného bloku paměti. Argument *memblock* odkazuje na začátek bloku paměti. Pokud má memblock **hodnotu null**, **_recalloc** se chová stejným způsobem jako [calloc](calloc.md) a přidělí nový blok bajtů s *číselnou* * *velikostí* . Každý prvek je inicializován na hodnotu 0. Pokud *memblock* není **null**, mělo by se jednat o ukazatel vrácený předchozím voláním metody **calloc** [, pro](malloc.md)nebo [realokace](realloc.md).

Vzhledem k tomu, že nový blok může být v novém umístění v paměti, ukazatel vrácený funkcí **_recalloc** není zaručený ukazatel předaný pomocí argumentu *memblock* .

**_recalloc** nastaví **errno** na **ENOMEM** , pokud se přidělení paměti nepovede nebo pokud je velikost požadované paměti větší než **_HEAP_MAXREQ**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** volá **realokace** za účelem použití C++ funkce [_set_new_mode](set-new-mode.md) k nastavení nového režimu obslužné rutiny. Nový režim obslužné rutiny označuje, zda je při selhání **realokace** volána nová rutina obslužné rutiny, jak je nastaveno na [_set_new_handler](set-new-handler.md). Ve výchozím nastavení opětovná **alokace** nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, že když **_recalloc** nepomůže přidělit paměť, **realokace** volá novou rutinu obslužné rutiny stejným způsobem jako operátor **New** při neúspěchu ze stejného důvodu. Chcete-li přepsat výchozí hodnotu, zavolejte

```C
_set_new_mode(1);
```

do začátku v programu nebo propojte pomocí NEWMODE. OBJ.

Pokud je aplikace propojena s ladicí verzí knihoven C Runtime, **_recalloc** se přeloží na [_recalloc_dbg](recalloc-dbg.md). Další informace o tom, jak je halda spravována během procesu ladění, naleznete v [haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** je označena `__declspec(restrict)`jako `__declspec(noalias)` , což znamená, že funkce zaručuje, že nemění globální proměnné a že ukazatel, který vrátil, nemá alias. Další informace najdete [v tématech a](../../cpp/noalias.md) [omezení](../../cpp/restrict.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_recalloc**|\<Stdlib. h > a \<. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[free](free.md)<br/>
[Možnosti odkazů](../../c-runtime-library/link-options.md)<br/>
