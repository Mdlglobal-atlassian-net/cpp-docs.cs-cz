---
title: __svm_vmsave | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_vmsave
dev_langs:
- C++
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54cc51ee320c6b942c3ff0563f293cf48d1c34db
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465656"
---
# <a name="svmvmsave"></a>__svm_vmsave
**Specifické pro Microsoft**  
  
 Uloží podmnožinu stav procesoru řídicí blok zadaný virtuální počítač (VMCB).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_vmsave(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[in] `VmcbPhysicalAddress`|Fyzickou adresu VMCB.|  
  
## <a name="remarks"></a>Poznámky  
 `__svm_vmsave` Funkce je ekvivalentní volání `VMSAVE` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "programátor architektury AMD64 ruční svazek 2: programování systému" dokument s číslem 24593, revize 3.11 nebo novější, na [AMD Corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__svm_vmsave`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmrun](../intrinsics/svm-vmrun.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)