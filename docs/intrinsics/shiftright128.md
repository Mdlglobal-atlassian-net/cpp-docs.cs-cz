---
title: __shiftright128 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __shiftright128
dev_langs:
- C++
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15c166f51e8d512dd0c5ef8d98bf1e6cf991664f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714204"
---
# <a name="shiftright128"></a>__shiftright128
**Specifické pro Microsoft**  
  
 Množství 128-bit, vyjádřené dvě veličiny 64-bit posune `LowPart` a `HighPart`, vpravo o počet bitů určený `Shift` a vrátí nízké 64 bitů výsledku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __shiftright128(   
   unsigned __int64 LowPart,   
   unsigned __int64 HighPart,   
   unsigned char Shift   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*LowPart*<br/>
[in] Nízká 64 bitů množství 128 bitů a posunutí.  
  
*HighPart*<br/>
[in] Vysoká 64 bitů množství 128 bitů a posunutí.  
  
*SHIFT*<br/>
[in] Počet bitů na posunu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nízká 64 bitů výsledku.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__shiftright128`|x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `Shift` Hodnota je vždy modulo 64 tak, že, například při volání `__shiftright128(0, 1, 64)`, funkce změní horní část `0` bits klikněte pravým tlačítkem myši a vrátí dolní část z `0` a ne `1` jako jinak lze očekávat.  
  
## <a name="example"></a>Příklad  
 Příklad najdete v tématu [__shiftleft128](../intrinsics/shiftleft128.md).  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [__shiftleft128](../intrinsics/shiftleft128.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)