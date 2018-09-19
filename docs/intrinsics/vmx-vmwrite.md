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
ms.openlocfilehash: 1a3a503528f5e12fbfafab8cb8e71711ba0650c6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396841"
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
|*Pole*|[in] Pole VMCS k zápisu.|
|*FieldValue*|[in] Hodnota k zápisu do příslušného pole VMCS.|

## <a name="return-value"></a>Návratová hodnota

0 je operace úspěšná.

1 operace selhala kvůli rozšířené stav k dispozici v `VM-instruction error field` z aktuální VMCS.

2 operace se nezdařila, aniž by k dispozici.

## <a name="remarks"></a>Poznámky

`__vmx_vmwrite` Funkce je ekvivalentní volání `VMWRITE` strojové instrukce. Hodnota `Field` parametr je kódovaný pole index, který je popsán v dokumentaci k Intel. Další informace, hledání dokumentů "Intel Virtualization technické specifikace pro the architekturou IA-32 Intel," dokumentu C97063-002 čísla na [společnosti Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokality a pak naleznete v dodatku C, který dokument.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__vmx_vmwrite`|x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmread](../intrinsics/vmx-vmread.md)