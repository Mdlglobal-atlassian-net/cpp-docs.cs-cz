---
title: islower, iswlower, _islower_l, _iswlower_l
ms.date: 11/04/2016
apiname:
- iswlower
- _islower_l
- islower
- _iswlower_l
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
- _istlower
- islower
- _ismbclower_l
- _liswlower_l
- _istlower_l
- _iswlower_l
- _islower _l
- _islower_l
- iswlower
helpviewer_keywords:
- _islower _l function
- _ismbclower_l function
- islower function
- _iswlower_l function
- _liswlower_l function
- _istlower_l function
- istlower function
- _istlower function
- iswlower function
- _islower_l function
ms.assetid: fcc3b70a-2b47-45fd-944d-e5c1942e6457
ms.openlocfilehash: b6b58522277b45fe8147dfa13a5930003f83c835
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331568"
---
# <a name="islower-iswlower-islowerl-iswlowerl"></a>islower, iswlower, _islower_l, _iswlower_l

Určuje, zda celočíselná hodnota představuje znak malého písmene.

## <a name="syntax"></a>Syntaxe

```C
int islower(
   int c
);
int iswlower(
   wint_t c
);
int islower_l(
   int c,
   _locale_t locale
);
int _iswlower_l(
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

Každá z těchto rutin vrátí nenulovou hodnotu, pokud *c* je konkrétní reprezentace malého znaku. **islower** vrací nenulovou hodnotu, pokud *c* je znak malého písmene (a – z). **iswlower –** vrací nenulovou hodnotu, pokud *c* je široký znak který odpovídá znaku malého písmene, nebo pokud *c* je jednou ze sad definovaných implementací širokých znaků, pro kterou žádná z hodnot **iswcntrl –**, **iswdigit –**, **iswpunct –**, nebo **iswspace –** nenulové. Každá z těchto rutin vrátí hodnotu 0, pokud *c* nesplňuje testovací podmínku.

Verze těchto funkcí, které mají **_l** příponu použít předané národní prostředí namísto aktuálního národního prostředí pro své chování závislé na národním prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Chování **islower** a **_islower_l –** není definováno, pokud *c* není konec souboru nebo v rozsahu 0 až 0xFF, včetně. Při použití ladicí CRT knihovny a *c* není jednou z těchto hodnot, funkce vyvolá kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istlower**|**islower**|[_ismbclower](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**iswlower**|
|**_istlower_l**|`_islower _l`|[_ismbclower_l](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**_liswlower_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**islower**|\<ctype.h>|
|**iswlower**|\<ctype.h > nebo \<wchar.h >|
|**_islower_l**|\<ctype.h>|
|**_swlower_l**|\<ctype.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
