---
title: ispunct, iswpunct, _ispunct_l, _iswpunct_l
ms.date: 11/04/2016
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
ms.openlocfilehash: 209f94bb8f9d3338f62b719d4d4b94b152ed5ab7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496392"
---
# <a name="ispunct-iswpunct-ispunctl-iswpunctl"></a>ispunct, iswpunct, _ispunct_l, _iswpunct_l

Určuje, zda celočíselná hodnota představuje znak interpunkce.

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
Celé číslo k testování.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud *c* je konkrétní reprezentace znaku interpunkce. **ispunct** vrací nenulovou hodnotu pro libovolný tisknutelný znak, který není znak mezery nebo znak, pro který **isalnum** nenulové. **iswpunct –** vrátí nenulovou hodnotu pro libovolný široký tisknutelný znak, který není široký znak mezery ani široký znak, pro které **iswalnum –** nenulové. Každá z těchto rutin vrátí hodnotu 0, pokud *c* nesplňuje testovací podmínku.

Výsledek testovací podmínky pro **ispunct** funkce závisí **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale _wsetlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí, které nemají **_l** používají aktuální národní prostředí pro všechna chování závislé na národním prostředí; ty, které mají **_l** přípona jsou stejné s tím rozdílem, že používají národní prostředí, které je předáno místo. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Chování **ispunct** a **_ispunct_l –** není definováno, pokud *c* není konec souboru nebo v rozsahu 0 až 0xFF, včetně. Při použití ladicí CRT knihovny a *c* není jednou z těchto hodnot, funkce vyvolá kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istpunct –**|**ispunct**|[_ismbcpunct](ismbcgraph-functions.md)|**iswpunct –**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ispunct**|\<ctype.h >|
|**iswpunct –**|\<ctype.h > nebo \<wchar.h >|
|**_ispunct_l**|\<ctype.h >|
|**_iswpunct_l**|\<ctype.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
