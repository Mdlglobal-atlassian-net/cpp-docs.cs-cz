---
title: _mbsbtype, _mbsbtype_l
ms.date: 11/04/2016
apiname:
- _mbsbtype_l
- _mbsbtype
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
ms.openlocfilehash: 5c2927b4e4b68b1284341fe7e767ec50feb21a44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331503"
---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype, _mbsbtype_l

Vrátí typ bajtu v rámci řetězce.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Adresa sekvence vícebajtových znaků.

*Počet*<br/>
Posun bajtu od záhlaví řetězce.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

**_mbsbtype –** a **_mbsbtype_l –** vrátí celočíselnou hodnotu označující výsledek testu na zadaném bajtu. Konstanty manifestu v následující tabulce jsou definovány v souboru Mbctype.h.

|Návratová hodnota|Byte – typ|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Jednobajtový znak. Například v kódové stránce 932 **_mbsbtype –** vrátí hodnotu 0, pokud je zadaný bajt rozsahu 0x20 – 0x7E nebo 0xA1 – 0xDF.|
|**_MBC_LEAD** (1)|Vedoucí bajt vícebajtového znaku. Například v kódové stránce 932 **_mbsbtype –** vrátí hodnotu 1, pokud je zadaný bajt rozsahu 0x81 – 0x9F nebo 0xE0 – 0xFC.|
|**_MBC_TRAIL** (2)|Koncový bajt vícebajtového znaku. Například v kódové stránce 932 **_mbsbtype –** vrací 2, pokud je zadaný bajt rozsahu 0x40 – 0x7E nebo 0x80 – 0xFC.|
|**_MBC_ILLEGAL** (-1)|**NULL** řetězec, neplatný znak nebo nulový bajt nalezený před bajtem na posunu *počet* v *mbstr*.|

## <a name="remarks"></a>Poznámky

**_Mbsbtype –** funkce určuje typ bajtu ve vícebajtovém znakovém řetězci. Funkce zkontroluje bajt na posunu *počet* v *mbstr*, ignoruje neplatné znaky před zadaným bajtem.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze této funkce bez **_l** příponu používá aktuální národní prostředí pro toto chování závislé na národním prostředí verze s **_l** přípona je identická s tím rozdílem, že používá Předaný parametr národního prostředí v místo. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud je vstupní řetězec **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **_MBC_ILLEGAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<Mbstring.h >|\<Mbctype.h > *|
|**_mbsbtype_l**|\<Mbstring.h >|\<Mbctype.h > *|

\* Konstanty manifestu používané jako vrácené hodnoty.

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
