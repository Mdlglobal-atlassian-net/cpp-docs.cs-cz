---
title: isprint, iswprint, _isprint_l, _iswprint_l
ms.date: 11/04/2016
apiname:
- iswprint
- isprint
- _isprint_l
- _iswprint_l
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
ms.openlocfilehash: aab604076f8a2e2eee0eefe20f08f46ae5388a34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157195"
---
# <a name="isprint-iswprint-isprintl-iswprintl"></a>isprint, iswprint, _isprint_l, _iswprint_l

Určuje, zda celočíselná hodnota představuje tisknutelný znak.

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

*c*<br/>
Celé číslo k testování.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud *c* je konkrétní reprezentace tisknutelného znaku. **isprint** vrací nenulovou hodnotu, pokud *c* je tisknutelný znak – jedná se o znak mezery (0x20 – 0x7E). **iswprint –** vrací nenulovou hodnotu, pokud *c* je tisknutelný široký znak – jedná se o širokého znaku mezery. Každá z těchto rutin vrátí hodnotu 0, pokud *c* nesplňuje testovací podmínku.

Výsledek testovací podmínky pro tyto funkce závisí **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale _wsetlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí, které nemají **_l** používají aktuální národní prostředí pro všechna chování závislé na národním prostředí; ty, které mají **_l** přípona jsou stejné s tím rozdílem, že používají národní prostředí, které je předáno místo. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Chování **isprint** a **_isprint_l –** není definováno, pokud *c* není konec souboru nebo v rozsahu 0 až 0xFF, včetně. Při použití ladicí CRT knihovny a *c* není jednou z těchto hodnot, funkce vyvolá kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istprint**|**isprint**|[_ismbcprint](ismbcgraph-functions.md)|**iswprint**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isprint**|\<ctype.h>|
|**iswprint**|\<ctype.h > nebo \<wchar.h >|
|**_isprint_l**|\<ctype.h>|
|**_iswprint_l**|\<ctype.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
