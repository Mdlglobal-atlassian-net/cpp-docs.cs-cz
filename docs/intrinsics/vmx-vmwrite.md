---
title: __vmx_vmwrite | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __vmx_vmwrite
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08cd68256e1219df36ce6f9ea22165938fba44af
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite
**Microsoft Specific**  
  
 Zapíše zadaná hodnota v zadaném poli Aktuální struktura řízení virtuálního počítače (VMCS).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __vmx_vmwrite(   
   size_t Field,  
   size_t FieldValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[in] `Field`|Pole VMCS k zápisu.|  
|[in] `FieldValue`|Hodnota k zápisu do pole VMCS.|  
  
## <a name="return-value"></a>Návratová hodnota  
 0  
 Operace byla úspěšná.  
  
 1  
 Operace se nezdařila s rozšířené stavu k dispozici v `VM-instruction error field` z aktuální VMCS.  
  
 2  
 Operace se nezdařila bez stavu k dispozici.  
  
## <a name="remarks"></a>Poznámky  
 `__vmx_vmwrite` Funkce je ekvivalentní volání `VMWRITE` počítač instrukcí. Hodnota `Field` parametr je indexu kódovaného pole, která je popsána v dokumentaci Intel. Další informace vyhledejte dokumentu "Intel technické specifikace pro the IA-32 Intel architektura virtualizace," dokumentu číslo C97063-002, na [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality a pak zjistěte příloha C této dokument.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__vmx_vmwrite`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmread](../intrinsics/vmx-vmread.md)