---
title: _mbbtype, _mbbtype_l
ms.date: 11/04/2016
api_name:
- _mbbtype
- _mbbtype_l
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
ms.openlocfilehash: ba4311921a0924d3f447feb1929a81ae1d816604
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952726"
---
# <a name="_mbbtype-_mbbtype_l"></a>_mbbtype, _mbbtype_l

Vrátí typ Byte na základě předchozího bajtu.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Testovaný znak.

*type*<br/>
Typ bajtu, který se má testovat.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**_mbbtype** vrací typ bajtu v řetězci. Toto rozhodnutí je závislé na kontextu, jak je určeno hodnotou *typu*, která poskytuje podmínku kontrolního testu. *typ* je typ předchozího bajtu v řetězci. Konstanty manifestu v následující tabulce jsou definovány v Mbctype. h.

|Hodnota *typu*|**_mbbtype** testy pro|Návratová hodnota|*c*|
|---------------------|--------------------------|------------------|---------|
|Libovolná hodnota kromě 1|Platný jeden bajt nebo vedoucí bajt|**_MBC_SINGLE** (0)|Jednobajtové (0x20-0x7E, 0xA1-0xDF)|
|Libovolná hodnota kromě 1|Platný jeden bajt nebo vedoucí bajt|**_MBC_LEAD** (1)|Vedoucí bajt vícebajtového znaku (0x81-0x9F, 0xE0-0xFC)|
|Libovolná hodnota kromě 1|Platný jednobajtové nebo vedoucí bajt|**_MBC_ILLEGAL**<br /><br /> ( -1)|Neplatný znak (jakákoli hodnota kromě 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, 0xE0-0xFC|
|1|Platný koncový bajt|**_MBC_TRAIL** (2)|Koncový bajt vícebajtového znaku (0x40-0x7E, 0x80-0xFC)|
|1|Platný koncový bajt|**_MBC_ILLEGAL**<br /><br /> ( -1)|Neplatný znak (jakákoli hodnota kromě 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, 0xE0-0xFC|

## <a name="remarks"></a>Poznámky

Funkce **_mbbtype** určuje typ bajtu v vícebajtovém znaku. Pokud je hodnota *typu* libovolná hodnota kromě 1, **_mbbtype** testy pro platný jednobajtové nebo vedoucí bajt vícebajtového znaku. Pokud je hodnota *typu* 1, **_mbbtype** testy pro platný koncový bajt vícebajtového znaku.

Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí; Další informace najdete v tématu [setlocale, _wsetlocale](setlocale-wsetlocale.md) . Verze **_mbbtype** této funkce používá aktuální národní prostředí pro toto chování závislé na národním prostředí; verze **_mbbtype_l** je shodná s tím rozdílem, že místo toho používá parametr národního prostředí, který je předán. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V dřívějších verzích se **_mbbtype** jmenovala **chkctype**. Pro nový kód použijte místo toho **_mbbtype** .

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<Mbstring. h >|\<Mbctype. h > *|
|**_mbbtype_l**|\<Mbstring. h >|\<Mbctype. h > *|

\*Pro definice konstant manifestů, které jsou používány jako návratové hodnoty.

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
