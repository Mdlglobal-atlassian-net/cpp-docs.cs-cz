---
title: _aligned_recalloc
ms.date: 4/2/2020
api_name:
- _aligned_recalloc
- _o__aligned_recalloc
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
- aligned_recalloc
- _aligned_recalloc
helpviewer_keywords:
- aligned_recalloc function
- _aligned_recalloc function
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
ms.openlocfilehash: af12322742c777cda879e01cb9c054297f807725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350490"
---
# <a name="_aligned_recalloc"></a>_aligned_recalloc

Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc](aligned-offset-malloc.md) a inicializuje paměť na 0.

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment
);
```

### <a name="parameters"></a>Parametry

*memblok*<br/>
Aktuální ukazatel bloku paměti.

*Číslo*<br/>
Počet prvků.

*Velikost*<br/>
Velikost v bajtů každého prvku.

*Zarovnání*<br/>
Hodnota zarovnání, která musí být celá mocnina 2.

## <a name="return-value"></a>Návratová hodnota

**_aligned_recalloc** vrátí ukazatel void na přerozdělenou (a případně přesunutou) paměťový blok. Vrácená hodnota je **NULL,** pokud je velikost nulová a argument vyrovnávací paměti není **NULL**, nebo pokud není k dispozici dostatek paměti pro rozšíření bloku na danou velikost. V prvním případě je uvolněn původní blok. V druhém případě je původní blok beze změny. Vrácená hodnota odkazuje na úložný prostor, který je zaručeně vhodně zarovnán pro uložení libovolného typu objektu. Chcete-li získat ukazatel na jiný typ než void, použijte typ přetypované na vrácenou hodnotu.

Je chyba přerozdělit paměť a změnit zarovnání bloku.

## <a name="remarks"></a>Poznámky

**_aligned_recalloc** je založen na **malloc**. Další informace o používání **_aligned_offset_malloc**naleznete v [tématu malloc](malloc.md).

Tato funkce nastaví **errno** na **ENOMEM,** pokud se přidělení paměti nezdařilo nebo pokud byla požadovaná velikost větší než **_HEAP_MAXREQ**. Další informace o **errno**naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Také **_aligned_recalloc** ověřuje jeho parametry. Pokud *zarovnání* není mocninu 2, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, vrátí tato funkce **hodnotu NULL** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_recalloc**|\<malloc.h>|

## <a name="see-also"></a>Viz také

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
