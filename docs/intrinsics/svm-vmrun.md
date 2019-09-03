---
title: __svm_vmrun
ms.date: 09/02/2019
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: f23df894cc8ad1c270c4c0acbc97cab727e47d93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219818"
---
# <a name="__svm_vmrun"></a>__svm_vmrun

**Specifické pro společnost Microsoft**

Spustí spuštění kódu hosta virtuálního počítače, který odpovídá zadanému řídicímu bloku virtuálního počítače (VMCB).

## <a name="syntax"></a>Syntaxe

```C
void __svm_vmrun(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>Parametry

*VmcbPhysicalAddress*\
pro Fyzická adresa VMCB.

## <a name="remarks"></a>Poznámky

`__svm_vmrun` Funkce používá k zahájení provádění kódu hosta virtuálního počítače minimální množství informací v VMCB. Použijte funkci [__svm_vmsave](../intrinsics/svm-vmsave.md) nebo [__svm_vmload](../intrinsics/svm-vmload.md) , pokud potřebujete další informace pro zpracování složitého přerušení nebo přepnutí na jiný host.

Funkce je ekvivalentní `VMRUN` instrukci počítače. `__svm_vmrun` Tato funkce podporuje interakci monitorování virtuálního počítače hostitele s hostovaným operačním systémem a jeho aplikacemi. Další informace najdete v dokumentu, "ručním svazkem pro programátory AMD64 architektury AMD64: Programování systému, "číslo dokumentu 24593, revize 3,11 nebo novější, na webu [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__svm_vmrun`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
