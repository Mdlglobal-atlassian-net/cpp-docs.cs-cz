---
title: _mbcjistojms –, _mbcjistojms_l –, _mbcjmstojis –, _mbcjmstojis_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07d34331e38362a6491e3231566443b5fe03260e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402425"
---
# <a name="mbcjistojms-mbcjistojmsl-mbcjmstojis-mbcjmstojisl"></a>_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l

Převede Japonsko oborový Standard (JIS) a Microsoft Japonsko (JMS) znaků.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Znak, který má převést.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

V japonské národním prostředí tyto funkce vrátí znak převedený nebo vrátí 0, pokud žádný převod je možné. Tyto funkce na národního prostředí není japonská, vrátí znak předaná.

## <a name="remarks"></a>Poznámky

**_Mbcjistojms –** funkce převádí znak Japonsko oborový Standard (JIS) na znak Kanji Microsoft (Shift JIS). Znak, který je převést pouze v případě, že realizace a záznam bajtů jsou v rozsahu 0x21 - 0x7E. Pokud je realizace nebo zkušební bajtů mimo tento rozsah **errno** je nastaven na **eilseq –**. Další informace o tomto a dalších kódy chyb najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**_Mbcjmstojis –** funkce převede znaků Shift JIS znaků JIS. Znak, který je převést pouze v případě, že úvodní bajt je v rozsahu 0x81-0x9F nebo 0xE0 - 0xFC a druhý bajt je v rozsahu 0x40-0x7E nebo 0x80 - 0xFC. Všimněte si, že nějaký kód body v této oblasti není obsahuje znak přiřazen a proto nelze převést.

Hodnota *c* musí být hodnota 16bitové, jehož horní 8 bitů představují úvodní bajt znaku převést a jehož nižších 8 bitů představují druhý bajt.

Výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

V dřívějších verzích **_mbcjistojms –** a **_mbcjmstojis –** měla volat **jistojms** a **jmstojis**, v uvedeném pořadí. **_mbcjistojms –**, **_mbcjistojms_l –**, **_mbcjmstojis –** a **_mbcjmstojis_l –** by měl být místo toho použít.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbcjistojms –**|\<Mbstring.h >|
|**_mbcjistojms_l**|\<Mbstring.h >|
|**_mbcjmstojis –**|\<Mbstring.h >|
|**_mbcjmstojis_l**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
