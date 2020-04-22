---
title: _CIfmod
ms.date: 4/2/2020
api_name:
- _CIfmod
- _o__CIfmod
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CIfmod
- CIfmod
helpviewer_keywords:
- CIfmod intrinsic
- _CIfmod intrinsic
ms.assetid: 7c050653-7ec6-4810-b3a7-7a0057ea65ed
ms.openlocfilehash: 8dcae95fa260593adc434fcaba648972caccb692
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745374"
---
# <a name="_cifmod"></a>_CIfmod

Vypočítá zbytek s plovoucí desetinnou cínek z prvních dvou hodnot v zásobníku.

## <a name="syntax"></a>Syntaxe

```cpp
void __cdecl _CIfmod();
```

## <a name="remarks"></a>Poznámky

Tato verze `fmod` funkce má specializované konvence volání, které kompilátor rozumí. Urychluje provádění, protože zabraňuje generování kopií a pomáhá s přidělením registru.

Výsledná hodnota je posunuta do horní části zásobníku.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[fmod, fmodf](../c-runtime-library/reference/fmod-fmodf.md)
