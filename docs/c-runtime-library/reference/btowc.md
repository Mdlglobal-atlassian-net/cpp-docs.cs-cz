---
title: btowc
ms.date: 11/04/2016
apiname:
- btowc
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: 399f56fe133a9f67ed457b435ae6c0496e1ecaa5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514673"
---
# <a name="btowc"></a>btowc

Určení, zda celočíselná hodnota představuje platné jednobajtový znak ve stavu počáteční posun.

## <a name="syntax"></a>Syntaxe

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>Parametry

*Znak*<br/>
Celé číslo k testování.

## <a name="return-value"></a>Návratová hodnota

Vrátí širokoznaká reprezentace znaku, pokud celé číslo představuje platné jednobajtový znak ve stavu počáteční posun. WEOF vrátí, pokud celé číslo se konec souboru nebo není platný jednobajtový znak ve stavu počáteční posun. Výstup této funkce je ovlivněna aktuálním **LC_TYPE** národní prostředí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**btowc**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
