---
title: __wbinvd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __wbinvd
dev_langs:
- C++
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccee7703550bff7980e1cf07b30f29d284e2a3a5
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464524"
---
# <a name="wbinvd"></a>__wbinvd
**Specifické pro Microsoft**  
  
 Generuje zapisovat zpět a zneplatnění mezipaměti (`wbinvd`) instrukce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __wbinvd(void);  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__wbinvd`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je dostupná pouze v režimu jádra s úrovní oprávnění (PANELU) 0 a rutina je dostupný jenom jako vnitřní.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)