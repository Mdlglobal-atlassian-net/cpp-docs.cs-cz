---
title: _aligned_offset_realloc
ms.date: 11/04/2016
apiname:
- _aligned_offset_realloc
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
- aligned_offset_realloc
- _aligned_offset_realloc
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
ms.openlocfilehash: d5f87f9bdfff262826b8d4cc4da86069588cf9db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341454"
---
# <a name="alignedoffsetrealloc"></a>_aligned_offset_realloc

Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md).

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

*Velikost*<br/>
Velikost přidělení paměti.

*Zarovnání*<br/>
Hodnota zarovnání, které musí být celočíselnou mocninou 2.

*Posun*<br/>
Posun na přidělení paměti pro vynucení zarovnání.

## <a name="return-value"></a>Návratová hodnota

**_aligned_offset_realloc –** vrací neplatný ukazatel na blok paměti a nevyčerpané prostředky se (může být přesunutý). Vrácená hodnota je **NULL** Pokud velikost je nula a argument vyrovnávací paměti není **NULL**, nebo pokud není k dispozici dostatek paměti a rozbalte bloku na danou velikost. V prvním případě původní blok je uvolněn. V druhém případě je beze změny původního bloku. Návratová hodnota odkazuje na prostor úložiště, která je zaručeně jako vhodně zarovnaný pro úložiště libovolného typu objektu. K získání ukazatele na typ jiný než void, použijte přetypování typu na návratovou hodnotu.

**_aligned_offset_realloc –** je označen `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce je zaručeno, že neupraví globální proměnné a Vrácený ukazatel není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).

## <a name="remarks"></a>Poznámky

Stejně jako [_aligned_offset_malloc –](aligned-offset-malloc.md), **_aligned_offset_realloc –** umožňuje struktura zarovnaný na posunu v rámci struktury.

**_aligned_offset_realloc –** vychází **malloc**. Další informace o používání **_aligned_offset_malloc –**, naleznete v tématu [malloc](malloc.md). Pokud *memblock* je **NULL**, volání funkce **_aligned_offset_malloc –** interně.

Tato funkce nastaví **errno** k **ENOMEM** Pokud přidělení paměti se nezdařilo nebo pokud byla větší než požadovaná velikost **_heap_maxreq –**. Další informace o **errno**, naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc **_aligned_offset_realloc –** ověří jeho parametry. Pokud *zarovnání* není mocninou čísla 2 nebo, pokud *posun* je větší než nebo rovna hodnotě *velikost* a nenulovou hodnotu, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrací **NULL** a nastaví **errno** k **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<malloc.h>|

## <a name="example"></a>Příklad

Další informace najdete v tématu [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Viz také:

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
