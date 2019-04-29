---
title: __vmx_vmresume
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmresume
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
ms.openlocfilehash: d2bfe9a8f98b8a03a82768177217d70674708c39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390006"
---
# <a name="vmxvmresume"></a>__vmx_vmresume

**Microsoft Specific**

Obnoví VMX nekořenovými operace pomocí aktuální řídicí struktura virtuálního počítače (VMCS).

## <a name="syntax"></a>Syntaxe

```
unsigned char __vmx_vmresume(
   void);
```

## <a name="return-value"></a>Návratová hodnota

|Value|Význam|
|-----------|-------------|
|0|Operace byla úspěšná.|
|1|Operace se nezdařila s rozšířenou stav k dispozici v `VM-instruction error field` z aktuální VMCS.|
|2|Operace selhala, aniž by k dispozici.|

## <a name="remarks"></a>Poznámky

Aplikace může provádět operace, která virtuálního počítače zadejte buď pomocí [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) nebo `__vmx_vmresume` funkce. `__vmx_vmlaunch` Funkci lze použít pouze s VMCS, jehož stav spuštění je `Clear`a `__vmx_vmresume` funkci lze použít pouze s VMCS, jehož stav spuštění je `Launched`. V důsledku toho použít [__vmx_vmclear](../intrinsics/vmx-vmclear.md) funkce pro nastavení stavu spuštění VMCS k `Clear`a pak použít `__vmx_vmlaunch` funkce pro první operace virtuálního počítače zadejte a `__vmx_vmresume` funkce pro následné zadejte virtuální počítač operace.

`__vmx_vmresume` Funkce je ekvivalentní volání `VMRESUME` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace, vyhledejte dokument PDF "Intel Virtualization technické specifikace pro the architekturou IA-32 Intel," dokumentu C97063-002 čísla na [společnosti Intel Corporation](https://software.intel.com/articles/intel-sdm) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__vmx_vmresume`|x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)<br/>
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)