---
title: _aligned_offset_realloc – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_realloc function
- _aligned_offset_realloc function
ms.assetid: e0263533-991e-41b0-acc9-1b8a51ab9ecd
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f3945497a0d9ff710516d1353a9fab7b7d2f8309
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="alignedoffsetrealloc"></a>_aligned_offset_realloc

Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md).

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
Zarovnání hodnota, která musí být celé číslo mocninou 2.

*Posun*<br/>
Posun do přidělení paměti vynutit zarovnání.

## <a name="return-value"></a>Návratová hodnota

**_aligned_offset_realloc –** vrací neplatný ukazatel k opětovnému přidělení (a případně přesouvat) paměti bloku. Vrácená hodnota je **NULL** Pokud velikost je nula a argument vyrovnávací paměti není **NULL**, nebo pokud není k dispozici dostatek paměti k rozšíření bloku na danou velikost. V prvním případě původní blok uvolněno. V druhém případě je původní blok beze změny. Návratová hodnota odkazuje na prostor úložiště, který zaručeně vhodně zarovnána pro ukládání jakéhokoli typu objektu. Získání ukazatele na typ než void, použijte typ přetypovat na návratovou hodnotu.

**_aligned_offset_realloc –** je označena `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce záruku, že nechcete upravit globální proměnné a že má ukazatel vrátí není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).

## <a name="remarks"></a>Poznámky

Jako [_aligned_offset_malloc –](aligned-offset-malloc.md), **_aligned_offset_realloc –** umožňuje struktura zarovnána na posun v rámci struktury.

**_aligned_offset_realloc –** je založena na **malloc –**. Další informace o používání **_aligned_offset_malloc –**, najdete v části [malloc –](malloc.md). Pokud *memblock* je **NULL**, volání funkce **_aligned_offset_malloc –** interně.

Tato funkce nastaví **errno** k **enomem –** Pokud přidělení paměti se nezdařilo nebo pokud byla větší než požadovaná velikost **_heap_maxreq –**. Další informace o **errno**, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc **_aligned_offset_realloc –** ověří jeho parametry. Pokud *zarovnání* není mocninou 2 nebo, pokud *posun* je větší než nebo rovno *velikost* a nenulové hodnoty, tato funkce volá neplatný parametr obslužnou rutinu, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu **NULL** a nastaví **errno** k **einval –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_offset_realloc**|\<malloc.h >|

## <a name="example"></a>Příklad

Další informace najdete v tématu [_aligned_malloc –](aligned-malloc.md).

## <a name="see-also"></a>Viz také

[Zarovnání dat](../../c-runtime-library/data-alignment.md)<br/>
