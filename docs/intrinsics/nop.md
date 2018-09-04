---
title: __nop | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __nop
dev_langs:
- C++
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 507f00b82a407b84d374d5f7b9fad8d29101a848
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682095"
---
# <a name="nop"></a>__nop
**Specifické pro Microsoft**  
  
 Generuje pro konkrétní platformu strojového kódu, který neprovádí operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __nop();  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__nop`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Specifické pro END Microsoft**  
  
## <a name="remarks"></a>Poznámky  
 `__nop` Funkce je ekvivalentní volání `NOP` strojové instrukce. Další informace vyhledejte dokument, "ruční architektury Intel softwarový vývojář, svazek 2: odkaz na sadu instrukcí," na [společnosti Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokality.  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__noop](../intrinsics/noop.md)