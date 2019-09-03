---
title: __svm_invlpga
ms.date: 09/02/2019
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: e0f8ef02efdb64f70bb65f6f017449fcc03beca1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219883"
---
# <a name="__svm_invlpga"></a>__svm_invlpga

**Specifické pro společnost Microsoft**

Zruší platnost položky mapování adres v vyrovnávací paměti pro překlad z překladu počítače. Parametry určují virtuální adresu a identifikátor adresního prostoru stránky k neplatnosti.

## <a name="syntax"></a>Syntaxe

```C
void __svm_invlpga(void *Vaddr, int as_id);
```

### <a name="parameters"></a>Parametry

*Vaddr*\
pro Virtuální adresa stránky, která se má neověřit

*as_id*\
pro Identifikátor adresního prostoru (ASID) stránky pro zrušení platnosti.

## <a name="remarks"></a>Poznámky

Funkce je ekvivalentní `INVLPGA` instrukci počítače. `__svm_invlpga` Tato funkce podporuje interakci monitorování virtuálního počítače hostitele s hostovaným operačním systémem a jeho aplikacemi. Další informace najdete v dokumentu, "ručním svazkem pro programátory AMD64 architektury AMD64: Programování systému, "číslo dokumentu 24593, revize 3,11, na webu [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__svm_invlpga`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
