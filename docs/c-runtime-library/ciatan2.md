---
title: _CIatan2
ms.date: 4/2/2020
api_name:
- _CIatan2
- _o__CIatan2
api_location:
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 585608b4d3dce723c0ea3a82e1c52325a0f6b7e6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745933"
---
# <a name="_ciatan2"></a>_CIatan2

Vypočítá arctangent *x* / *y,* kde *x* a *y* jsou hodnoty v horní části zásobníku.

## <a name="syntax"></a>Syntaxe

```cpp
void __cdecl _CIatan2();
```

## <a name="remarks"></a>Poznámky

Tato verze `atan2` funkce má specializované konvence volání, které kompilátor rozumí. Urychluje provádění, protože zabraňuje generování kopií a pomáhá s přidělením registru.

Výsledná hodnota je posunuta do horní části zásobníku.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)
