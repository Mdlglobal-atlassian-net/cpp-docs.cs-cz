---
title: _recalloc
ms.date: 4/2/2020
api_name:
- _recalloc
- _o__recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 342228635e69d49e0b51196aef03a296c1f0e652
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917856"
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

Funkce **_recalloc** změní velikost přiděleného bloku paměti. Argument *memblock* odkazuje na začátek bloku paměti. Pokud *memblock* má memblock **hodnotu null**, **_recalloc** se chová stejným způsobem jako [calloc](calloc.md) a přiděluje nový blok bajtů s *číselnou* * *velikostí* . Každý prvek je inicializován na hodnotu 0. Pokud *memblock* není **null**, mělo by se jednat o ukazatel vrácený předchozím voláním metody **calloc** [, pro](malloc.md)nebo [realokace](realloc.md).

Vzhledem k tomu, že nový blok může být v novém umístění v paměti, ukazatel vrácený **_recalloc** není zaručen jako ukazatel předaný pomocí argumentu *memblock* .

**_recalloc** nastaví **errno** na **ENOMEM** , pokud se přidělení paměti nepovede nebo pokud je velikost požadované paměti větší než **_HEAP_MAXREQ**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** volá **realokace** za účelem použití funkce C++ [_set_new_mode](set-new-mode.md) k nastavení nového režimu obslužné rutiny. Nový režim obslužné rutiny označuje, zda je při selhání **realokace** volána nová rutina obslužné rutiny, jak je nastavena [_set_new_handler](set-new-handler.md). Ve výchozím nastavení opětovná **alokace** nevolá novou rutinu obslužné rutiny při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby při **_recalloc** nepomohly přidělit paměť, opětovná **alokace** volá novou rutinu obslužné rutiny stejným způsobem jako operátor **New** při neúspěchu ze stejného důvodu. Chcete-li přepsat výchozí hodnotu, zavolejte

```C
_set_new_mode(1);
```

do začátku v programu nebo propojte pomocí NEWMODE. OBJ.

Pokud je aplikace propojena s ladicí verzí běhových knihoven jazyka C, **_recalloc** překládá na [_recalloc_dbg](recalloc-dbg.md). Další informace o tom, jak je halda spravována během procesu ladění, naleznete v [haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** je `__declspec(noalias)` označena `__declspec(restrict)`jako, což znamená, že funkce zaručuje, že nemění globální proměnné a že ukazatel, který vrátil, nemá alias. Další informace najdete [v tématech a](../../cpp/noalias.md) [omezení](../../cpp/restrict.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_recalloc**|\<Stdlib. h> a \<. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[dost](free.md)<br/>
[Možnosti propojení](../../c-runtime-library/link-options.md)<br/>
