---
title: isalnum, iswalnum, _isalnum_l, _iswalnum_l
ms.date: 11/04/2016
api_name:
- _iswalnum_l
- _isalnum_l
- iswalnum
- isalnum
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
- _istalnum_l
- _iswalnum_l
- iswalnum
- _isalnum_l
- isalnum
- _istalnum
helpviewer_keywords:
- _istalnum function
- _ismbcalnum_l function
- iswalnum function
- isalnum function
- istalnum function
- _isalnum_l function
- _istalnum_l function
- _iswalnum_l function
ms.assetid: 0dc51306-ade8-4944-af27-e4176fc89093
ms.openlocfilehash: 636e43a921c2b859db3a31b3dd658112f4e8e9f4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954589"
---
# <a name="isalnum-iswalnum-_isalnum_l-_iswalnum_l"></a>isalnum, iswalnum, _isalnum_l, _iswalnum_l

Určuje, zda celočíselná hodnota představuje alfanumerický znak.

## <a name="syntax"></a>Syntaxe

```C
int isalnum( int c );
int iswalnum( wint_t c );
int _isalnum_l( int c,  _locale_t locale );
int _iswalnum_l( wint_t c, _locale_t locale );
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo k otestování.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud je *c* konkrétní reprezentace alfanumerického znaku. **isalnum** vrací nenulovou hodnotu, pokud je parametrem " **Alpha** **" nebo "** nenulová" hodnota " *c*", to znamená, pokud je *c* v rozsahu od a-Z, a-z nebo 0-9. **iswalnum** vrací nenulovou hodnotu, pokud buď **iswalpha** nebo **iswdigit** není nula pro *c*. Každá z těchto rutin vrátí hodnotu 0, pokud *c* nesplňuje podmínky testu.

Verze těchto funkcí, které mají příponu **_l** , používají parametr národního prostředí, který je předaný namísto aktuálního národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Chování **isalnum** a **_isalnum_l** není definováno, pokud *c* není EOF nebo v rozsahu 0 až 0xFF (včetně). Pokud je použita knihovna CRT ladění a *c* není jedna z těchto hodnot, funkce vyvolá kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istalnum**|**isalnum**|[_ismbcalnum](ismbcalnum-functions.md)|**iswalnum**|
|**_istalnum_l**|**_isalnum_l**|**_ismbcalnum_l**|**_iswalnum_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isalnum**|\<CType. h >|
|**iswalnum**|\<CType. h > nebo \<WCHAR. h >|
|**_isalnum_l**|\<CType. h >|
|**_iswalnum_l**|\<CType. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
