---
title: __vmx_vmptrst | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrst
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e879726f9ef3ad65dabd00056ddb859c72dd039e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679564"
---
# <a name="vmxvmptrst"></a>__vmx_vmptrst
**Specifické pro Microsoft**  
  
 Ukládá ukazatel na aktuální struktura řízení virtuálních počítačů (VMCS) na zadané adrese.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __vmx_vmptrst(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] *`VmcsPhysicalAddress`  
 Adresa aktuální ukazatel VMCS se mají ukládat.  
  
## <a name="remarks"></a>Poznámky  
 Ukazatel VMCS je 64-bit fyzickou adresu.  
  
 `__vmx_vmptrst` Funkce je ekvivalentní volání `VMPTRST` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace, hledání dokumentů "Intel Virtualization technické specifikace pro the architekturou IA-32 Intel," dokumentu C97063-002 čísla na [společnosti Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__vmx_vmptrst`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)