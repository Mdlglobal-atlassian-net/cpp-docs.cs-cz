---
title: _CIatan2
ms.date: 11/04/2016
api_name:
- _CIatan2
api_location:
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIatan2
- _CIatan2
helpviewer_keywords:
- _CIatan2 intrinsic
- CIatan2 intrinsic
ms.assetid: 31f8cc78-b79f-4576-b73b-8add18e08680
ms.openlocfilehash: dee536b41ccb4c45284fa418e92b99807e51c53a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940534"
---
# <a name="_ciatan2"></a>_CIatan2

Vypočítá arkustangens *x* / *y* , kde *x* a *y* jsou hodnoty v horní části zásobníku.

## <a name="syntax"></a>Syntaxe

```
void __cdecl _CIatan2();
```

## <a name="remarks"></a>Poznámky

Tato verze `atan2` funkce má specializovanou konvenci volání, kterou kompilátor rozumí. Zrychluje spouštění, protože brání vygenerování kopií a pomáhá s přidělením registru.

Výsledná hodnota je vložena do horní části zásobníku.

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)
