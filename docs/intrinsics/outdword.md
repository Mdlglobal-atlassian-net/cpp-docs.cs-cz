---
title: __outdword | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outdword
dev_langs:
- C++
helpviewer_keywords:
- out instruction
- outdword instruction
- __outdword intrinsic
ms.assetid: ed1e4994-a84b-4759-8bf9-cd48fb073f4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 326ebeeb1d282950ed7d481014d4349c168dc897
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465671"
---
# <a name="outdword"></a>__outdword
**Specifické pro Microsoft**  
  
 Generuje `out` pokyn k odeslání doubleword `Data` z portu `Port`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __outdword(   
   unsigned short Port,   
   unsigned long Data   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Port`  
 Port pro odesílání dat na.  
  
 [in] `Data`  
 Doubleword k odeslání.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__outdword`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tato rutina je k dispozici pouze jako vnitřní objekt.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)