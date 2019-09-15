---
title: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
ms.date: 11/04/2016
api_name:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
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
ms.openlocfilehash: 6bf1109cfba93042bd00acde4812706c1bbf7a01
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952590"
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

*c*<br/>
Znak, který se má převést

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

V japonském národním prostředí tyto funkce vrátí převedený znak nebo vrátí hodnotu 0, pokud převod není možný. V nejaponském národním prostředí tyto funkce vrací předaný znak.

## <a name="remarks"></a>Poznámky

Funkce **_mbcjistojms** převede znak na standardu JIS (Japonsko Industry Standard) na znak Microsoft Kanji (Shift JIS). Znak je převeden pouze v případě, že jsou olovo a koncové bajty v rozsahu 0x21-0x7E. Pokud je vedoucí nebo zkušební bajt mimo tento rozsah, **errno** je nastaven na **EILSEQ**. Další informace o tomto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Funkce **_mbcjmstojis** převede znak Shift JIS na znak JIS. Znak je převeden pouze v případě, že je vedoucí bajt v rozsahu 0x81-0x9F nebo 0xE0-0xFC a koncový bajt je v rozsahu 0x40-0x7E nebo 0x80-0xFC. Všimněte si, že některé body kódu v tomto rozsahu nemají přiřazený znak, a proto je nelze převést.

Hodnota *c* by měla být 16bitová hodnota, jejíž horních 8 bitů představuje vedoucí bajt znaku, který má být převeden, a jehož dolních 8 bitů představuje koncový bajt.

Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md) . Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že místo toho používají předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V dřívějších verzích byly **_mbcjistojms** a **_mbcjmstojis** označovány jako **jistojms** a **jmstojis**, v uvedeném pořadí. místo toho by se měly použít **_mbcjistojms**, **_mbcjistojms_l**, **_mbcjmstojis** a **_mbcjmstojis_l** .

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbcjistojms**|\<Mbstring. h >|
|**_mbcjistojms_l**|\<Mbstring. h >|
|**_mbcjmstojis**|\<Mbstring. h >|
|**_mbcjmstojis_l**|\<Mbstring. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
