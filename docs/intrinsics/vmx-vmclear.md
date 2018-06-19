---
title: __vmx_vmclear | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmclear
dev_langs:
- C++
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8da1e3d2c5b1a2018df0e46f085fede9b923fff8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332407"
---
# <a name="vmxvmclear"></a>__vmx_vmclear
**Konkrétní Microsoft**  
  
 Inicializuje strukturu řízení zadaný virtuální počítač (VMCS) a nastaví její stav spuštění `Clear`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __vmx_vmclear(  
   unsigned __int64 *VmcsPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `VmcsPhysicalAddress`|Ukazatel na 64-bit paměti umístění, které obsahuje fyzickou adresu VMCS zrušte.|  
  
## <a name="return-value"></a>Návratová hodnota  
  
|Hodnota|Význam|  
|-----------|-------------|  
|0|Operace byla úspěšná.|  
|1|Operace se nezdařila s rozšířené stavu k dispozici v `VM-instruction error field` z aktuální VMCS.|  
|2|Operace se nezdařila bez stavu k dispozici.|  
  
## <a name="remarks"></a>Poznámky  
 Aplikace můžete provést operaci virtuálního počítače zadejte buď pomocí [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) nebo [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkce. [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkci lze použít pouze s VMCS, jejichž stav spuštění je `Clear`a [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkci lze použít pouze s VMCS, jejichž stav spuštění je `Launched`. V důsledku toho použít [__vmx_vmclear](../intrinsics/vmx-vmclear.md) funkce pro nastavení stavu spuštění VMCS k `Clear`. Použití [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkce pro první operaci zadejte virtuální počítač a [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkce pro následující operace zadejte virtuální počítač.  
  
 `__vmx_vmclear` Funkce je ekvivalentní volání `VMCLEAR` počítač instrukcí. Tato funkce podporuje interakci monitorování virtuální počítač na hostitele s hostovaného operačního systému a jeho aplikace. Další informace vyhledejte dokumentu "Intel technické specifikace pro the IA-32 Intel architektura virtualizace," dokumentu číslo C97063-002, na [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__vmx_vmclear`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [__vmx_vmresume](../intrinsics/vmx-vmresume.md)