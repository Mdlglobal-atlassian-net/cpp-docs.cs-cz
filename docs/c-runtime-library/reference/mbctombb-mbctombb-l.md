---
title: _mbctombb, _mbctombb_l
ms.date: 11/04/2016
api_name:
- _mbctombb_l
- _mbctombb
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
- _mbctombb_l
- _mbctombb
- mbctombb_l
- mbctombb
helpviewer_keywords:
- _mbctombb function
- mbctombb_l function
- mbctombb function
- _mbctombb_l function
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
ms.openlocfilehash: b449dfae04f875c819f34422b9a0ae92e2b8a7c2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952531"
---
# <a name="_mbctombb-_mbctombb_l"></a>_mbctombb, _mbctombb_l

Převede vícebajtový znak dvoubajtové na odpovídající vícebajtový znak.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Vícebajtový znak pro převod.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí **_mbctombb** a **_mbctombb_l** znak jednobajtové, který odpovídá *c*; v opačném případě vrátí *c*.

## <a name="remarks"></a>Poznámky

Funkce **_mbctombb** a **_mbctombb_l** převádějí daný vícebajtový znak na odpovídající jednobajtové vícebajtový znak. Znaky musí odpovídat jednobajtových znakům v rozsahu 0x20-0x7E nebo 0xA1-0xDF, aby je bylo možné převést.

Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md) . Verze této funkce bez přípony **_l** používá aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** je shodná s tím rozdílem, že místo toho používá parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V předchozích verzích se **_mbctombb** volala **zentohan**. Místo toho použijte **_mbctombb** .

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbctombb**|\<Mbstring. h >|
|**_mbctombb_l**|\<Mbstring. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[_mbbtombc, _mbbtombc_l](mbbtombc-mbbtombc-l.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)<br/>
[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
