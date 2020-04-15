---
title: _aligned_offset_realloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_realloc
- _o__aligned_offset_realloc
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
- aligned_offset_realloc
- _aligned_offset_realloc
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
ms.openlocfilehash: b27f5000a48ec3aafe37c6bd59e9b9acddd5bec5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350568"
---
# <a name="_aligned_offset_realloc"></a>_aligned_offset_realloc

Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_realloc(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*memblok*<br/>
Aktuální ukazatel bloku paměti.

*Velikost*<br/>
Velikost přidělení paměti.

*Zarovnání*<br/>
Hodnota zarovnání, která musí být celá mocnina 2.

*Posun*<br/>
Posun do přidělení paměti vynutit zarovnání.

## <a name="return-value"></a>Návratová hodnota

**_aligned_offset_realloc** vrátí ukazatel void na přerozdělenou (a případně přesunutou) paměťový blok. Vrácená hodnota je **NULL,** pokud je velikost nulová a argument vyrovnávací paměti není **NULL**, nebo pokud není k dispozici dostatek paměti pro rozšíření bloku na danou velikost. V prvním případě je uvolněn původní blok. V druhém případě je původní blok beze změny. Vrácená hodnota odkazuje na úložný prostor, který je zaručeně vhodně zarovnán pro uložení libovolného typu objektu. Chcete-li získat ukazatel na jiný typ než void, použijte typ přetypované na vrácenou hodnotu.

**_aligned_offset_realloc** je `__declspec(noalias)` `__declspec(restrict)`označena a , což znamená, že je zaručeno, že funkce nebude měnit globální proměnné a že vrácený ukazatel není aliasován. Další informace naleznete v [tématu noalias](../../cpp/noalias.md) a [restrict](../../cpp/restrict.md).

## <a name="remarks"></a>Poznámky

Stejně jako [_aligned_offset_malloc](aligned-offset-malloc.md) **umožňuje _aligned_offset_realloc** zarovnání struktury v odsazení uvnitř struktury.

**_aligned_offset_realloc** je založen na **malloc**. Další informace o používání **_aligned_offset_malloc**naleznete v [tématu malloc](malloc.md). Pokud *memblock* je **NULL**, funkce volá **_aligned_offset_malloc** interně.

Tato funkce nastaví **errno** na **ENOMEM,** pokud se přidělení paměti nezdařilo nebo pokud byla požadovaná velikost větší než **_HEAP_MAXREQ**. Další informace o **errno**naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Také **_aligned_offset_realloc** ověřuje jeho parametry. Pokud *trasování* není mocninu 2 nebo pokud *je posun* větší nebo roven *velikosti* a nenulová, tato funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, vrátí tato funkce **hodnotu NULL** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<malloc.h>|

## <a name="example"></a>Příklad

Další informace naleznete [v tématu _aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Viz také

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
