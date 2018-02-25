---
title: __shiftright128 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __shiftright128
dev_langs:
- C++
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 56fbd52709addbba414d6c6fc839baf96f0b2c02
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="shiftright128"></a>__shiftright128
**Microsoft Specific**  
  
 Posune množství 128-bit, vyjádřené dvě počty 64-bit `LowPart` a `HighPart`, vpravo podle počtu bitů určeného `Shift` a vrátí nízkou 64bitová verze výsledku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __shiftright128(   
   unsigned __int64 LowPart,   
   unsigned __int64 HighPart,   
   unsigned char Shift   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `LowPart`  
 Nízkou 64bitová verze množství 128-bit se posunou.  
  
 [in] `HighPart`  
 Vysoká 64bitová verze množství 128-bit se posunou.  
  
 [in] `Shift`  
 Počet bitů se posunou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nízkou 64bitová verze výsledku.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__shiftright128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `Shift` Hodnota je vždycky modulo 64, která, například při volání `__shiftright128(0, 1, 64)`, funkce se posunutí horní část `0` bitů doprava a vrátit nízkou součástí `0` a není `1` jinak může být správně.  
  
## <a name="example"></a>Příklad  
 Příklad, naleznete v části [__shiftleft128](../intrinsics/shiftleft128.md).  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__shiftleft128](../intrinsics/shiftleft128.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)