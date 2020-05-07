---
title: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
ms.date: 4/2/2020
api_name:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
- _o__mbcjistojms
- _o__mbcjistojms_l
- _o__mbcjmstojis
- _o__mbcjmstojis_l
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
- mbcjistojms
- _mbcjistojms
- _mbcjistojms_l
- _mbcjmstojis_l
- _mbcjmstojis
- mbcjmstojis_l
- mbcjistojms_l
- mbcjmstojis
helpviewer_keywords:
- _mbcjmstojis_l function
- _mbcjistojms function
- mbcjmstojis function
- _mbcjistojms_l function
- _mbcjmstojis function
- mbcjistojms function
- mbcjmstojis_l function
- mbcjistojms_l function
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
ms.openlocfilehash: fc4df04274c33fa14af0762dc62f20ed09f23cd9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918428"
---
# <a name="_mbcjistojms-_mbcjistojms_l-_mbcjmstojis-_mbcjmstojis_l"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l

Převádí se mezi JMS znaky z Japonska (Japonsko Industry Standard) a Japonsko (Microsoft).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _mbcjistojms(
   unsigned int c
);
unsigned int _mbcjistojms_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbcjmstojis(
   unsigned int c
);
unsigned int _mbcjmstojis_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*r*<br/>
Znak, který se má převést

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

V japonském národním prostředí tyto funkce vrátí převedený znak nebo vrátí hodnotu 0, pokud převod není možný. V nejaponském národním prostředí tyto funkce vrací předaný znak.

## <a name="remarks"></a>Poznámky

Funkce **_mbcjistojms** převede znak na standardu JIS (Japonsko Industry Standard) na znak Microsoft Kanji (Shift JIS). Znak je převeden pouze v případě, že jsou olovo a koncové bajty v rozsahu 0x21-0x7E. Pokud je vedoucí nebo zkušební bajt mimo tento rozsah, **errno** je nastaven na **EILSEQ**. Další informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Funkce **_mbcjmstojis** převede znak Shift JIS na znak JIS. Znak je převeden pouze v případě, že je vedoucí bajt v rozsahu 0x81-0x9F nebo 0xE0-0xFC a koncový bajt je v rozsahu 0x40-0x7E nebo 0x80-0xFC. Všimněte si, že některé body kódu v tomto rozsahu nemají přiřazený znak, a proto je nelze převést.

Hodnota *c* by měla být 16bitová hodnota, jejíž horních 8 bitů představuje vedoucí bajt znaku, který má být převeden, a jehož dolních 8 bitů představuje koncový bajt.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** kategorie národního prostředí; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md) . Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V dřívějších verzích se **_mbcjistojms** a **_mbcjmstojis** volala v uvedeném pořadí jako **jistojms** a **jmstojis**. místo toho by se měly použít **_mbcjistojms**, **_mbcjistojms_l**, **_mbcjmstojis** a **_mbcjmstojis_l** .

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbcjistojms**|\<Mbstring. h>|
|**_mbcjistojms_l**|\<Mbstring. h>|
|**_mbcjmstojis**|\<Mbstring. h>|
|**_mbcjmstojis_l**|\<Mbstring. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Rutiny _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
