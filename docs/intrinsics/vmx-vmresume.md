---
title: __vmx_vmresume
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmresume
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
ms.openlocfilehash: 34d0e6814dd00da07076e644513400bd5be36bd3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219449"
---
# <a name="__vmx_vmresume"></a>__vmx_vmresume

**Specifické pro společnost Microsoft**

Obnoví VMX nekořenovou operaci pomocí aktuální struktury řízení virtuálních počítačů (VMCS).

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmresume(
   void);
```

## <a name="return-value"></a>Návratová hodnota

|Value|Význam|
|-----------|-------------|
|0|Operace byla úspěšná.|
|1|Operace se nezdařila s rozšířeným stavem dostupným v `VM-instruction error field` aktuálním VMCS.|
|2|Operace se nezdařila bez dostupného stavu.|

## <a name="remarks"></a>Poznámky

Aplikace může provést operaci zadání virtuálního počítače pomocí funkce [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) nebo `__vmx_vmresume` . Funkci lze použít pouze s VMCS, jejíž stav spuštění je `Clear`, a `__vmx_vmresume` funkci lze použít pouze s VMCS, jejichž stav spuštění je `Launched`. `__vmx_vmlaunch` V důsledku toho použijte funkci [__vmx_vmclear](../intrinsics/vmx-vmclear.md) k nastavení stavu spuštění VMCS na `Clear` `__vmx_vmlaunch` a pak použijte funkci pro `__vmx_vmresume` první operaci s virtuálním počítačem a funkci pro následné operace zadání virtuálního počítače.

Funkce je ekvivalentní `VMRESUME` instrukci počítače. `__vmx_vmresume` Tato funkce podporuje interakci monitorování virtuálního počítače hostitele s hostovaným operačním systémem a jeho aplikacemi. Další informace najdete v dokumentu PDF "Technická specifikace virtualizace Intel pro architekturu IA-32 Intel," číslo dokumentu C97063-002, na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__vmx_vmresume`|x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
