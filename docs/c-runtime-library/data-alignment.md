---
title: Zarovnání dat
ms.date: 11/04/2016
f1_keywords:
- data.alignment
helpviewer_keywords:
- data alignment [C++]
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
ms.openlocfilehash: 92b8df81751e01e655e348d5f090705e5194312b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344522"
---
# <a name="data-alignment"></a>Zarovnání dat

Následující funkce jazyka C za běhu podporují zarovnání dat.

## <a name="data-alignment-routines"></a>Rutiny zarovnání dat

|Rutina|Použití|
|-------------|---------|
|[_aligned_free](../c-runtime-library/reference/aligned-free.md)|Uvolní blok paměti, která byla přidělena pomocí [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_free_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|Uvolní blok paměti, která byla přidělena pomocí [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) (pouze debug).|
|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)|Přidělí paměť v zadaných hranicích zarovnání.|
|[_aligned_malloc_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|Přidělí paměť v zadaných hranicích zarovnání s další místo pro ladění záhlaví a přepsat vyrovnávací paměti (pouze ladicí verze).|
|[_aligned_msize](../c-runtime-library/reference/aligned-msize.md)|Vrátí velikost bloku paměti přidělení na haldě.|
|[_aligned_msize_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|Vrátí velikost bloku paměti přiděleny do haldy (pouze ladicí verze).|
|[_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|Přidělí paměť v zadaných hranicích zarovnání.|
|[_aligned_offset_malloc_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|Přidělí paměť v zadaných hranicích zarovnání (pouze ladicí verze).|
|[_aligned_offset_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_offset_realloc_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) (pouze ladicí verze).|
|[_aligned_offset_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) a inicializuje přidělenou paměť na hodnotu 0.|
|[_aligned_offset_recalloc_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) a inicializuje přidělenou paměť na hodnotu 0 (pouze ladicí verze).|
|[_aligned_realloc](../c-runtime-library/reference/aligned-realloc.md)|Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_realloc_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) (pouze ladicí verze).|
|[_aligned_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) a inicializuje přidělenou paměť na hodnotu 0.|
|[_aligned_recalloc_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|Změní velikost bloku paměti, která byla přidělena pomocí [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) a inicializuje přidělenou paměť na hodnotu 0 (pouze ladicí verze).|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
