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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c719f62a089b1c233bac193f3431d0375af826eb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910264"
---
# <a name="_aligned_offset_realloc"></a>_aligned_offset_realloc

Změní velikost bloku paměti, který byl přidělen pomocí [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc](aligned-offset-malloc.md).

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

*memblock*<br/>
Aktuální ukazatel bloku paměti.

*hodnota*<br/>
Velikost přidělené paměti.

*bod*<br/>
Hodnota zarovnání, která musí být celočíselnou mocninou 2.

*polohy*<br/>
Posun k přidělení paměti pro vynucení zarovnání.

## <a name="return-value"></a>Návratová hodnota

**_aligned_offset_realloc** vrátí ukazatel void na blok paměti realokováno (a případně přesunuto). Návratová hodnota má **hodnotu null** , pokud je velikost nulová a argument buffer nemá **hodnotu null**, nebo pokud není k dispozici dostatek paměti pro rozšíření bloku na danou velikost. V prvním případě je původní blok uvolněn. V druhém případě se původní blok nezměnil. Vrácená hodnota odkazuje na prostor úložiště, který je zaručen vhodným způsobem pro uložení libovolného typu objektu. Chcete-li získat ukazatel na jiný typ než void, použijte přetypování typu u vrácené hodnoty.

**_aligned_offset_realloc** je `__declspec(noalias)` označena `__declspec(restrict)`jako, což znamená, že funkce zaručuje, že nemění globální proměnné a že ukazatel, který vrátil, nemá alias. Další informace najdete [v tématech a](../../cpp/noalias.md) [omezení](../../cpp/restrict.md).

## <a name="remarks"></a>Poznámky

Podobně [_aligned_offset_malloc](aligned-offset-malloc.md)jako _aligned_offset_malloc **_aligned_offset_realloc** umožňuje, aby byla struktura zarovnána na posunu v rámci struktury.

**_aligned_offset_realloc** je založena na **systému.** Další informace o použití **_aligned_offset_malloc**naleznete v tématu [.](malloc.md) Pokud *memblock* má Memblock **hodnotu null**, funkce volá interně **_aligned_offset_malloc** .

Tato funkce nastaví **errno** na **ENOMEM** , pokud se přidělení paměti nepovedlo nebo pokud je požadovaná velikost větší než **_HEAP_MAXREQ**. Další informace o **errno**najdete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). **_Aligned_offset_realloc** také ověřuje jeho parametry. Pokud *Zarovnání* není mocninou 2 nebo pokud je *posun* větší nebo roven *velikosti* a nenulové hodnotě, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrátí **hodnotu null** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<. h>|

## <a name="example"></a>Příklad

Další informace najdete v tématu [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Viz také

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
