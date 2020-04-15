---
title: _isctype, iswctype, _isctype_l, _iswctype_l
ms.date: 4/2/2020
api_name:
- _isctype_l
- iswctype
- _iswctype_l
- _isctype
- _o__isctype
- _o__isctype_l
- _o__iswctype_l
- _o_iswctype
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
- iswctype
- _isctype
- _isctype_l
- _iswctype
- isctype
- iswctype_l
- isctype_l
- _iswctype_l
helpviewer_keywords:
- isctype_l function
- iswctype_l function
- iswctype function
- _isctype function
- _isctype_l function
- _iswctype_l function
- isctype function
- _iswctype function
ms.assetid: cf7509b7-12fc-4d95-8140-ad2eb98173d3
ms.openlocfilehash: 5beedd8a5da6848fc8c43ab1a27ee52402fe394e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343856"
---
# <a name="_isctype-iswctype-_isctype_l-_iswctype_l"></a>_isctype, iswctype, _isctype_l, _iswctype_l

Testuje *c* pro vlastnost ctype určenou argumentem *desc.* Pro každou platnou hodnotu *desc*existuje ekvivalentní rutina klasifikace širokých znaků.

## <a name="syntax"></a>Syntaxe

```C
int _isctype(
   int c,
   _ctype_t desc
);
int _isctype_l(
   int c,
   _ctype_t desc,
   _locale_t locale
);
int iswctype(
   wint_t c,
   wctype_t desc
);
int _iswctype_l(
   wint_t c,
   wctype_t desc,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Celé číslo k testování.

*Desc*<br/>
Vlastnost, pro která chcete testovat. To se obvykle načítá pomocí ctype nebo [wctype](wctype.md).

*Národní prostředí*<br/>
Národní prostředí, které chcete použít pro všechny testy závislé na národním prostředí.

## <a name="return-value"></a>Návratová hodnota

**_isctype** a **iswctype** vrátí nenulovou hodnotu, pokud *c* má vlastnost určenou *desc* v aktuálním národním prostředí nebo 0, pokud tomu tak není. Verze těchto funkcí s **příponou _l** jsou identické s tím rozdílem, že používají národní prostředí předané namísto aktuálního národního prostředí pro jejich chování závislé na národním prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Chování **_isctype** a **_isctype_l** není definována, pokud *c* není EOF nebo v rozsahu 0 až 0xFF, včetně. Při ladění CRT knihovny a *c* není jednou z těchto hodnot, funkce vyvolat kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|neuvedeno|**_isctype**|neuvedeno|**_iswctype**|
|neuvedeno|**_isctype_l**|neuvedeno|**_iswctype_l**|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_isctype**|\<ctype.h>|
|**iswctyp**|\<ctype.h> \<nebo wchar.h>|
|**_isctype_l**|\<ctype.h>|
|**_iswctype_l**|\<ctype.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw Rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
