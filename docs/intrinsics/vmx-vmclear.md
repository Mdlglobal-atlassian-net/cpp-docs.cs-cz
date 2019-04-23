---
title: __vmx_vmclear
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmclear
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
ms.openlocfilehash: 17e3e5c91a58894b25fc6b2a72f7d0056fa88119
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036534"
---
# <a name="vmxvmclear"></a>__vmx_vmclear

**Microsoft Specific**

Inicializuje struktury řízení zadaný virtuální počítač (VMCS) a nastaví její stav spuštění na `Clear`.

## <a name="syntax"></a>Syntaxe

```
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*VmcsPhysicalAddress*|[in] Ukazatel na umístění paměti 64-bit, který obsahuje fyzickou adresu VMCS zrušte.|

## <a name="return-value"></a>Návratová hodnota

|Hodnota|Význam|
|-----------|-------------|
|0|Operace byla úspěšná.|
|1|Operace se nezdařila s rozšířenou stav k dispozici v `VM-instruction error field` z aktuální VMCS.|
|2|Operace selhala, aniž by k dispozici.|

## <a name="remarks"></a>Poznámky

Aplikace může provádět operace, která virtuálního počítače zadejte buď pomocí [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) nebo [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkce. [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkci lze použít pouze s VMCS, jehož stav spuštění je `Clear`a [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkci lze použít pouze s VMCS, jehož stav spuštění je `Launched`. V důsledku toho použít [__vmx_vmclear](../intrinsics/vmx-vmclear.md) funkce pro nastavení stavu spuštění VMCS k `Clear`. Použití [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) funkce pro první virtuální počítač zadat operaci a [__vmx_vmresume](../intrinsics/vmx-vmresume.md) funkce pro následné operace zadejte virtuální počítač.

`__vmx_vmclear` Funkce je ekvivalentní volání `VMCLEAR` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace, hledání dokumentů "Intel Virtualization technické specifikace pro the architekturou IA-32 Intel," dokumentu C97063-002 čísla na [společnosti Intel Corporation](https://software.intel.com/articles/intel-sdm) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__vmx_vmclear`|x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)<br/>
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)