---
title: __svm_stgi
ms.date: 09/02/2019
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: 6bd731951b440d3d2597d54c9a52d9f8640a5c5f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219843"
---
# <a name="__svm_stgi"></a>__svm_stgi

**Specifické pro společnost Microsoft**

Nastaví příznak globálního přerušení.

## <a name="syntax"></a>Syntaxe

```C
void __svm_stgi(void);
```

## <a name="remarks"></a>Poznámky

Funkce je ekvivalentní `STGI` instrukci počítače. `__svm_stgi` Příznak globálního přerušení určuje, zda mikroprocesor ignoruje, odloží nebo zpracovává přerušení, kvůli událostem, jako je například dokončení vstupně-výstupních operací, Výstraha teploty hardwaru nebo výjimka ladění.

Tato funkce podporuje interakci monitorování virtuálního počítače hostitele s hostovaným operačním systémem a jeho aplikacemi. Další informace najdete v tématu "ručním svazkem pro programátory AMD64 architektury": Programování systému, "na webu [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__svm_stgi`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__svm_clgi](../intrinsics/svm-clgi.md)
