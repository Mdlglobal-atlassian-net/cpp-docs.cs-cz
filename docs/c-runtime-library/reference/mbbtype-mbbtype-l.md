---
title: _mbbtype, _mbbtype_l
ms.date: 11/04/2016
apiname:
- _mbbtype
- _mbbtype_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: a6d17b99e4314c2ab836a16129ab8a0e6ac7720e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467168"
---
# <a name="mbbtype-mbbtypel"></a>_mbbtype, _mbbtype_l

Vrátí typ bajtu podle předchozí bajtů.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*c*<br/>
Znak k testování.

*Typ*<br/>
Typ bajtu pro test.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**_mbbtype –** vrátí typ bajtu v řetězci. Toto rozhodnutí je kontextové, jak je uvedeno hodnotou *typ*, který obsahuje testovací podmínku ovládacího prvku. *typ* je typ předchozí bajtů v řetězci. Konstanty manifestu v následující tabulce jsou definovány v souboru Mbctype.h.

|Hodnota *typu*|**_mbbtype –** testy pro|Návratová hodnota|*c*|
|---------------------|--------------------------|------------------|---------|
|Žádná hodnota kromě 1|Platný jednobajtový nebo vedoucí bajt|**_MBC_SINGLE** (0)|Jeden bajt (0x20 – 0x7E, 0xA1 – 0xDF)|
|Žádná hodnota kromě 1|Platný jednobajtový nebo vedoucí bajt|**_MBC_LEAD** (1)|Vedoucí bajt vícebajtového znaku (0x81 – 0x9F, 0xE0 – 0xFC)|
|Žádná hodnota kromě 1|Platný jednobajtové nebo vedoucí bajt|**_MBC_ILLEGAL**<br /><br /> ( -1)|Neplatný znak (všechny hodnoty s výjimkou 0x20 – 0x7E, 0xA1 – 0xDF, 0x81 – 0x9F, 0xE0 – 0xFC|
|1|Platný bajt|**_MBC_TRAIL** (2)|Koncový bajt vícebajtového znaku (0x40 – 0x7E, 0x80 – 0xFC)|
|1|Platný bajt|**_MBC_ILLEGAL**<br /><br /> ( -1)|Neplatný znak (všechny hodnoty s výjimkou 0x20 – 0x7E, 0xA1 – 0xDF, 0x81 – 0x9F, 0xE0 – 0xFC|

## <a name="remarks"></a>Poznámky

**_Mbbtype –** funkce určuje typ bajtu ve vícebajtovém znaku. Pokud hodnota *typ* je libovolná hodnota s výjimkou 1, **_mbbtype –** testy pro platné jednobajtové nebo vedoucí bajt vícebajtového znaku. Pokud hodnota *typ* 1, **_mbbtype –** testy pro platný bajt vícebajtového znaku.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale _wsetlocale](setlocale-wsetlocale.md) Další informace. **_Mbbtype –** verze této funkce používá aktuální národní prostředí pro toto chování závislé na národním prostředí **_mbbtype_l –** verze je stejná s tím rozdílem, že používá parametr národního prostředí, které je předáno místo . Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V dřívějších verzích **_mbbtype –** označovala jako **chkctype**. Pro nový kód, použijte **_mbbtype –** místo.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_mbbtype –**|\<Mbstring.h >|\<Mbctype.h > *|
|**_mbbtype_l**|\<Mbstring.h >|\<Mbctype.h > *|

\* Definice konstanty manifestu používané jako vrácené hodnoty.

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
