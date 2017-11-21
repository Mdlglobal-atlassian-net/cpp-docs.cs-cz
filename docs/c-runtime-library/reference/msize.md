---
title: "_msize – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _msize
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
- msize
- _msize
dev_langs: C++
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e678d5ba1abcf552fa5e4576578a5a220fe50f8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="msize"></a>_msize
Vrátí velikost bloku paměti přidělené v haldě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      size_t _msize(  
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Ukazatel na oblast paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_msize`Vrátí velikost (v bajtech) jako celé číslo bez znaménka.  
  
## <a name="remarks"></a>Poznámky  
 `_msize` Funkce vrátí velikost v bajtech bloku paměti přidělené voláním `calloc`, `malloc`, nebo `realloc`.  
  
 Když aplikace je spojená s verzí ladicí běhové knihovny jazyka C, `_msize` přeloží na [_msize_dbg –](../../c-runtime-library/reference/msize-dbg.md). Další informace o spravováni haldě ladění během najdete v tématu [haldy ladění The CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Tato funkce ověří jeho parametru. Pokud `memblock` je ukazatel s hodnotou null, `_msize` vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud se zpracovává chyby, nastaví funkci `errno` k `EINVAL` a vrátí hodnotu -1.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_msize`|\<malloc.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [realloc –](../../c-runtime-library/reference/realloc.md).  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [calloc –](../../c-runtime-library/reference/calloc.md)   
 [_rozšířit lokalitu](../../c-runtime-library/reference/expand.md)   
 [malloc –](../../c-runtime-library/reference/malloc.md)   
 [realloc –](../../c-runtime-library/reference/realloc.md)