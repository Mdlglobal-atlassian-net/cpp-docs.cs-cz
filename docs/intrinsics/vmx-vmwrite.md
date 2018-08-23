---
title: __vmx_vmwrite | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmwrite
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec022fe2d317ec38bc1d9b06f459b9efc7818c92
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466316"
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite
**Specifické pro Microsoft**  
  
 Zapíše zadaná hodnota v zadaném poli aktuální řídicí struktura virtuálního počítače (VMCS).  
  
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
|[in] `FieldValue`|Hodnota k zápisu do příslušného pole VMCS.|  
  
## <a name="return-value"></a>Návratová hodnota  
 0  
 Operace byla úspěšná.  
  
 1  
 Operace se nezdařila s rozšířenou stav k dispozici v `VM-instruction error field` z aktuální VMCS.  
  
 2  
 Operace selhala, aniž by k dispozici.  
  
## <a name="remarks"></a>Poznámky  
 `__vmx_vmwrite` Funkce je ekvivalentní volání `VMWRITE` strojové instrukce. Hodnota `Field` parametr je kódovaný pole index, který je popsán v dokumentaci k Intel. Další informace, hledání dokumentů "Intel Virtualization technické specifikace pro the architekturou IA-32 Intel," dokumentu C97063-002 čísla na [společnosti Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokality a pak naleznete v dodatku C, který dokument.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__vmx_vmwrite`|x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmread](../intrinsics/vmx-vmread.md)