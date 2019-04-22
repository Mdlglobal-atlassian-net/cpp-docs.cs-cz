---
title: __halt
ms.date: 11/04/2016
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: dd68c88a13035ca25f89304bcd84267a73978420
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025948"
---
# <a name="halt"></a>__halt

**Microsoft Specific**

Mikroprocesoru zastaví, dokud nenastane povoleno přerušení, nemaskovatelné přerušení (NMI) nebo obnovení.

## <a name="syntax"></a>Syntaxe

```
void __halt( void );
```

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__halt`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`__halt` Funkce je ekvivalentní volání `HLT` strojové instrukce a je k dispozici pouze v režimu jádra. Další informace vyhledejte dokument, "ruční architektury Intel softwarový vývojář, svazek 2: Instrukce nastavit odkaz,"na [společnosti Intel Corporation](https://software.intel.com/articles/intel-sdm) lokality.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)