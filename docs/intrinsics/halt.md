---
title: __halt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __halt
- __halt_cpp
dev_langs: C++
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03045fcda597edcf5f1e0a32da466dc40953d4f3
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="halt"></a>__halt
**Konkrétní Microsoft**  
  
 Vašem mikroprocesoru a používané zastaví, dokud nenastane povoleno přerušení, nemaskovatelné přerušení (NMI) nebo provést obnovení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __halt( void );  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__halt`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `__halt` Funkce je ekvivalentní volání `HLT` počítač instrukce a je k dispozici pouze v režimu jádra. Další informace naleznete v dokumentu "vyvíjející Software Intel architektura ruční svazku 2: odkaz na sadu instrukce," v [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)