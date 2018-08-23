---
title: _zakázat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _disable_cpp
- _disable
dev_langs:
- C++
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2748d0412c9ee0f7e7684d35a38f3c2b5d133754
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465406"
---
# <a name="disable"></a>_disable
**Specifické pro Microsoft**  
  
 Zakáže přerušení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _disable(void);  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`_disable`|x86, ARM, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `_disable` dává pokyn Vymazat příznak přerušení procesoru. Na x86 systémy, tato funkce generuje Vymazat příznak přerušení (`cli`) instrukce.  
  
 Tato funkce je pouze k dispozici v režimu jádra. Pokud použity v uživatelském režimu, je vyvolána výjimka Privilegovaná instrukce v době běhu.  
  
 Na platformách ARM se tato rutina je k dispozici pouze jako vnitřní.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)