---
title: __vmx_vmptrld
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: 79b5a8b34b652ae1f011e89c793a7157c9e435ee
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219504"
---
# <a name="__vmx_vmptrld"></a>__vmx_vmptrld

**Specifické pro společnost Microsoft**

Načte ukazatel na aktuální strukturu řízení virtuálních počítačů (VMCS) ze zadané adresy.

## <a name="syntax"></a>Syntaxe

```C
int __vmx_vmptrld(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmcsPhysicalAddress*\
pro Adresa, kde je uložen ukazatel VMCS.

## <a name="return-value"></a>Návratová hodnota

0\
Operace byla úspěšná.

1\
Operace se nezdařila s rozšířeným stavem dostupným v `VM-instruction error field` aktuálním VMCS.

2\
Operace se nezdařila bez dostupného stavu.

## <a name="remarks"></a>Poznámky

Ukazatel VMCS je 64 fyzická adresa.

Funkce je ekvivalentní `VMPTRLD` instrukci počítače. `__vmx_vmptrld` Tato funkce podporuje interakci monitorování virtuálního počítače hostitele s hostovaným operačním systémem a jeho aplikacemi. Další informace najdete v dokumentu "Technická specifikace technologie Intel Virtualization pro architekturu IA-32 Intel," číslo dokumentu C97063-002 "na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__vmx_vmptrld`|x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)
