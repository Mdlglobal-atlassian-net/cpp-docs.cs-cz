---
title: Zarovnání dat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- data.alignment
dev_langs:
- C++
helpviewer_keywords:
- data alignment [C++]
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f336e13efeea356743d7905317011cd31f96730
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="data-alignment"></a>Zarovnání dat

Následující funkce C Runtime podporují zarovnání dat.

## <a name="data-alignment-routines"></a>Zarovnání dat rutiny

|Rutina|Použití|
|-------------|---------|
|[_aligned_free](../c-runtime-library/reference/aligned-free.md)|Uvolní blok paměti, který byl přidělen s [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md)nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_free_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|Uvolní blok paměti, který byl přidělen s [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) (pouze ladění).|
|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)|Přidělí paměť na hranici zadané zarovnání.|
|[_aligned_malloc_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|Přidělí paměť na hranici zadané zarovnání s další prostor pro ladění hlavičky a přepsání vyrovnávací paměti (pouze ladicí verze).|
|[_aligned_msize](../c-runtime-library/reference/aligned-msize.md)|Vrátí velikost bloku paměti přidělené v haldě.|
|[_aligned_msize_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|Vrátí velikost bloku paměti přidělené v haldě (pouze ladicí verze).|
|[_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|Přidělí paměť na hranici zadané zarovnání.|
|[_aligned_offset_malloc_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|Přidělí paměť na hranici zadané zarovnání (pouze ladicí verze).|
|[_aligned_offset_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_offset_realloc_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) (pouze ladicí verze).|
|[_aligned_offset_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) a inicializuje paměť na 0.|
|[_aligned_offset_recalloc_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) a inicializuje paměť na hodnotu 0 (pouze ladicí verze).|
|[_aligned_realloc](../c-runtime-library/reference/aligned-realloc.md)|Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md).|
|[_aligned_realloc_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) (pouze ladicí verze).|
|[_aligned_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) a inicializuje paměť na 0.|
|[_aligned_recalloc_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../c-runtime-library/reference/aligned-offset-malloc.md) a inicializuje paměť na hodnotu 0 (pouze ladicí verze).|

## <a name="see-also"></a>Viz také

[Univerzální C runtime rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>