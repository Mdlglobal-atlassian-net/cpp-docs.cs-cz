---
title: _mbctombb –, _mbctombb_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbctombb_l
- _mbctombb
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
- _mbctombb_l
- _mbctombb
- mbctombb_l
- mbctombb
dev_langs:
- C++
helpviewer_keywords:
- _mbctombb function
- mbctombb_l function
- mbctombb function
- _mbctombb_l function
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adb233b489b5f4c190a4015805b07ab36770a283
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="mbctombb-mbctombbl"></a>_mbctombb, _mbctombb_l

Převede na odpovídající vícebajtových znaků jednobajtové dvoubajtové vícebajtových znaků.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _mbctombb(
   unsigned int c
);
unsigned int _mbctombb_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Vícebajtové znakové převést.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného **_mbctombb –** a **_mbctombb_l –** vrátí jednobajtové znak, který odpovídá *c*; v opačném případě vrátí *c* .

## <a name="remarks"></a>Poznámky

**_Mbctombb –** a **_mbctombb_l –** funkce převést na odpovídající vícebajtových znaků jednobajtové dané vícebajtových znaků. Znaky musí odpovídat jednobajtové znaky v rozsahu 0x20-0x7E nebo 0xA1 - 0xDF má být převeden.

Výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze této funkce bez **_l** příponu používá aktuální národní prostředí pro toto chování závislých na národním prostředí; na verzi s **_l** přípona se shoduje s tím rozdílem, že se používat Předaný parametr národního prostředí v místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

V předchozích verzích **_mbctombb –** byla volána **zentohan**. Použití **_mbctombb –** místo.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbctombb –**|\<Mbstring.h >|
|**_mbctombb_l**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[_mbbtombc, _mbbtombc_l](mbbtombc-mbbtombc-l.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)<br/>
[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
