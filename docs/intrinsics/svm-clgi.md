---
title: __svm_clgi
ms.date: 09/02/2019
f1_keywords:
- __svm_clgi
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
ms.openlocfilehash: 740c76e5dcc8f94b9257272624a6ad3c1f9726c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219966"
---
# <a name="__svm_clgi"></a>__svm_clgi

**Specifické pro společnost Microsoft**

Odstraní příznak globálního přerušení.

## <a name="syntax"></a>Syntaxe

```C
void __svm_clgi( void );
```

## <a name="remarks"></a>Poznámky

Funkce je ekvivalentní `CLGI` instrukci počítače. `__svm_clgi` Příznak globálního přerušení určuje, zda mikroprocesor ignoruje, odloží nebo zpracovává přerušení, kvůli událostem, jako je například dokončení vstupně-výstupních operací, Výstraha teploty hardwaru nebo výjimka ladění.

Tato funkce podporuje interakci monitorování virtuálního počítače hostitele s hostovaným operačním systémem a jeho aplikacemi. Další informace najdete v tématu "ručním svazkem pro programátory AMD64 architektury": Programování systému, "na webu [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__svm_clgi`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__svm_stgi](../intrinsics/svm-stgi.md)
