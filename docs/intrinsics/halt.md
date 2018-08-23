---
title: __halt | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __halt
- __halt_cpp
dev_langs:
- C++
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 007b3be0fc26d9a011d961540f9dc4057498b137
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465478"
---
# <a name="halt"></a>__halt
**Specifické pro Microsoft**  
  
 Mikroprocesoru zastaví, dokud nenastane povoleno přerušení, nemaskovatelné přerušení (NMI) nebo obnovení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __halt( void );  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__halt`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `__halt` Funkce je ekvivalentní volání `HLT` strojové instrukce a je k dispozici pouze v režimu jádra. Další informace vyhledejte dokument, "ruční architektury Intel softwarový vývojář, svazek 2: odkaz na sadu instrukcí," na [společnosti Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)