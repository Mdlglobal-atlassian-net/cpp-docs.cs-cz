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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 57972a48336d8dd362b5da7513c854703134921b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338126"
---
# <a name="_recalloc"></a>_recalloc

Kombinace **relokace** a **calloc**. Přerozdělí pole v paměti a inicializuje jeho prvky na 0.

## <a name="syntax"></a>Syntaxe

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*memblok*<br/>
Ukazatel na dříve přidělený blok paměti.

*Číslo*<br/>
Počet prvků.

*Velikost*<br/>
Délka v bajtů každého prvku.

## <a name="return-value"></a>Návratová hodnota

**_recalloc** vrátí ukazatel **void** na přerozdělenou (a případně přesunutou) paměťový blok.

Pokud není k dispozici dostatek paměti pro rozšíření bloku na danou velikost, původní blok zůstane beze změny **a** null je vrácena.

Pokud je požadovaná velikost nulová, je blok, na který ukazuje *memblock,* uvolněn; vrácená hodnota je **NULL**a *memblock* je ponechán a směřující na uvolněný blok.

Vrácená hodnota odkazuje na úložný prostor, který je zaručeně vhodně zarovnán pro uložení libovolného typu objektu. Chcete-li získat ukazatel na jiný typ než **void**, použijte typ přetypované na vrácenou hodnotu.

## <a name="remarks"></a>Poznámky

Funkce **_recalloc** změní velikost přiděleného bloku paměti. Argument *memblock* odkazuje na začátek bloku paměti. Pokud *memblock* je **NULL**, **_recalloc** se chová stejným způsobem jako [calloc](calloc.md) a přiděluje nový blok*velikosti* *čísla* * bajtů. Každý prvek je inicializován na 0. Pokud *memblock* není **NULL**, by měl být ukazatel vrácena předchozí volání **calloc**, [malloc](malloc.md), nebo [reloc](realloc.md).

Vzhledem k tomu, že nový blok může být v novém umístění paměti, ukazatel vrácený **_recalloc** není zaručeno, že ukazatel prošel *memblock* argument.

**_recalloc** nastaví **errno** na **ENOMEM,** pokud se nezdaří přidělení paměti nebo pokud požadované množství paměti překročí **_HEAP_MAXREQ**. Informace o tomto a dalších kódech chyb naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** volá **realloc,** aby bylo možné použít funkci [_set_new_mode](set-new-mode.md) C++ k nastavení nového režimu obslužné rutiny. Nový režim obslužné rutiny označuje, zda při selhání je **přečíslono** volat novou rutinu obslužné rutiny nastavené [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **reloc** nevolá rutinu nové obslužné rutiny při selhání připřidělování paměti. Můžete přepsat toto výchozí chování tak, že když **_recalloc** nepodaří přidělit paměť, **realloc** volá rutinu nové obslužné rutiny stejným způsobem, jako **nový** operátor, když se nezdaří ze stejného důvodu. Chcete-li přepsat výchozí,

```C
_set_new_mode(1);
```

brzy v programu, nebo odkaz s NEWMODE.OBJ.

Pokud je aplikace propojena s ladicí verzí knihoven run-time C, **_recalloc** překládá na [_recalloc_dbg](recalloc-dbg.md). Další informace o tom, jak haldy je spravována během procesu ladění, naleznete [v tématu HALDA ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** je `__declspec(noalias)` `__declspec(restrict)`označena a , což znamená, že je zaručeno, že funkce nebude měnit globální proměnné a že vrácený ukazatel není aliasován. Další informace naleznete v [tématu noalias](../../cpp/noalias.md) a [restrict](../../cpp/restrict.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> \<a malloc.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[Zdarma](free.md)<br/>
[Možnosti propojení](../../c-runtime-library/link-options.md)<br/>
