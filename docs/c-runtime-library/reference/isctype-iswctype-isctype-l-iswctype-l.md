---
title: _isctype, iswctype, _isctype_l, _iswctype_l
ms.date: 11/04/2016
api_name:
- _isctype_l
- iswctype
- _iswctype_l
- _isctype
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
ms.openlocfilehash: 9fefb852f8ebd34b932842ee4c12b53f79b29641
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954403"
---
# <a name="_isctype-iswctype-_isctype_l-_iswctype_l"></a>_isctype, iswctype, _isctype_l, _iswctype_l

Testuje *c* pro vlastnost CType určenou argumentem *DESC* . Pro každou platnou hodnotu třídy *DESC*existuje ekvivalentní rutina klasifikace se stejnou šířkou znaku.

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

*c*<br/>
Celé číslo k otestování.

*desc*<br/>
Vlastnost, která se má testovat. To se obvykle načte pomocí CType nebo [wctype](wctype.md).

*jazyka*<br/>
Národní prostředí, které se má použít pro všechny testy závislé na národním prostředí.

## <a name="return-value"></a>Návratová hodnota

**_isctype** a **iswctype** vrací nenulovou hodnotu, pokud *c* má vlastnost určenou pomocí *DESC* v aktuálním národním prostředí nebo 0, pokud tomu tak není. Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předané národní prostředí namísto aktuálního národního prostředí pro své chování závislé na národním prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Chování **_isctype** a **_isctype_l** není definováno, pokud *c* není EOF nebo v rozsahu 0 až 0xFF (včetně). Pokud je použita knihovna CRT ladění a *c* není jedna z těchto hodnot, funkce vyvolá kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|není k dispozici|**_isctype**|není k dispozici|**_iswctype**|
|není k dispozici|**_isctype_l**|není k dispozici|**_iswctype_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_isctype**|\<CType. h >|
|**iswctype**|\<CType. h > nebo \<WCHAR. h >|
|**_isctype_l**|\<CType. h >|
|**_iswctype_l**|\<CType. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
