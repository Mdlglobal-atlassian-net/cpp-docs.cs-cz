---
title: _aligned_recalloc
ms.date: 11/04/2016
apiname:
- _aligned_recalloc
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
- aligned_recalloc
- _aligned_recalloc
helpviewer_keywords:
- aligned_recalloc function
- _aligned_recalloc function
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
ms.openlocfilehash: ce505c5a389d4ff6aa12a88bfc47fb0a6f026eea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623688"
---
# <a name="alignedrecalloc"></a>_aligned_recalloc

Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md) a inicializuje přidělenou paměť na hodnotu 0.

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

*memblock*<br/>
Aktuální ukazatel bloku paměti.

*Číslo*<br/>
Počet prvků.

*Velikost*<br/>
Velikost v bajtech každého prvku.

*Zarovnání*<br/>
Hodnota zarovnání, které musí být celočíselnou mocninou 2.

## <a name="return-value"></a>Návratová hodnota

**_aligned_recalloc –** vrací neplatný ukazatel na blok paměti a nevyčerpané prostředky se (může být přesunutý). Vrácená hodnota je **NULL** Pokud velikost je nula a argument vyrovnávací paměti není **NULL**, nebo pokud není k dispozici dostatek paměti a rozbalte bloku na danou velikost. V prvním případě původní blok je uvolněn. V druhém případě je beze změny původního bloku. Návratová hodnota odkazuje na prostor úložiště, která je zaručeně jako vhodně zarovnaný pro úložiště libovolného typu objektu. K získání ukazatele na typ jiný než void, použijte přetypování typu na návratovou hodnotu.

Jedná se o chybu znovu přidělit paměti a změnit zarovnání do bloku.

## <a name="remarks"></a>Poznámky

**_aligned_recalloc –** vychází **malloc**. Další informace o používání **_aligned_offset_malloc –**, naleznete v tématu [malloc](malloc.md).

Tato funkce nastaví **errno** k **ENOMEM** Pokud přidělení paměti se nezdařilo nebo pokud byla větší než požadovaná velikost **_heap_maxreq –**. Další informace o **errno**, naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc **_aligned_recalloc –** ověří jeho parametry. Pokud *zarovnání* není mocninou čísla 2, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrací **NULL** a nastaví **errno** k **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_recalloc**|\<malloc.h >|

## <a name="see-also"></a>Viz také:

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
