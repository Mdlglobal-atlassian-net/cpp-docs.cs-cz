---
title: __svm_stgi
ms.date: 11/04/2016
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: ea138f17a24af21afa937991f77bd1e2a689c3f7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024787"
---
# <a name="svmstgi"></a>__svm_stgi

**Specifické pro Microsoft**

Nastaví příznak globální přerušení.

## <a name="syntax"></a>Syntaxe

```
void __svm_stgi(void);
```

## <a name="remarks"></a>Poznámky

`__svm_stgi` Funkce je ekvivalentní volání `STGI` strojové instrukce. Přerušení globální příznak určuje, jestli mikroprocesoru ignoruje, odloží nebo zpracovává přerušení z důvodu události, například dokončení vstupně-výstupních operací, výstraha teploty hardwaru nebo výjimka ladění.

Tato funkce podporuje interakce monitorování virtuálního počítače hostitele s hostovaného operačního systému a jeho aplikací. Další informace vyhledejte dokument, "ruční svazek programátor architektury AMD64 2: Číslo 24593 revize 3.11, systém programování,"dokumentu na [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokality.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__svm_stgi`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**END Specifické pro Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_clgi](../intrinsics/svm-clgi.md)