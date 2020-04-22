---
title: _CIexp
ms.date: 4/2/2020
api_name:
- _CIexp
- _o__CIexp
api_location:
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIexp
- _CIexp
helpviewer_keywords:
- CIexp intrinsic
- _CIexp intrinsic
ms.assetid: f8a3e3b7-fa57-41a3-9983-6c81914cbb55
ms.openlocfilehash: a85a9a90ee922c6100649f2aebb9eb4c68696a0d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745768"
---
# <a name="_ciexp"></a>_CIexp

Vypočítá exponenciální nejvyšší hodnotu v zásobníku.

## <a name="syntax"></a>Syntaxe

```cpp
void __cdecl _CIexp();
```

## <a name="remarks"></a>Poznámky

Tato verze `exp` funkce má specializované konvence volání, které kompilátor rozumí. Urychluje provádění, protože zabraňuje generování kopií a pomáhá s přidělením registru.

Výsledná hodnota je posunuta do horní části zásobníku.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](../c-runtime-library/reference/exp-expf.md)
