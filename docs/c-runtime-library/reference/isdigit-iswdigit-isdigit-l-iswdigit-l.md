---
title: isdigit, iswdigit, _isdigit_l, _iswdigit_l
ms.date: 4/2/2020
api_name:
- _isdigit_l
- iswdigit
- _iswdigit_l
- isdigit
- _o_isdigit
- _o_iswdigit
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _iswdigit_l
- _isdigit_l
- iswdigit
- isdigit
- _istdigit
- _istdigit_l
helpviewer_keywords:
- iswdigit function
- iswdigit_l function
- _iswdigit_l function
- _istdigit_l function
- _istdigit function
- istdigit function
- isdigit function
- isdigit_l function
- _ismbcdigit_l function
- _isdigit_l function
ms.assetid: 350b0093-843a-47b0-954e-c1776e8a3853
ms.openlocfilehash: 70a370068ca05c430845a8eba83a73498384b067
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917590"
---
# <a name="isdigit-iswdigit-_isdigit_l-_iswdigit_l"></a>isdigit, iswdigit, _isdigit_l, _iswdigit_l

Určuje, zda celočíselná hodnota představuje znak desítkové číslice.

## <a name="syntax"></a>Syntaxe

```C
int isdigit(
   int c
);
int iswdigit(
   wint_t c
);
int _isdigit_l(
   int c,
   _locale_t locale
);
int _iswdigit_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*r*<br/>
Celé číslo k otestování.

*locale*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud je *c* konkrétní reprezentace znaku desítkové číslice. hodnota- **číslice** vrátí nenulovou hodnotu, pokud je *c* desítková číslice (0-9). **iswdigit** vrací nenulovou hodnotu, pokud je *c* je celosvětový znak, který odpovídá znaku desítkové číslice. Každá z těchto rutin vrátí hodnotu 0, pokud *c* nesplňuje podmínky testu.

Verze těchto funkcí, které mají příponu **_l** , používají národní prostředí, které je předáno namísto aktuálního národního prostředí pro své chování závislé na národním prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Chování funkce- **číslice** a **_isdigit_l** není definováno, pokud *c* není EOF nebo v rozsahu 0 až 0xFF (včetně). Pokud je použita knihovna CRT ladění a *c* není jedna z těchto hodnot, funkce vyvolá kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istdigit**|**IsDigit**|[_ismbcdigit](ismbcalnum-functions.md)|**iswdigit**|
|**_istdigit_l**|**_isdigit_l**|[_ismbcdigit_l](ismbcalnum-functions.md)|**_iswdigit_l**|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**IsDigit**|\<CType. h>|
|**iswdigit**|\<CType. h> nebo \<WCHAR. h>|
|**_isdigit_l**|\<CType. h>|
|**_iswdigit_l**|\<CType. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[je, rutiny ISW](../../c-runtime-library/is-isw-routines.md)<br/>
