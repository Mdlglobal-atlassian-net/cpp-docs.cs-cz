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
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740005"
---
# <a name="btowc"></a>btowc

Určí, zda celočíselná hodnota představuje platný znak jednobajtového znaku v počátečním stavu posunutí.

## <a name="syntax"></a>Syntaxe

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>Parametry

*character*<br/>
Celé číslo k otestování.

## <a name="return-value"></a>Návratová hodnota

Vrátí reprezentaci celého znaku znaku, pokud celé číslo představuje platný znak jednobajtového znaku v počátečním stavu posunutí. Vrátí WEOF, pokud je celočíselná hodnota EOF nebo není platným znakem jednobajtové v počátečním stavu posunutí. Výstup této funkce je ovlivněn aktuálním národním prostředím **LC_TYPE** .

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**btowc**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
