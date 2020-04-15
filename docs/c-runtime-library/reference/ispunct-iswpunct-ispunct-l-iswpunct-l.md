---
title: ispunct, iswpunct, _ispunct_l, _iswpunct_l
ms.date: 4/2/2020
api_name:
- ispunct
- _iswpunct_l
- iswpunct
- _ispunct_l
- _o_ispunct
- _o_iswpunct
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3072f147d2adff2c50304d2d2052947ca32cb060
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342814"
---
# <a name="ispunct-iswpunct-_ispunct_l-_iswpunct_l"></a>ispunct, iswpunct, _ispunct_l, _iswpunct_l

Určuje, zda celé číslo představuje interpunkční znak.

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

*C*<br/>
Celé číslo k testování.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou, pokud *c* je konkrétní reprezentace interpunkčního znaku. **ispunct** vrátí nenulovou hodnotu pro libovolný tisknutelný znak, který není znakem mezery nebo znakem, pro který je **isalnum** nenulová. **iswpunct** vrátí nenulovou hodnotu pro všechny tisknutelné široký znak, který není ani mezera široký znak ani široký znak, pro který **iswalnum** je nenulová. Každá z těchto rutin vrátí hodnotu 0, pokud *c* nesplňuje zkušební podmínku.

Výsledek zkušební podmínky pro **ispunct** funkce závisí na **nastavení LC_CTYPE** kategorie národního prostředí; další informace naleznete [v _wsetlocale setlocale.](setlocale-wsetlocale.md) Verze těchto funkcí, které nemají **příponu _l,** používají aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; verze, které mají **_l** příponu jsou identické s tím rozdílem, že používají národní prostředí, které je předáno místo. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Chování **ispunct** a **_ispunct_l** je nedefinována, pokud *c* není EOF nebo v rozsahu 0 až 0xFF, včetně. Při ladění CRT knihovny a *c* není jednou z těchto hodnot, funkce vyvolat kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**-** **istpunct**|**ispunct**|[_ismbcpunct](ismbcgraph-functions.md)|**iswpunct**|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ispunct**|\<ctype.h>|
|**iswpunct**|\<ctype.h> \<nebo wchar.h>|
|**_ispunct_l**|\<ctype.h>|
|**_iswpunct_l**|\<ctype.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw Rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
