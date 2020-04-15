---
title: _mbsbtype, _mbsbtype_l
ms.date: 4/2/2020
api_name:
- _mbsbtype_l
- _mbsbtype
- _o__mbsbtype
- _o__mbsbtype_l
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
ms.openlocfilehash: d71a061d9af5028c9bc6b4008f9904606a233592
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340875"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype, _mbsbtype_l

Vrátí typ bajtu v řetězci.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*mbstr*<br/>
Adresa posloupnosti vícebajtových znaků.

*Počet*<br/>
Posun bajtu od hlavy řetězce.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**_mbsbtype** a **_mbsbtype_l** vrátí hodnotu celé číslo označující výsledek testu na určeném bajtu. Konstanty manifestu v následující tabulce jsou definovány v souboru Mbctype.h.

|Návratová hodnota|Typ bajtu|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Jednobajtový znak. Například v znakové stránce 932 **_mbsbtype** vrátí 0, pokud je zadaný bajt v rozsahu 0x20 - 0x7E nebo 0xA1 - 0xDF.|
|**_MBC_LEAD** (1)|Úvodní bajt vícebajtového znaku. Například v znakové stránce 932 **vrátí _mbsbtype** 1, pokud je zadaný bajt v rozsahu 0x81 - 0x9F nebo 0xE0 - 0xFC.|
|**_MBC_TRAIL** (2)|Koncový bajt vícebajtového znaku. Například v znakové stránce 932 **vrátí _mbsbtype** 2, pokud je zadaný bajt v rozsahu 0x40 - 0x7E nebo 0x80 - 0xFC.|
|**_MBC_ILLEGAL** (-1)|**Null** řetězec, neplatný znak nebo nulový bajt nalezen před bajtem při *počtu posunů* v *mbstr*.|

## <a name="remarks"></a>Poznámky

Funkce **_mbsbtype** určuje typ bajtu v vícebajtovém znakovém řetězci. Funkce zkoumá pouze bajt při *počtu posunů* v *mbstr*a ignoruje neplatné znaky před určeným bajtem.

Výstupní hodnota je ovlivněna nastavením nastavení **LC_CTYPE** kategorie národního prostředí; další informace naleznete [v tématu setlocale.](setlocale-wsetlocale.md) Verze této funkce bez **_l** přípony používá aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s **příponou _l** je identická s tím rozdílem, že místo toho používá parametr národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Pokud je vstupní řetězec **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **_MBC_ILLEGAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\*Pro konstanty manifestu používané jako vrácené hodnoty.

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
