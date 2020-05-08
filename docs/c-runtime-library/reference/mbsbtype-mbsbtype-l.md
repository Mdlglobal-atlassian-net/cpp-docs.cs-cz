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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c1431a2d0886ffd3d16b43abf82b7342c166273a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909470"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype, _mbsbtype_l

Vrátí typ bajtu v rámci řetězce.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*výpočtu*<br/>
Posun bajtů od hlavičky řetězce

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**_mbsbtype** a **_mbsbtype_l** vrací celočíselnou hodnotu označující výsledek testu na zadaném bajtu. Konstanty manifestu v následující tabulce jsou definovány v Mbctype. h.

|Návratová hodnota|Typ bajtu|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Jednobajtové znak. Například v kódové stránce 932 **_mbsbtype** vrátí hodnotu 0, pokud je zadaný bajt v rozsahu 0X20-0X7e nebo 0XA1-0xDF.|
|**_MBC_LEAD** (1)|Vedoucí bajt vícebajtového znaku. Například v kódové stránce 932 **_mbsbtype** vrátí hodnotu 1, pokud je zadaný bajt v rozsahu 0X81-0X9f nebo 0XE0-0xFC.|
|**_MBC_TRAIL** (2)|Koncový bajt vícebajtového znaku. Například v kódové stránce 932 **_mbsbtype** vrátí hodnotu 2, pokud je zadaný bajt v rozsahu 0X40-0x7E nebo 0X80-0xFC.|
|**_MBC_ILLEGAL** (-1)|Před bajtem *na posunu* v *mbstr*byl nalezen řetězec s **hodnotou null** , neplatný znak nebo bajt s hodnotou null.|

## <a name="remarks"></a>Poznámky

Funkce **_mbsbtype** určuje typ bajtu v vícebajtovém řetězci znaků. Funkce kontroluje pouze bajt v *počtu* posunu v *mbstr*a ignoruje neplatné znaky před zadaným bajtem.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** kategorie národního prostředí; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md) . Verze této funkce bez přípony **_l** používá aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** je shodná s tím rozdílem, že místo toho používá parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud je vstupní řetězec **null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **_MBC_ILLEGAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<Mbstring. h>|\<Mbctype. h> *|
|**_mbsbtype_l**|\<Mbstring. h>|\<Mbctype. h> *|

\*Pro konstanty manifestu použité jako návratové hodnoty.

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
