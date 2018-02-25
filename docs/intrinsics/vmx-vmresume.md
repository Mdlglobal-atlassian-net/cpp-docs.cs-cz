---
title: __vmx_vmresume | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __vmx_vmresume
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f7c35842c0e51b519e474378436c66a406ff80b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="vmxvmresume"></a>__vmx_vmresume
**Microsoft Specific**  
  
 Obnoví VMX nekořenovými operace s použitím aktuální struktury řízení virtuálního počítače (VMCS).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __vmx_vmresume(  
   void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
  
|Hodnota|Význam|  
|-----------|-------------|  
|0|Operace byla úspěšná.|  
|1|Operace se nezdařila s rozšířené stavu k dispozici v `VM-instruction error field` z aktuální VMCS.|  
|2|Operace se nezdařila bez stavu k dispozici.|  
  
## <a name="remarks"></a>Poznámky  
 Aplikace můžete provést operaci virtuálního počítače zadejte buď pomocí [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) nebo `__vmx_vmresume` funkce. `__vmx_vmlaunch` Funkci lze použít pouze s VMCS, jejichž stav spuštění je `Clear`a `__vmx_vmresume` funkci lze použít pouze s VMCS, jejichž stav spuštění je `Launched`. V důsledku toho použít [__vmx_vmclear](../intrinsics/vmx-vmclear.md) funkce pro nastavení stavu spuštění VMCS k `Clear`a potom `__vmx_vmlaunch` funkce pro první operaci zadejte virtuální počítač a `__vmx_vmresume` funkce pro následné zadejte virtuální počítač operace.  
  
 `__vmx_vmresume` Funkce je ekvivalentní volání `VMRESUME` počítač instrukcí. Tato funkce podporuje interakci monitorování virtuální počítač na hostitele s hostovaného operačního systému a jeho aplikace. Další informace, vyhledejte dokument PDF, "Intel technické specifikace pro the IA-32 Intel architektura virtualizace," dokumentu C97063-002 číslo na [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__vmx_vmresume`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [__vmx_vmclear](../intrinsics/vmx-vmclear.md)