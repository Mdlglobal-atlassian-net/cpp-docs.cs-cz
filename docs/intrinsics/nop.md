---
title: __nop
ms.date: 11/04/2016
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 1e76110c1ef0c4b98c295578189eedc99d76eeb9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396623"
---
# <a name="nop"></a>__nop

**Microsoft Specific**

Generuje pro konkrétní platformu strojového kódu, který neprovádí operaci.

## <a name="syntax"></a>Syntaxe

```
void __nop();
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__nop`|x86, ARM, x64, ARM64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="remarks"></a>Poznámky

`__nop` Funkce je ekvivalentní volání `NOP` strojové instrukce. Další informace o x86 a x64 vyhledejte dokument, "ruční architektury Intel softwarový vývojář, svazek 2: Instrukce nastavit odkaz,"na [společnosti Intel Corporation](https://software.intel.com/articles/intel-sdm) lokality.

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__noop](../intrinsics/noop.md)
