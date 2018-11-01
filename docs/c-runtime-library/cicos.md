---
title: _CIcos
ms.date: 04/11/2018
apiname:
- _CIcos
apilocation:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- CIcos
- _CIcos
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
ms.openlocfilehash: fc6cb9a45a7467e63129bd859817ebdfc23a0160
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497226"
---
# <a name="cicos"></a>_CIcos

Vypočítá kosinus nejvyšší hodnotu v zásobníku s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _CIcos();
```

## <a name="remarks"></a>Poznámky

Tato verze [cos](../c-runtime-library/reference/cos-cosf-cosl.md) funkce má specializované konvence volání, které kompilátor rozpozná. Urychluje provádění, protože kopie zabraňuje generovaných a pomáhá při přidělení registru.

Výsledná hodnota je vloženy do horní části zásobníku s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[Cos cosf –, cosl –](../c-runtime-library/reference/cos-cosf-cosl.md)<br/>
