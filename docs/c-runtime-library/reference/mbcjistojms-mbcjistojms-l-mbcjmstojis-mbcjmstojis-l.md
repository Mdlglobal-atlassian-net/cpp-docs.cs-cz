---
title: _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
ms.date: 11/04/2016
apiname:
- _mbcjistojms
- _mbcjmstojis
- _mbcjistojms_l
- _mbcjmstojis_l
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
ms.openlocfilehash: 22cf8eeb5f99b6abee624aa3b1d06246d7230652
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665891"
---
# <a name="mbcjistojms-mbcjistojmsl-mbcjmstojis-mbcjmstojisl"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l

Převede mezi znaky Japonsko průmyslové normy (JIS) a Japan Microsoft (JMS).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Znak pro převod.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

V japonském národním prostředí tyto funkce vrací převedený znak nebo vrátí 0, pokud převod není možný. Na jiném než japonském národním prostředí tyto funkce vrátí zadaný znak.

## <a name="remarks"></a>Poznámky

**_Mbcjistojms –** funkce převede znak Japonsko průmyslové normy (JIS) na znak Microsoft Kanji (Shift JIS). Znak je převeden pouze v případě, že vedoucí a bajty jsou v rozsahu 0x21 – 0x7E. Li vedoucí nebo zkušební bajt mimo tento rozsah **errno** je nastavena na **EILSEQ**. Další informace o tomto a dalších chybových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**_Mbcjmstojis –** funkce převede znak Shift JIS na znak JIS. Znak je převeden pouze v případě, že vedoucí bajt je v rozsahu 0x81 – 0x9F nebo 0xE0 – 0xFC a druhý bajt je v rozsahu 0x40 – 0x7E nebo 0x80 – 0xFC. Všimněte si, že některé body kódu v tom, že rozsahu nemají přiřazený znak a proto je nelze převést.

Hodnota *c* by měla být 16bitová hodnota, jejíž horních 8 bitů představuje vedoucí bajt znak pro převod a jehož dolních 8 bitů představuje druhý bajt.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí bez **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí místo něho předán v. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V dřívějších verzích **_mbcjistojms –** a **_mbcjmstojis –** byly volány **jistojms** a **jmstojis**v uvedeném pořadí. **_mbcjistojms –**, **_mbcjistojms_l –**, **_mbcjmstojis –** a **_mbcjmstojis_l –** by místo toho používat.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbcjistojms –**|\<Mbstring.h >|
|**_mbcjistojms_l**|\<Mbstring.h >|
|**_mbcjmstojis –**|\<Mbstring.h >|
|**_mbcjmstojis_l**|\<Mbstring.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
