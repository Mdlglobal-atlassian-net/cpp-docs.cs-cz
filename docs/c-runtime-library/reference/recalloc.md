---
title: _recalloc
ms.date: 11/04/2016
apiname:
- _recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 3bcc238dcb950a8e30af16efc557e99d933efe92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357718"
---
# <a name="recalloc"></a>_recalloc

Kombinace **realloc** a **calloc**. Znovu alokuje pole v paměti a inicializuje jeho prvky na hodnotu 0.

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
Ukazatele na blok paměti dříve přidělené.

*Číslo*<br/>
Počet prvků.

*Velikost*<br/>
Délka v bajtech každého prvku.

## <a name="return-value"></a>Návratová hodnota

**_recalloc –** vrátí **void** ukazatele na blok paměti a nevyčerpané prostředky se (může být přesunutý).

Pokud není k dispozici dostatek paměti a rozbalte na danou velikost bloku, původního bloku je vlevo beze změny, a **NULL** je vrácena.

Pokud je požadovaná velikost nula, pak bloku odkazované *memblock* je uvolněn; vrácená hodnota je **NULL**, a *memblock* zbývá odkazující na uvolněné bloku.

Návratová hodnota odkazuje na prostor úložiště, která je zaručeně jako vhodně zarovnaný pro úložiště libovolného typu objektu. Získání ukazatele na typ jiný než **void**, použijte přetypování typu na návratovou hodnotu.

## <a name="remarks"></a>Poznámky

**_Recalloc –** funkce změní velikost přidělené paměti bloku. *Memblock* argument odkazuje na začátku bloku paměti. Pokud *memblock* je **NULL**, **_recalloc –** se chová stejně jako [calloc](calloc.md) a přiděluje nový blok *číslo*  *  *velikost* bajtů. Každý prvek je inicializován na hodnotu 0. Pokud *memblock* není **NULL**, měla by být ukazatel vrácený z předchozího volání **calloc**, [malloc](malloc.md), nebo [realloc ](realloc.md).

Vzhledem k tomu, že nový blok může být nové umístění paměti, vrácený ukazatel **_recalloc –** nemusí být předány prostřednictvím ukazatele *memblock* argument.

**_recalloc –** nastaví **errno** k **ENOMEM** Pokud selhání přidělení paměti, nebo pokud požadované množství paměti překročí **_heap_maxreq –**. Informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc –** volání **realloc** Chcete-li použít C++ [_set_new_mode](set-new-mode.md) funkce nastavíte nový režim obslužné rutiny. Nový režim obslužné rutiny Určuje, zda je při selhání, **realloc** je volat nové rutiny obsluhy úmluvu [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **realloc** nevolá nové rutiny obsluhy při selhání přidělení paměti. Toto výchozí chování můžete přepsat tak, aby, když **_recalloc –** selže přidělování paměti, **realloc** volá nové rutiny obsluhy ve stejném způsobu, jakým **nové** – operátor provede, když ze stejného důvodu selže. Chcete-li přepsat výchozí hodnotu, zavolejte

```C
_set_new_mode(1);
```

zpočátku v programu nebo propojení s NEWMODE.OBJ.

Když je aplikace spojena s ladicí verzí knihovny run-time C **_recalloc –** přeloží na [_recalloc_dbg –](recalloc-dbg.md). Další informace o tom, jak je spravována halda během procesu ladění, naleznete v tématu [haldy pro ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc –** je označen `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce je zaručeno, že neupraví globální proměnné a Vrácený ukazatel není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h > a \<malloc.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[free](free.md)<br/>
[Možnosti odkazů](../../c-runtime-library/link-options.md)<br/>
