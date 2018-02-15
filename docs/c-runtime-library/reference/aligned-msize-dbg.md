---
title: _aligned_msize_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _aligned_msize_dbg
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
apitype: DLLExport
f1_keywords:
- _aligned_msize_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0c26a876f6ef4f77d4f9c649a3993fe666cb6f3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg
Vrátí velikost bloku paměti přidělené v haldě (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t _aligned_msize_dbg(  
   void *memblock,  
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `memblock`  
 Ukazatel na oblast paměti.  
  
 [in] `alignment`  
 Zarovnání hodnota, která musí být celé číslo mocninou 2.  
  
 [in] `offset`  
 Posun do přidělení paměti vynutit zarovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí velikost (v bajtech) jako celé číslo bez znaménka.  
  
## <a name="remarks"></a>Poznámky  
 `alignment` a `offset` hodnoty musí být stejný jako hodnoty předané funkce, která přidělené bloku.  
  
 `_aligned_msize_dbg` ladicí verze [_aligned_msize –](../../c-runtime-library/reference/aligned-msize.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání `_aligned_msize_dbg` byla snížena volání `_aligned_msize`. Obě `_aligned_msize` a `_aligned_msize_dbg` vypočítat velikost bloku paměti v haldě základní ale `_aligned_msize_dbg` přidá funkce ladění: v vrácená velikost obsahuje vyrovnávací paměti na obou stranách části uživatele bloku paměti.  
  
 Tato funkce ověří jeho parametru. Pokud `memblock` je nulový ukazatel nebo `alignment` není mocninou 2, `_msize` vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud se zpracovává chyby, nastaví funkci `errno` k `EINVAL` a vrátí hodnotu -1.  
  
 Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_aligned_msize_dbg`|\<crtdbg.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)