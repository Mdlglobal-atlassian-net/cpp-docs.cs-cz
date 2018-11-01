---
title: _mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l
ms.date: 11/04/2016
apiname:
- _mbctohira
- _mbctohira_l
- _mbctokata
- _mbctokata_l
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
- _mbctokata
- mbctohira
- _mbctohira
- _mbctohira_l
- mbctokata
- mbctokata_l
- mbctohira_l
- _mbctokata_l
helpviewer_keywords:
- _mbctokata function
- _mbctokata_l function
- _mbctohira_l function
- mbctohira_l function
- mbctohira function
- mbctokata_l function
- _mbctohira function
- mbctokata function
ms.assetid: f949afd7-44d4-4f08-ac8f-1fef2c915a1c
ms.openlocfilehash: 11b08449a7d27015c4ffe0ce398c471bbd6069f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637798"
---
# <a name="mbctohira-mbctohiral-mbctokata-mbctokatal"></a>_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l

Převede mezi znaky hiragana a katakana.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _mbctohira(
   unsigned int c
);
unsigned int _mbctohira_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbctokata(
   unsigned int c
);
unsigned int _mbctokata_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Vícebajtový znak pro převod.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací převedený znak *c*, pokud je to možné. V opačném případě vrátí znak *c* beze změny.

## <a name="remarks"></a>Poznámky

**_Mbctohira –** a **_mbctokata –** funkce otestují znak *c* a pokud je to možné, použijte jednu z následujících převodů.

|Rutiny|Převede|
|--------------|--------------|
|**_mbctohira –**, **_mbctohira_l –**|Vícebajtové znaky katakana pro vícebajtové znaky hiragana.|
|**_mbctokata –**, **_mbctokata_l –**|Vícebajtové znaky hiragana na vícebajtové znaky katakana.|

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí jsou identické, s tím rozdílem, ty, které nemají mít **_l** přípona používají aktuální národní prostředí pro toto chování závislé na národním prostředí a ty, které mají **_l** místo toho příponu použijte parametr národního prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V dřívějších verzích **_mbctohira –** označovala jako **jtohira** a **_mbctokata –** označovala jako **jtokata**. Pro nový kód použijte nové názvy.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbctohira**|\<Mbstring.h >|
|**_mbctohira_l**|\<Mbstring.h >|
|**_mbctokata**|\<Mbstring.h >|
|**_mbctokata_l**|\<Mbstring.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
