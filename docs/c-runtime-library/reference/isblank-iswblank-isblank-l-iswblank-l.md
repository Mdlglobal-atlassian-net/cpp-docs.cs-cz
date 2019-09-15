---
title: isblank, iswblank, _isblank_l, _iswblank_l
ms.date: 11/04/2016
api_name:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
ms.openlocfilehash: 022eba0335facc597f0608d63cfb58e0146e0f23
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954521"
---
# <a name="isblank-iswblank-_isblank_l-_iswblank_l"></a>isblank, iswblank, _isblank_l, _iswblank_l

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
Celé číslo k otestování.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud je *c* konkrétní reprezentace mezery nebo horizontálního znaku tabulátoru, nebo je jednou ze sad znaků specifických pro národní prostředí, které se používají k oddělení slov v rámci řádku textu. hodnota **blank** vrátí nenulovou hodnotu, pokud je *c* znak mezery (0x20) nebo znak horizontálního tabulátoru (0x09). Výsledek testovací podmínky pro funkce **unblank** závisí na nastavení kategorie **LC_CTYPE** národního prostředí; Další informace naleznete v tématu [setlocale, _wsetlocale](setlocale-wsetlocale.md). Verze těchto funkcí, které nemají příponu **_l** , používají aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; verze, které mají příponu **_l** , jsou stejné s tím rozdílem, že používají národní prostředí, které je předáno místo toho. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

**iswblank** vrací nenulovou hodnotu, pokud je *c* je celosvětovým znakem, který odpovídá standardnímu znaku mezery nebo horizontálnímu znaku tabulátoru.

Chování funkce **blank** a **_isblank_l** není definováno, pokud *c* není EOF nebo v rozsahu 0 až 0xFF (včetně). Pokud je použita knihovna CRT ladění a *c* není jedna z těchto hodnot, funkce vyvolá kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isblank**|\<CType. h >|
|**iswblank**|\<CType. h > nebo \<WCHAR. h >|
|**_isblank_l**|\<CType. h >|
|**_iswblank_l**|\<CType. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
