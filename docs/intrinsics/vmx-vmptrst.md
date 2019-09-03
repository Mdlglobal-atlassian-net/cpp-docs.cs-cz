---
title: __vmx_vmptrst
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrst
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
ms.openlocfilehash: e559746be9e2a3fe5e81afa4d290265394db3e36
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219482"
---
# <a name="__vmx_vmptrst"></a>__vmx_vmptrst

**Specifické pro společnost Microsoft**

Ukládá ukazatel na aktuální strukturu řízení virtuálních počítačů (VMCS) na zadané adrese.

## <a name="syntax"></a>Syntaxe

```C
void __vmx_vmptrst(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmcsPhysicalAddress*\
pro Adresa, kde je uložen aktuální ukazatel VMCS

## <a name="remarks"></a>Poznámky

Ukazatel VMCS je 64 fyzická adresa.

Funkce je ekvivalentní `VMPTRST` instrukci počítače. `__vmx_vmptrst` Tato funkce podporuje interakci monitorování virtuálního počítače hostitele s hostovaným operačním systémem a jeho aplikacemi. Další informace najdete v dokumentu "Technická specifikace technologie Intel Virtualization pro architekturu IA-32 Intel," číslo dokumentu C97063-002 "na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__vmx_vmptrst`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)
