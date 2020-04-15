---
title: isalpha, iswalpha, _isalpha_l, _iswalpha_l
ms.date: 4/2/2020
api_name:
- iswalpha
- _iswalpha_l
- isalpha
- _isalpha_l
- _o_isalpha
- _o_iswalpha
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
- _istalpha
- _ismbcalpha_l
- isalpha
- _isalpha_l
- iswalpha
- _istalpha_l
- _iswalpha_l
helpviewer_keywords:
- _iswalpha_l function
- _isalpha_l function
- _ismbcalpha_l function
- _istalpha_l function
- _ismbcalpha function
- isalpha function
- iswalpha function
- istalpha function
- _istalpha function
ms.assetid: ed6cc2be-c4b0-4475-87ac-bc06d8c23064
ms.openlocfilehash: 187031adc0b22aff2c5418cd7e0f3e64075f1745
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343934"
---
# <a name="isalpha-iswalpha-_isalpha_l-_iswalpha_l"></a>isalpha, iswalpha, _isalpha_l, _iswalpha_l

Určuje, zda celé číslo představuje abecední znak.

## <a name="syntax"></a>Syntaxe

```C
int isalpha(
   int c
);
int iswalpha(
   wint_t c
);
int _isalpha_l(
   int c,
   _locale_t locale
);
int _iswalpha_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Celé číslo k testování.

*Národní prostředí*<br/>
Národní prostředí, které chcete použít namísto aktuálního národního prostředí.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou *hodnotu,* pokud c je určitá reprezentace abecedního znaku. **isalpha** vrátí nenulovou hodnotu, pokud *c* je v rozsahu A - Z nebo a - z. **iswalpha** vrátí nenulovou hodnotu pouze pro široké znaky, pro které [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) nebo **iswlower** je nenulová; to znamená, že pro libovolný široký znak, který je jedním z implementací definované sady, pro které žádný z **iswcntrl**, **iswdigit**, **iswpunct**, nebo **iswspace** je nenulová. Každá z těchto rutin vrátí hodnotu 0, pokud *c* nesplňuje zkušební podmínku.

Verze těchto funkcí, které mají **příponu _l** použít parametr národního prostředí, který je předán namísto aktuálního národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Chování **isalpha** a **_isalpha_l** je nedefinována, pokud *c* není EOF nebo v rozsahu 0 až 0xFF, včetně. Při ladění CRT knihovny a *c* není jednou z těchto hodnot, funkce vyvolat kontrolní výraz.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istalpha**|**isalpha**|**_ismbcalpha**|**iswalpha**|
|**_istalpha_l**|**_isalpha_l**|**_ismbcalpha_l**|**_iswalpha_l**|

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isalpha**|\<ctype.h>|
|**iswalpha**|\<ctype.h> \<nebo wchar.h>|
|**_isalpha_l**|\<ctype.h>|
|**_iswalpha_l**|\<ctype.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw Rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
