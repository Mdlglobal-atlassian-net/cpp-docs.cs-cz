---
title: isspace, iswspace, _isspace_l, _iswspace_l
ms.date: 11/04/2016
api_name:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswspace
- _istspace
- isspace
helpviewer_keywords:
- iswspace function
- isspace function
- _iswspace_l function
- _isspace_l function
- iswspace_l function
- isspace_l function
- _istspace function
- istspace function
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
ms.openlocfilehash: b01aaf29ff0cd3994c45433db9ff0b9f4ca7481c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953649"
---
# <a name="isspace-iswspace-_isspace_l-_iswspace_l"></a>isspace, iswspace, _isspace_l, _iswspace_l

Určuje, zda celočíselná hodnota představuje znak mezery.

## <a name="syntax"></a>Syntaxe

```C
int isspace(
   int c
);
int iswspace(
   wint_t c
);
int _isspace_l(
   int c,
   _locale_t locale
);
int _iswspace_l(
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

Každá z těchto rutin vrátí nenulovou hodnotu, pokud je *c* konkrétní reprezentace znaku mezery. Když je *c* prázdným znakem (0X09-0x0D nebo 0x20) **, vrátí** nenulovou hodnotu. Výsledek testovací podmínky pro funkci **inspace** závisí na nastavení kategorie **LC_CTYPE** národního prostředí; Další informace najdete v tématu [setlocale, _wsetlocale](setlocale-wsetlocale.md) . Verze těchto funkcí, které nemají příponu **_l** , používají aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; verze, které mají příponu **_l** , jsou stejné s tím rozdílem, že používají národní prostředí, které je předáno místo toho. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

**iswspace** vrací nenulovou hodnotu, pokud je *c* je celosvětový znak, který odpovídá standardnímu prázdnému znaku.

Chování funkce- **Space** a **_isspace_l** není definováno, pokud *c* není EOF nebo v rozsahu 0 až 0xFF (včetně). Pokud je použita knihovna CRT ladění a *c* není jedna z těchto hodnot, funkce vyvolá kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istspace**|**isspace**|[_ismbcspace](ismbcgraph-functions.md)|**iswspace**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isspace**|\<CType. h >|
|**iswspace**|\<CType. h > nebo \<WCHAR. h >|
|**_isspace_l**|\<CType. h >|
|**_iswspace_l**|\<CType. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
