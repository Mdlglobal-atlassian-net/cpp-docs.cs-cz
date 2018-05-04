---
title: ispunct –, iswpunct –, _ispunct_l –, _iswpunct_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ispunct
- _iswpunct_l
- iswpunct
- _ispunct_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswpunct
- _istpunct
- ispunct
dev_langs:
- C++
helpviewer_keywords:
- _istpunct function
- _ispunct_l function
- iswpunct function
- ispunct function
- istpunct function
- ispunct_l function
- _iswpunct_l function
- iswpunct_l function
ms.assetid: 94403240-85c8-40a4-9c2b-e3e95c729c76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9509270906de3f0a9c7a20fd5f126ecffcafcff0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ispunct-iswpunct-ispunctl-iswpunctl"></a>ispunct, iswpunct, _ispunct_l, _iswpunct_l

Určuje, zda celé reprezentuje interpunkční znaménko.

## <a name="syntax"></a>Syntaxe

```C
int ispunct(
   int c
);
int iswpunct(
   wint_t c
);
int _ispunct_l(
   int c,
   _locale_t locale
);
int _iswpunct_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo pro testování.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Všechny tyto rutiny vrátí nenulové hodnoty, pokud *c* je konkrétní reprezentace interpunkční znaménko. **ispunct –** vrátí nenulovou hodnotu pro všechny tisknutelná znak, který není znak mezery nebo znak, pro který **isalnum –** nenulový. **iswpunct –** vrátí nenulovou hodnotu pro všechny tisknutelná široké znak, který není široké znak mezery ani široké znak, pro který **iswalnum –** nenulový. Všechny tyto rutiny vrátí hodnotu 0, pokud *c* nesplňuje podmínky testu.

Výsledek testu podmínky pro **ispunct –** funkce závisí na **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale _wsetlocale](setlocale-wsetlocale.md) Další informace. Verze tyto funkce, které nemají **_l** příponu využívání aktuální národní prostředí pro chování všech závislých na národním prostředí, verze, které mají **_l** příponu jsou shodné s tím rozdílem, že se používají národní prostředí, který se předává v místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

Chování **ispunct –** a **_ispunct_l –** není definován, pokud *c* není EOF nebo v rozsahu 0 až 0xFF (včetně). V případě použití knihovny ladění CRT a *c* není jednou z těchto hodnot, funkce raise kontrolní výrazy.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istpunct –**|**ispunct –**|[_ismbcpunct](ismbcgraph-functions.md)|**iswpunct –**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ispunct –**|\<ctype.h >|
|**iswpunct –**|\<ctype.h > nebo \<wchar.h >|
|**_ispunct_l**|\<ctype.h >|
|**_iswpunct_l**|\<ctype.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
