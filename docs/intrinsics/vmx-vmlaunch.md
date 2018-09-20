---
title: __vmx_vmlaunch | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmlaunch
dev_langs:
- C++
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a511a70c1f6cecd9c2a6dd489f11d5c18b655f3d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373331"
---
# <a name="vmxvmlaunch"></a>__vmx_vmlaunch

**Specifické pro Microsoft**

Umístí volající aplikace ve stavu operace nekořenovými VMX (zadejte virtuální počítač) pomocí aktuální struktury řízení virtuálních počítačů (VMCS).

## <a name="syntax"></a>Syntaxe

```
unsigned char __vmx_vmlaunch(
   void);
```

## <a name="return-value"></a>Návratová hodnota

|Hodnota|Význam|
|-----------|-------------|
|0|Operace byla úspěšná.|
|1|Operace se nezdařila s rozšířenou stav k dispozici v `VM-instruction error field` z aktuální VMCS.|
|2|Operace selhala, aniž by k dispozici.|

## <a name="remarks"></a>Poznámky

Aplikace může provádět operace, která virtuálního počítače zadejte buď pomocí [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) nebo [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkce. [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkci lze použít pouze s VMCS, jehož stav spuštění je `Clear`a [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkci lze použít pouze s VMCS, jehož stav spuštění je `Launched`. V důsledku toho použít [__vmx_vmclear](../intrinsics/vmx-vmclear.md) funkce pro nastavení stavu spuštění VMCS k `Clear`a pak použít [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkce pro první virtuální počítač zadat operaci a [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkce pro následné operace zadejte virtuální počítač.

`__vmx_vmlaunch` Funkce je ekvivalentní volání `VMLAUNCH` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace, hledání dokumentů "Intel Virtualization technické specifikace pro the architekturou IA-32 Intel," dokumentu C97063-002 čísla na [společnosti Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__vmx_vmlaunch`|x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)<br/>
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)