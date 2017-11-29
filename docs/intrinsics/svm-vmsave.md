---
title: __svm_vmsave | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __svm_vmsave
dev_langs: C++
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 49f0f2bc2446c45c394daa9a4ec1e8c0a6278c83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="svmvmsave"></a>__svm_vmsave
**Konkrétní Microsoft**  
  
 Ukládá podmnožinu stav procesoru v řídicí blok zadaný virtuální počítač (VMCB).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_vmsave(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`VmcbPhysicalAddress`|Fyzickou adresu VMCB.|  
  
## <a name="remarks"></a>Poznámky  
 `__svm_vmsave` Funkce je ekvivalentní volání `VMSAVE` počítač instrukcí. Tato funkce podporuje interakci monitorování virtuální počítač na hostitele s hostovaného operačního systému a jeho aplikace. Další informace naleznete v dokumentu "programátory architektura AMD64 ruční svazku 2: programování systému" číslem 24593, revize 3.11 nebo novější, na [AMD Corporation](http://go.microsoft.com/fwlink/?LinkId=23746) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__svm_vmsave`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmrun](../intrinsics/svm-vmrun.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)