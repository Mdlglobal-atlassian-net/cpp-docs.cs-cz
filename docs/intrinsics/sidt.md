---
title: __sidt
ms.date: 11/04/2016
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: 88dbb4713577fcf224e1c5646bf4c38b2a1dfafe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390318"
---
# <a name="sidt"></a>__sidt

**Microsoft Specific**

Uloží hodnotu registru tabulky popisovače přerušení (IDTR) v zadaném umístění v paměti.

## <a name="syntax"></a>Syntaxe

```
void __sidt(void * Destination);
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*cíl*|[in] Ukazatel na umístění v paměti, kde je uložen IDTR.|

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__sidt`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`__sidt` Funkce je ekvivalentní volání `SIDT` strojové instrukce. Další informace vyhledejte dokument, "ruční architektury Intel softwarový vývojář, svazek 2: Instrukce nastavit odkaz,"na [společnosti Intel Corporation](https://software.intel.com/articles/intel-sdm) lokality.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__lidt](../intrinsics/lidt.md)