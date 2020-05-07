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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a9b18c2eb0a76885f3c3aad7bb1f03d7dea52c5c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918071"
---
# <a name="_cicos"></a>_CIcos

Vypočítá kosinus horní hodnoty v zásobníku s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _CIcos();
```

## <a name="remarks"></a>Poznámky

Tato verze funkce [cos](../c-runtime-library/reference/cos-cosf-cosl.md) má specializovanou konvenci volání, kterou kompilátor rozumí. Zrychluje spouštění, protože brání vygenerování kopií a pomáhá s přidělením registru.

Výsledná hodnota je vložena do horní části zásobníku s plovoucí desetinnou čárkou.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[cos, cosf, cosl](../c-runtime-library/reference/cos-cosf-cosl.md)<br/>
