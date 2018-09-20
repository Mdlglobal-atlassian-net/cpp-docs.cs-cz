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
ms.openlocfilehash: a7126dc3b6a0ece4a5b7627859d0b80abf962d88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429099"
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

[in] *`VmcsPhysicalAddress` adresa ukazatele VMCS se mají ukládat.

## <a name="return-value"></a>Návratová hodnota

0 je operace úspěšná.

1 operace selhala kvůli rozšířené stav k dispozici v `VM-instruction error field` z aktuální VMCS.

2 operace se nezdařila, aniž by k dispozici.

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

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)