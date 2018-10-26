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
ms.openlocfilehash: 16a61578b7512c1d9ce9d7ca217b29a3ea670657
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068486"
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

### <a name="parameters"></a>Parametry

*VmcsPhysicalAddress*<br/>
[in] Adresa ukazatele VMCS se mají ukládat.

## <a name="return-value"></a>Návratová hodnota

0<br/>
Operace byla úspěšná.

1<br/>
Operace se nezdařila s rozšířenou stav k dispozici v `VM-instruction error field` z aktuální VMCS.

2<br/>
Operace selhala, aniž by k dispozici.

## <a name="remarks"></a>Poznámky

Ukazatel VMCS je 64-bit fyzickou adresu.

`__vmx_vmptrld` Funkce je ekvivalentní volání `VMPTRLD` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace, hledání dokumentů "Intel Virtualization technické specifikace pro the architekturou IA-32 Intel," dokumentu C97063-002 čísla na [společnosti Intel Corporation](https://software.intel.com/articles/intel-sdm) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__vmx_vmptrld`|x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)