---
title: __nop
ms.date: 09/02/2019
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 4561bcb84063f3707825c8ca164867d41500e2db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221669"
---
# <a name="__nop"></a>__nop

**Specifické pro společnost Microsoft**

Generuje strojový kód specifický pro platformu, který neprovede žádnou operaci.

## <a name="syntax"></a>Syntaxe

```C
void __nop();
```

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__nop`|x86, ARM, x64, ARM64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="remarks"></a>Poznámky

Funkce je ekvivalentní `NOP` instrukci počítače. `__nop` Pokud chcete získat další informace o x86 a x64, vyhledejte dokument "Intel Architecture Software Developer 's Manual, Volume 2: Odkaz na sadu instrukcí "na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__noop](../intrinsics/noop.md)
