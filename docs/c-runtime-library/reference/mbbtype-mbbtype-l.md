---
title: _mbbtype, _mbbtype_l
ms.date: 4/2/2020
api_name:
- _mbbtype
- _mbbtype_l
- _o__mbbtype
- _o__mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
ms.openlocfilehash: 7e2e818ed70ec393e4f81008f76ca9efe9cfa7e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341402"
---
# <a name="_mbbtype-_mbbtype_l"></a>_mbbtype, _mbbtype_l

Vrátí typ bajtů na základě předchozího bajtu.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _mbbtype(
   unsigned char c,
   int type
);
int _mbbtype_l(
   unsigned char c,
   int type,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Znak k testování.

*Typ*<br/>
Typ bajtu, pro který chcete testovat.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**_mbbtype** vrátí typ bajtu v řetězci. Toto rozhodnutí je kontextově závislé, jak je určeno hodnotou *typu*, která poskytuje podmínku kontrolního testu. *type* je typ předchozího bajtu v řetězci. Konstanty manifestu v následující tabulce jsou definovány v souboru Mbctype.h.

|Hodnota *typu*|**_mbbtype** testy pro|Návratová hodnota|*C*|
|---------------------|--------------------------|------------------|---------|
|Libovolná hodnota kromě 1|Platný jednobajtový nebo hlavní bajt|**_MBC_SINGLE** (0)|Jeden bajt (0x20 - 0x7E, 0xA1 - 0xDF)|
|Libovolná hodnota kromě 1|Platný jednobajtový nebo hlavní bajt|**_MBC_LEAD** (1)|Olověný bajt vícebajtového znaku (0x81 - 0x9F, 0xE0 - 0xFC)|
|Libovolná hodnota kromě 1|Platný jednobajtové nebo hlavní bajt|**_MBC_ILLEGAL**<br /><br /> ( -1)|Neplatný znak (libovolná hodnota kromě 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|
|1|Platný bajt trasy|**_MBC_TRAIL** (2)|Koncový bajt vícebajtového znaku (0x40 - 0x7E, 0x80 - 0xFC)|
|1|Platný bajt trasy|**_MBC_ILLEGAL**<br /><br /> ( -1)|Neplatný znak (libovolná hodnota kromě 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|

## <a name="remarks"></a>Poznámky

Funkce **_mbbtype** určuje typ bajtu v vícebajtovém znaku. Pokud je hodnota *typu* libovolná hodnota s výjimkou 1, **_mbbtype** testy platného jednobajtového nebo úvodního bajtu vícebajtového znaku. Pokud je hodnota *typu* 1, **_mbbtype** testy platného bajtu stopy vícebajtového znaku.

Výstupní hodnota je ovlivněna nastavením nastavení **LC_CTYPE** kategorie národního prostředí; další informace naleznete [v _wsetlocale setlocale.](setlocale-wsetlocale.md) Verze **_mbbtype** této funkce používá aktuální národní prostředí pro toto chování závislé na národním prostředí; **verze _mbbtype_l** je identická s tím rozdílem, že místo toho používá parametr národního prostředí, který je předán. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

V dřívějších verzích byl **_mbbtype** pojmenován **chkctype**. Pro nový kód použijte místo toho **_mbbtype.**

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\*Pro definice konstant manifestu, které se používají jako vrácené hodnoty.

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
