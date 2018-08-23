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
ms.openlocfilehash: 1cfa38ddcd5b68c2f64e5c6d401ab0812406b51c
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465657"
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
 `__nop` Funkce je ekvivalentní volání `NOP` strojové instrukce. Další informace vyhledejte dokument, "ruční architektury Intel softwarový vývojář, svazek 2: odkaz na sadu instrukcí," na [společnosti Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality.  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__noop](../intrinsics/noop.md)