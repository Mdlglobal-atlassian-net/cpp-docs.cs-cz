---
title: _InterlockedAddLargeStatistic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
dev_langs: C++
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1d9e61abc6ac531fe489465b1d81e167bdde5242
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic
**Konkrétní Microsoft**  
  
 Provede příležitost interlocked, ve kterém je první operand hodnotu 64-bit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long _InterlockedAddLargeStatistic(  
   __int64 volatile * Addend,  
   long Value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [ve out]`Addend`  
 Ukazatel na první operand pro operace přidání. Hodnota ukazuje je nahrazena výsledek přidání.  
  
 [v]`Value`  
 Druhý operand; Hodnota k přidání do první operand.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota Druhý operand.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`_InterlockedAddLargeStatistic`|x86|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tento vnitřní není atomic vzhledem k tomu, že jsou implementované jako dva samostatné uzamčeném pokyny. Atomic 64-bit pro čtení, ke kterému dochází na jiné vlákno během provádění této vnitřní by mohla způsobit hodnotou nekonzistentní, který je čten.  
  
 Tato funkce se chová jako bariéry pro čtení a zápis. Další informace najdete v tématu [_readwritebarrier –](../intrinsics/readwritebarrier.md).  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)