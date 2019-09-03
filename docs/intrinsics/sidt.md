---
title: __sidt
ms.date: 09/02/2019
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: d6b685da0e02373307a3149c5b7b28213f37ad40
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222321"
---
# <a name="__sidt"></a>__sidt

**Specifické pro společnost Microsoft**

Ukládá v zadaném umístění v paměti hodnotu registru deskriptoru přerušení (IDTR).

## <a name="syntax"></a>Syntaxe

```C
void __sidt(void * Destination);
```

### <a name="parameters"></a>Parametry

*Tabulka*\
pro Ukazatel na umístění v paměti, kde je uložen IDTR.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__sidt`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Funkce je ekvivalentní `SIDT` instrukci počítače. `__sidt` Pokud chcete získat další informace, vyhledejte dokument "Intel Architecture Software Developer 's Manual, Volume 2: Odkaz na sadu instrukcí "na webu [společnosti Intel](https://software.intel.com/articles/intel-sdm) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__lidt](../intrinsics/lidt.md)
