---
title: isprint, iswprint, _isprint_l, _iswprint_l
ms.date: 4/2/2020
api_name:
- iswprint
- isprint
- _isprint_l
- _iswprint_l
- _o_isprint
- _o_iswprint
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswprint
- _istprint
- isprint
helpviewer_keywords:
- _istprint function
- iswprint function
- _iswprint_l function
- isprint_l function
- istprint function
- isprint function
- iswprint_l function
- _isprint_l function
ms.assetid: a8bbcdb0-e8d0-4d8c-ae4e-56d3bdee6ca3
ms.openlocfilehash: f09168e8e010fb59d748c109d4a41c533318e2eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342888"
---
# <a name="isprint-iswprint-_isprint_l-_iswprint_l"></a>isprint, iswprint, _isprint_l, _iswprint_l

Určuje, zda celé číslo představuje tisknutelný znak.

## <a name="syntax"></a>Syntaxe

```C
int isprint(
   int c
);
int iswprint(
   wint_t c
);
int _isprint_l(
   int c,
   _locale_t locale
);
int _iswprint_l(
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

Každá z těchto rutin vrátí nenulovou, pokud *c* je konkrétní reprezentace tisknutelného znaku. **isprint** vrátí nenulovou hodnotu, pokud *c* je tisknutelný znak – to zahrnuje znak mezery (0x20 - 0x7E). **iswprint** vrátí nenulovou hodnotu, pokud *c* je tisknutelný široký znak – to zahrnuje celý znak mezery. Každá z těchto rutin vrátí hodnotu 0, pokud *c* nesplňuje zkušební podmínku.

Výsledek zkušební podmínky pro tyto funkce závisí na **nastavení LC_CTYPE** kategorie národního prostředí; další informace naleznete [v _wsetlocale setlocale.](setlocale-wsetlocale.md) Verze těchto funkcí, které nemají **příponu _l,** používají aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; verze, které mají **_l** příponu jsou identické s tím rozdílem, že používají národní prostředí, které je předáno místo. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Chování **isprint** a **_isprint_l** není definována, pokud *c* není EOF nebo v rozsahu 0 až 0xFF, včetně. Při ladění CRT knihovny a *c* není jednou z těchto hodnot, funkce vyvolat kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_unicode definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**-** **istprint**|**isprint**|[_ismbcprint](ismbcgraph-functions.md)|**iswprint**|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isprint**|\<ctype.h>|
|**iswprint**|\<ctype.h> \<nebo wchar.h>|
|**_isprint_l**|\<ctype.h>|
|**_iswprint_l**|\<ctype.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw Rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
