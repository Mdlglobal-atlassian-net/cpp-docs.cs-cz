---
title: __vmx_vmread | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmread
dev_langs:
- C++
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81feddd403c96d0b3f9402aaa744d0c79dbec21e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="vmxvmread"></a>__vmx_vmread
**Konkrétní Microsoft**  
  
 Čte zadané pole z aktuální struktura řízení virtuálního počítače (VMCS) a umístí jej do zadaného umístění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __vmx_vmread(  
   size_t Field,  
   size_t *FieldValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `Field`|Pole VMCS ke čtení.|  
|[v] `FieldValue`|Ukazatel na umístění k uložení hodnota číst z pole VMCS určeného `Field` parametr.|  
  
## <a name="return-value"></a>Návratová hodnota  
  
|Hodnota|Význam|  
|-----------|-------------|  
|0|Operace byla úspěšná.|  
|1|Operace se nezdařila s rozšířené stavu k dispozici v `VM-instruction error field` z aktuální VMCS.|  
|2|Operace se nezdařila bez stavu k dispozici.|  
  
## <a name="remarks"></a>Poznámky  
 `__vmx_vmread` Funkce je ekvivalentní volání `VMREAD` počítač instrukcí. Hodnota `Field` parametr je indexu kódovaného pole, která je popsána v dokumentaci Intel. Další informace vyhledejte dokumentu "Intel technické specifikace pro the IA-32 Intel architektura virtualizace," dokumentu C97063-002 číslo na [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality a pak najdete příloha C tohoto dokumentu .  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__vmx_vmread`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)