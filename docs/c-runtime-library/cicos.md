---
title: _CIcos
ms.date: 4/2/2020
api_name:
- _CIcos
- _o__CIcos
api_location:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIcos
- _CIcos
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
ms.openlocfilehash: e7009272dbbd2b406c6355977514feaaf13ba746
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334379"
---
# <a name="_cicos"></a>_CIcos

Vypočítá kosinus nejvyšší hodnoty v zásobníku s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _CIcos();
```

## <a name="remarks"></a>Poznámky

Tato verze funkce [cos](../c-runtime-library/reference/cos-cosf-cosl.md) má specializovanou konvenci volání, které kompilátor rozumí. Urychluje provádění, protože zabraňuje generování kopií a pomáhá s přidělením registru.

Výsledná hodnota je posunuta do horní části zásobníku s plovoucí desetinnou desetinnou táhou.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[cos, cosf, cosl](../c-runtime-library/reference/cos-cosf-cosl.md)<br/>
