---
title: isspace, iswspace, _isspace_l, _iswspace_l
ms.date: 11/04/2016
apiname:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
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
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: bb3d18e5034be50d69531d2686b6c270ba55a1cb
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210208"
---
# <a name="isspace-iswspace-isspacel-iswspacel"></a>isspace, iswspace, _isspace_l, _iswspace_l

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
Celé číslo k testování.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud *c* je konkrétní reprezentace znaku mezery. **isspace** vrací nenulovou hodnotu, pokud *c* je prázdný znak (0x09 – 0x0D nebo 0x20). Výsledek testovací podmínky pro **isspace** funkce závisí **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale _wsetlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí, které nemají **_l** používají aktuální národní prostředí pro všechna chování závislé na národním prostředí; ty, které mají **_l** přípona jsou stejné s tím rozdílem, že používají národní prostředí, které je předáno místo. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

**iswspace –** vrací nenulovou hodnotu, pokud *c* je široký znak který odpovídá standardnímu znaku prázdný znak.

Chování **isspace** a **_isspace_l –** není definováno, pokud *c* není konec souboru nebo v rozsahu 0 až 0xFF, včetně. Při použití ladicí CRT knihovny a *c* není jednou z těchto hodnot, funkce vyvolá kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istspace –**|**isspace**|[_ismbcspace](ismbcgraph-functions.md)|**iswspace**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isspace**|\<ctype.h>|
|**iswspace**|\<ctype.h > nebo \<wchar.h >|
|**_isspace_l**|\<ctype.h>|
|**_iswspace_l**|\<ctype.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
