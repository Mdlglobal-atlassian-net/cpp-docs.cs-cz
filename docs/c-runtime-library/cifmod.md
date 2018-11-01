---
title: _CIfmod
ms.date: 11/04/2016
apiname:
- _CIfmod
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _CIfmod
- CIfmod
helpviewer_keywords:
- CIfmod intrinsic
- _CIfmod intrinsic
ms.assetid: 7c050653-7ec6-4810-b3a7-7a0057ea65ed
ms.openlocfilehash: 4f0ad84d61153c81e1e4ef6bc804a3ad498f854f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601133"
---
# <a name="cifmod"></a>_CIfmod

Vypočítá zbytek s plovoucí desetinnou čárkou nejvyšší dvě hodnoty v zásobníku.

## <a name="syntax"></a>Syntaxe

```
void __cdecl _CIfmod();
```

## <a name="remarks"></a>Poznámky

Tato verze `fmod` funkce má specializované konvence volání, které kompilátor rozpozná. Urychluje provádění, protože kopie zabraňuje generovaných a pomáhá při přidělení registru.

Výsledná hodnota je vloženy do horní části zásobníku.

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[fmod, fmodf](../c-runtime-library/reference/fmod-fmodf.md)