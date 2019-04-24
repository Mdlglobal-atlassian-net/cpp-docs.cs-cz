---
title: _CIlog10
ms.date: 11/04/2016
apiname:
- _CIlog10
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- CIlog10
- _CIlog10
helpviewer_keywords:
- _CIlog10 intrinsic
- CIlog10 intrinsic
ms.assetid: 05d7fcaa-3cff-4cc5-8d44-015e7cacba24
ms.openlocfilehash: 771ed103c8ab0fe29061086923189cc90eb047d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290180"
---
# <a name="cilog10"></a>_CIlog10

Provádí `log10` operace na nejvyšší hodnotu v zásobníku.

## <a name="syntax"></a>Syntaxe

```
void __cdecl _CIlog10();
```

## <a name="remarks"></a>Poznámky

Tato verze `log10` funkce má specializované konvence volání, které kompilátor rozpozná. Funkce urychluje provádění, protože kopie zabraňuje generovaných a pomáhá při přidělení registru.

Výsledná hodnota je vloženy do horní části zásobníku.

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[log, logf, log10, log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)
