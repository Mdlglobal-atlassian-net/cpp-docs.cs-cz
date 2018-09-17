---
title: __readmsr | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readmsr
dev_langs:
- C++
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26fb2637c5a92a430d72e496cabeb8f5749ccaa1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711790"
---
# <a name="readmsr"></a>__readmsr
**Specifické pro Microsoft**  
  
 Generuje `rdmsr` instrukce, který čte register specifické pro model určený `register` a vrátí jeho hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__int64 __readmsr(   
   int register   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*Registrace*<br/>
[in] Model konkrétním registru ke čtení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota do zadaného registru.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__readmsr`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je dostupná pouze v režimu jádra a rutina je dostupný jenom jako vnitřní.  
  
 Další informace najdete v dokumentaci k AMD.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)