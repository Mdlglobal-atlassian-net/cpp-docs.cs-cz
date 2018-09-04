---
title: __vmx_off | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_off
dev_langs:
- C++
helpviewer_keywords:
- VMXOFF instruction
- __vmx_off intrinsic
ms.assetid: 78a32d46-9291-406c-b982-a550855aff18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 924cd8f502b6fe41aa4733df3dc59a372c27e6cb
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683632"
---
# <a name="vmxoff"></a>__vmx_off
**Specifické pro Microsoft**  
  
 Deaktivuje operace rozšíření (VMX) virtuálního počítače v procesoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __vmx_off();  
```  
  
## <a name="remarks"></a>Poznámky  
 `__vmx_off` Funkce je ekvivalentní volání `VMXOFF` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace, hledání dokumentů "Intel Virtualization technické specifikace pro the architekturou IA-32 Intel," dokumentu C97063-002 čísla na [společnosti Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__vmx_off`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)