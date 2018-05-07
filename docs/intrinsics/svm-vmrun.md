---
title: __svm_vmrun | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_vmrun
dev_langs:
- C++
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bce7d2bef75c7fba88c986d22e95d3ab40ba652
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="svmvmrun"></a>__svm_vmrun
**Konkrétní Microsoft**  
  
 Spustí provádění kódu hosta virtuálního počítače, který odpovídá řídicí blok zadaný virtuální počítač (VMCB).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_vmrun(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `VmcbPhysicalAddress`|Fyzickou adresu VMCB.|  
  
## <a name="remarks"></a>Poznámky  
 `__svm_vmrun` Funkce používá minimální množství informací VMCB zahájíte provádění kódu hosta virtuálního počítače. Použití [__svm_vmsave](../intrinsics/svm-vmsave.md) nebo [__svm_vmload](../intrinsics/svm-vmload.md) fungovat, pokud potřebujete další informace pro zpracování komplexní přerušení nebo přepnout do jiného hosta.  
  
 `__svm_vmrun` Funkce je ekvivalentní volání `VMRUN` počítač instrukcí. Tato funkce podporuje interakci monitorování virtuální počítač na hostitele s hostovaného operačního systému a jeho aplikace. Další informace naleznete v dokumentu "programátory architektura AMD64 ruční svazku 2: programování systému" číslem 24593, revize 3.11 nebo novější, na [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__svm_vmrun`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)