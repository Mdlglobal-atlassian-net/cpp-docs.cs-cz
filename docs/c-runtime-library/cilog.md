---
title: _CIlog
ms.date: 11/04/2016
apiname:
- _CIlog
apilocation:
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _CIlog
- CIlog
helpviewer_keywords:
- _CIlog intrinsic
- CIlog intrinsic
ms.assetid: 23503854-ddaa-4fe0-a4a3-7fbb3a43bdec
ms.openlocfilehash: 731c30e08c40f839c99d028aa46d5b61e5fd7c92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566397"
---
# <a name="cilog"></a>_CIlog

Vypočítá přirozený logaritmus nejvyšší hodnotu v zásobníku.

## <a name="syntax"></a>Syntaxe

```
void __cdecl _CIlog();
```

## <a name="remarks"></a>Poznámky

Tato verze `log` funkce má specializované konvence volání, které kompilátor rozpozná. Urychluje provádění, protože kopie zabraňuje generovaných a pomáhá při přidělení registru.

Výsledná hodnota je vloženy do horní části zásobníku.

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[log, logf, log10, log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)