---
title: isblank, iswblank, _isblank_l, _iswblank_l
ms.date: 11/04/2016
apiname:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
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
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
ms.openlocfilehash: eb088c4056e2277e188d7f98a57dd36216d013ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497315"
---
# <a name="isblank-iswblank-isblankl-iswblankl"></a>isblank, iswblank, _isblank_l, _iswblank_l

Určuje, zda celočíselná hodnota představuje prázdný znak.

## <a name="syntax"></a>Syntaxe

```C
int isblank(
   int c
);
int iswblank(
   wint_t c
);
int _isblank_l(
   int c,
   _locale_t locale
);
int _iswblank_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo k testování.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud *c* konkrétní reprezentací prostoru nebo znak horizontálního tabulátoru, nebo je jednou ze specifických pro národní prostředí množinu znaků, které se používají k oddělení slov v řádku textu. **isblank** vrací nenulovou hodnotu, pokud *c* je znak mezery (0x20) nebo znak horizontálního tabulátoru (0x09). Výsledek testovací podmínky pro **isblank** funkce závisí **LC_CTYPE** kategorie nastavení národního prostředí; Další informace najdete v článku [setlocale _wsetlocale](setlocale-wsetlocale.md). Verze těchto funkcí, které nemají **_l** používají aktuální národní prostředí pro všechna chování závislé na národním prostředí; ty, které mají **_l** přípona jsou stejné s tím rozdílem, že používají národní prostředí, které je předáno místo. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

**iswblank** vrací nenulovou hodnotu, pokud *c* je široký znak který odpovídá standardní mezeře nebo znaku horizontálního tabulátoru.

Chování **isblank** a **_isblank_l** není definováno, pokud *c* není konec souboru nebo v rozsahu 0 až 0xFF, včetně. Při použití ladicí CRT knihovny a *c* není jednou z těchto hodnot, funkce vyvolá kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isblank**|\<ctype.h >|
|**iswblank**|\<ctype.h > nebo \<wchar.h >|
|**_isblank_l**|\<ctype.h >|
|**_iswblank_l**|\<ctype.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
