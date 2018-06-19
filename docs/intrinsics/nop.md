---
title: __nop | Microsoft Docs
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
ms.openlocfilehash: 25ada52595b5d811f68a05813d8df5c68d4a70c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328770"
---
# <a name="nop"></a>__nop
**Konkrétní Microsoft**  
  
 Generuje kód počítače specifické pro platformu, která provádí žádná operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __nop();  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__nop`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="remarks"></a>Poznámky  
 `__nop` Funkce je ekvivalentní volání `NOP` počítač instrukcí. Další informace naleznete v dokumentu "vyvíjející Software Intel architektura ruční svazku 2: odkaz na sadu instrukce," v [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality.  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__noop](../intrinsics/noop.md)