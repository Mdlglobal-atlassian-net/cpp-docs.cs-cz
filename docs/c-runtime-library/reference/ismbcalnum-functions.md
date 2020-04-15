---
title: _ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l
ms.date: 4/2/2020
api_name:
- _ismbcalpha
- _ismbcalnum
- _ismbcdigit
- _ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha_l
- _o__ismbcalnum
- _o__ismbcalnum_l
- _o__ismbcalpha
- _o__ismbcalpha_l
- _o__ismbcdigit
- _o__ismbcdigit_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbcdigit
- ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha
- ismbcalnum
- ismbcdigit
- ismbcalpha
- _ismbcalnum_l
- _ismbcalnum
- ismbcdigit_l
helpviewer_keywords:
- ismbcalpha function
- _ismbcalnum function
- ismbcdigit_l function
- _ismbcalnum_l function
- _ismbcdigit function
- ismbcalnum function
- _ismbcalpha_l function
- ismbcdigit function
- _ismbcalpha function
- _ismbcdigit_l function
- ismbcalnum_l function
- ismbcalpha_l function
ms.assetid: 12d57925-aebe-46e0-80b0-82b84c4c31ec
ms.openlocfilehash: 828c8b68855197f0c17202739f98a45e0abb929c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343310"
---
# <a name="_ismbcalnum-_ismbcalnum_l-_ismbcalpha-_ismbcalpha_l-_ismbcdigit-_ismbcdigit_l"></a>_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l

Zkontroluje, zda je vícebajtový znak alfanumerický, alfa nebo číslicový znak.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbcalnum
(
   unsigned int c
);
int _ismbcalnum_l
(
   unsigned int c,
   _locale_t locale
);
int _ismbcalpha
(
   unsigned int c
);
int _ismbcalpha_l
(
   unsigned int c,
   _locale_t locale
);
int _ismbcdigit
(
   unsigned int c
);
int _ismbcdigit_l
(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Znak, který má být testován.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud znak splňuje testovací podmínku, nebo 0, pokud tomu tak není. Pokud *c*<= 255 a existuje odpovídající **rutina _ismbb** (například **_ismbcalnum** odpovídá **_ismbbalnum**), výsledkem je vrácená hodnota odpovídající **_ismbb** rutiny.

## <a name="remarks"></a>Poznámky

Každá z těchto rutin testuje daný vícebajtový znak pro danou podmínku.

Verze těchto funkcí s **příponou _l** jsou identické s tím rozdílem, že používají národní prostředí předané namísto aktuálního národního prostředí pro jejich chování závislé na národním prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

|Rutina|Zkušební podmínka|Příklad znakové stránky 932|
|-------------|--------------------|---------------------------|
|**_ismbcalnum** **, _ismbcalnum_l**|Alfanumerické znaky|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtovou reprezentací anglického písmene ASCII: Viz příklady pro **_ismbcdigit** a **_ismbcalpha**.|
|**_ismbcalpha**, **_ismbcalpha_l**|Abecedy|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtová reprezentace anglického písmene ASCII: 0x41<=*c*<=0x5A nebo 0x61<=*c*<=0x7A; nebo písmeno katakana: 0xA6<=*c*<=0xDF.|
|**_ismbcdigit**, **_ismbcdigit**|Číslice|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtová reprezentace číslice ASCII: 0x30<=*c*<=0x39.|

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbcalnum** **, _ismbcalnum_l**|\<mbstring.h>|
|**_ismbcalpha**, **_ismbcalpha_l**|\<mbstring.h>|
|**_ismbcdigit**, **_ismbcdigit_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw Rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
