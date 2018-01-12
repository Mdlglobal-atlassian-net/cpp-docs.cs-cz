---
title: __vmx_on | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __vmx_on
dev_langs: C++
helpviewer_keywords:
- VMXON instruction
- __vmx_on intrinsic
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 457866d54fe3f290c40ca70b07e19ec3f337de41
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="vmxon"></a>__vmx_on
**Konkrétní Microsoft**  
  
 Aktivuje operace rozšíření (VMX) virtuálního počítače v procesoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __vmx_on(  
   unsigned __int64 *VmsSupportPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`VmsSupportPhysicalAddress`  
 Ukazatel na 64-bit fyzickou adresu, která odkazuje na virtuální počítač řídicí struktury (VMCS).  
  
## <a name="return-value"></a>Návratová hodnota  
  
|Hodnota|Význam|  
|-----------|-------------|  
|0|Operace byla úspěšná.|  
|1|Operace se nezdařila s rozšířené stavu k dispozici v `VM-instruction error field` z aktuální VMCS.|  
|2|Operace se nezdařila bez stavu k dispozici.|  
  
## <a name="remarks"></a>Poznámky  
 `__vmx_on` Funkce odpovídá `VMXON` počítač instrukcí. Tato funkce podporuje interakci monitorování virtuální počítač na hostitele s hostovaného operačního systému a jeho aplikace. Další informace vyhledejte dokumentu "Intel technické specifikace pro the IA-32 Intel architektura virtualizace," dokumentu číslo C97063-002, na [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__vmx_on`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)