---
title: __svm_vmrun | Dokumentace Microsoftu
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
ms.openlocfilehash: 3777492212bbff368902acf589f0a3c46ea4ac18
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718669"
---
# <a name="svmvmrun"></a>__svm_vmrun
**Specifické pro Microsoft**  
  
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
|*VmcbPhysicalAddress*|[in] Fyzickou adresu VMCB.|  
  
## <a name="remarks"></a>Poznámky  
 `__svm_vmrun` Funkce používá minimální množství informací VMCB zahájíte spuštěním kódu hosta virtuálního počítače. Použití [__svm_vmsave](../intrinsics/svm-vmsave.md) nebo [__svm_vmload](../intrinsics/svm-vmload.md) fungovat, pokud potřebujete další informace pro zpracování složitých přerušení nebo přepněte do jiného typu Host.  
  
 `__svm_vmrun` Funkce je ekvivalentní volání `VMRUN` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "programátor architektury AMD64 ruční svazek 2: programování systému" dokument s číslem 24593, revize 3.11 nebo novější, na [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__svm_vmrun`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)