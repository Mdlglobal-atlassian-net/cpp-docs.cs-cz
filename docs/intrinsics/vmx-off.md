---
title: __vmx_off
ms.date: 11/04/2016
f1_keywords:
- __vmx_off
helpviewer_keywords:
- VMXOFF instruction
- __vmx_off intrinsic
ms.assetid: 78a32d46-9291-406c-b982-a550855aff18
ms.openlocfilehash: 4a01752bd510f9aa8cb159c23e691c9d244145e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390071"
---
# <a name="vmxoff"></a>__vmx_off

**Microsoft Specific**

Deaktivuje operace rozšíření (VMX) virtuálního počítače v procesoru.

## <a name="syntax"></a>Syntaxe

```
void __vmx_off();
```

## <a name="remarks"></a>Poznámky

`__vmx_off` Funkce je ekvivalentní volání `VMXOFF` strojové instrukce. Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace, hledání dokumentů "Intel Virtualization technické specifikace pro the architekturou IA-32 Intel," dokumentu C97063-002 čísla na [společnosti Intel Corporation](https://software.intel.com/articles/intel-sdm) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__vmx_off`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)