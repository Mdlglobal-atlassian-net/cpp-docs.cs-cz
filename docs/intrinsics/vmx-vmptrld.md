---
title: __vmx_vmptrld | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrld
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd04350df17b6d2dfed65526d0f7681c314f07f8
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682617"
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld
**Specifické pro Microsoft**  
  
 Načte ukazatel na aktuální struktura řízení virtuálních počítačů (VMCS) ze zadané adresy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int __vmx_vmptrld(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] *`VmcsPhysicalAddress`  
 Adresa ukazatele VMCS se mají ukládat.  
  
## <a name="return-value"></a>Návratová hodnota  
 0  
 Operace byla úspěšná.  
  
 1  
 Operace se nezdařila s rozšířenou stav k dispozici v `VM-instruction error field` z aktuální VMCS.  
  
 2  
 Operace selhala, aniž by k dispozici.  
  
## <a name="remarks"></a>Poznámky  
 Ukazatel VMCS je 64-bit fyzickou adresu.  
  
 `__vmx_vmptrld` Funkce je ekvivalentní volání `VMPTRLD` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace, hledání dokumentů "Intel Virtualization technické specifikace pro the architekturou IA-32 Intel," dokumentu C97063-002 čísla na [společnosti Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__vmx_vmptrld`|x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)