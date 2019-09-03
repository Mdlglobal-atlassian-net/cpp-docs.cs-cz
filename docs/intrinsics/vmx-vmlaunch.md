---
title: __vmx_vmlaunch
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmlaunch
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
ms.openlocfilehash: 8d78e5181fdd43e10431e12d0cf540c8c9c2e719
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219550"
---
# <a name="__vmx_vmlaunch"></a>__vmx_vmlaunch

**Specifické pro společnost Microsoft**

Umístí volající aplikaci do stavu nekořenové operace VMX (zadejte virtuální počítač) pomocí aktuální struktury řízení virtuálního počítače (VMCS).

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmlaunch(void);
```

## <a name="return-value"></a>Návratová hodnota

|Value|Význam|
|-----------|-------------|
|0|Operace byla úspěšná.|
|1|Operace se nezdařila s rozšířeným stavem dostupným v `VM-instruction error field` aktuálním VMCS.|
|2|Operace se nezdařila bez dostupného stavu.|

## <a name="remarks"></a>Poznámky

Aplikace může provést operaci s virtuálním počítačem pomocí funkce [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) nebo [__vmx_vmresume](../intrinsics/vmx-vmresume.md) . Funkci [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) lze použít pouze s VMCS, jejichž stav spuštění je `Clear`, a funkci [__vmx_vmresume](../intrinsics/vmx-vmresume.md) lze použít pouze s VMCS, jejíž stav spuštění je. `Launched` V důsledku toho použijte funkci [__vmx_vmclear](../intrinsics/vmx-vmclear.md) k nastavení stavu spuštění VMCS na `Clear`a pak použijte funkci [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) pro první operaci VM-ENTER a funkci [__vmx_vmresume](../intrinsics/vmx-vmresume.md) pro další virtuální počítače – zadejte Operations.

Funkce je ekvivalentní `VMLAUNCH` instrukci počítače. `__vmx_vmlaunch` Tato funkce podporuje interakci monitorování virtuálního počítače hostitele s hostovaným operačním systémem a jeho aplikacemi. Další informace najdete v dokumentu "Technická specifikace technologie Intel Virtualization pro architekturu IA-32 Intel," číslo dokumentu C97063-002 "na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__vmx_vmlaunch`|x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
