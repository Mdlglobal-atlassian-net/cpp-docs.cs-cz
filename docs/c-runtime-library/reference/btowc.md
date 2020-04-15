---
title: btowc
ms.date: 4/2/2020
api_name:
- btowc
- _o_btowc
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: b4262f31c95b5272e3917f58a6c945577d401f16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333766"
---
# <a name="btowc"></a>btowc

Určete, zda celé číslo představuje platný jednobajtový znak v počátečním stavu směny.

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

Vrátí širokoúhlou reprezentaci znaku, pokud celé číslo představuje platný jednobajtový znak ve stavu počáteční směny. Vrátí funkce WEOF, pokud je celé číslo EOF nebo není platným jednobajtovým znakem ve stavu počáteční směny. Výstup této funkce je ovlivněn aktuálním **LC_TYPE** národního prostředí.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**btowc**|\<stdio.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
