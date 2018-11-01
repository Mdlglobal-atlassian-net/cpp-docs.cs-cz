---
title: __lidt
ms.date: 11/04/2016
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 8ac86674dfa0dc269328854d363db24922cf20ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623883"
---
# <a name="lidt"></a>__lidt

**Specifické pro Microsoft**

Načte do přerušení popisovač tabulky registru (IDTR) s hodnotou v zadaném umístění v paměti.

## <a name="syntax"></a>Syntaxe

```
void __lidt(void * Source);
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Zdroj*|[in] Hodnota, která má být zkopírován do IDTR ukazatel.|

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__lidt`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

`__lidt` Funkce je ekvivalentní volání `LIDT` strojové instrukce a je k dispozici pouze v režimu jádra. Další informace vyhledejte dokument, "ruční architektury Intel softwarový vývojář, svazek 2: odkaz na sadu instrukcí," na [společnosti Intel Corporation](https://software.intel.com/articles/intel-sdm) lokality.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__sidt](../intrinsics/sidt.md)