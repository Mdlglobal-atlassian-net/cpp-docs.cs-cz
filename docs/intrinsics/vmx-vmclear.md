---
title: __vmx_vmclear
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmclear
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
ms.openlocfilehash: 3b5807402cf0a9d8a9ef1ded1d112d22a801633e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219537"
---
# <a name="__vmx_vmclear"></a>__vmx_vmclear

**Specifické pro společnost Microsoft**

Inicializuje zadanou strukturu ovládacího prvku virtuálního počítače (VMCS) a nastaví její stav spuštění na `Clear`.

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmcsPhysicalAddress*\
pro Ukazatel na umístění 64 paměti obsahující fyzickou adresu VMCS, která se má vymazat.

## <a name="return-value"></a>Návratová hodnota

|Value|Význam|
|-----------|-------------|
|0|Operace byla úspěšná.|
|1|Operace se nezdařila s rozšířeným stavem dostupným v `VM-instruction error field` aktuálním VMCS.|
|2|Operace se nezdařila bez dostupného stavu.|

## <a name="remarks"></a>Poznámky

Aplikace může provést operaci s virtuálním počítačem pomocí funkce [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) nebo [__vmx_vmresume](../intrinsics/vmx-vmresume.md) . Funkci [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) lze použít pouze s VMCS, jejichž stav spuštění je `Clear`, a funkci [__vmx_vmresume](../intrinsics/vmx-vmresume.md) lze použít pouze s VMCS, jejíž stav spuštění je. `Launched` V důsledku toho použijte funkci [__vmx_vmclear](../intrinsics/vmx-vmclear.md) k nastavení stavu spuštění VMCS na `Clear`. Použijte funkci [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) pro první operaci VM-ENTER a funkci [__vmx_vmresume](../intrinsics/vmx-vmresume.md) pro následné operace vstupu do virtuálního počítače.

Funkce je ekvivalentní `VMCLEAR` instrukci počítače. `__vmx_vmclear` Tato funkce podporuje interakci monitorování virtuálního počítače hostitele s hostovaným operačním systémem a jeho aplikacemi. Další informace najdete v dokumentu "Technická specifikace technologie Intel Virtualization pro architekturu IA-32 Intel," číslo dokumentu C97063-002 "na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__vmx_vmclear`|x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)
