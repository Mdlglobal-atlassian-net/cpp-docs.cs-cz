---
title: __vmx_vmptrld | Microsoft Docs
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
ms.openlocfilehash: 599e15414a944602ee196f3910a1c5dd561c906d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld
**Konkrétní Microsoft**  
  
 Načte ukazatel na strukturu aktuální ovládací prvek virtuálního počítače (VMCS) ze zadané adresy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int __vmx_vmptrld(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v] *`VmcsPhysicalAddress`  
 Adresa se uloží VMCS ukazatele.  
  
## <a name="return-value"></a>Návratová hodnota  
 0  
 Operace byla úspěšná.  
  
 1  
 Operace se nezdařila s rozšířené stavu k dispozici v `VM-instruction error field` z aktuální VMCS.  
  
 2  
 Operace se nezdařila bez stavu k dispozici.  
  
## <a name="remarks"></a>Poznámky  
 Ukazatel VMCS je 64-bit fyzickou adresu.  
  
 `__vmx_vmptrld` Funkce je ekvivalentní volání `VMPTRLD` počítač instrukcí. Tato funkce podporuje interakci monitorování virtuální počítač na hostitele s hostovaného operačního systému a jeho aplikace. Další informace vyhledejte dokumentu "Intel technické specifikace pro the IA-32 Intel architektura virtualizace," dokumentu číslo C97063-002, na [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__vmx_vmptrld`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)