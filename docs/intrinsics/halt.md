---
title: __halt
ms.date: 09/02/2019
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: 66f5e05e7673523966ef35ac743fc585930b511c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222160"
---
# <a name="__halt"></a>__halt

**Specifické pro společnost Microsoft**

Zastaví mikroprocesory, dokud neproběhne povolené přerušení, nemaskované přerušení (NMI) nebo obnovení.

## <a name="syntax"></a>Syntaxe

```C
void __halt( void );
```

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__halt`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Funkce je ekvivalentní `HLT` instrukci počítače a je k dispozici pouze v režimu jádra. `__halt` Pokud chcete získat další informace, vyhledejte dokument "Intel Architecture Software Developer 's Manual, Volume 2: Odkaz na sadu instrukcí "na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
