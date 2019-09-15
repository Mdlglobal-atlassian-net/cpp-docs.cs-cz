---
title: _mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l
ms.date: 11/04/2016
api_name:
- _mbctohira
- _mbctohira_l
- _mbctokata
- _mbctokata_l
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
ms.openlocfilehash: 6e158e933442256b1d712ba42afc28b94e2b123c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952549"
---
# <a name="_mbctohira-_mbctohira_l-_mbctokata-_mbctokata_l"></a>_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l

Převádí mezi znaky hiragana a Katakana.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí převedený znak *c*, pokud je to možné. V opačném případě vrátí znak *c* beze změny.

## <a name="remarks"></a>Poznámky

Funkce **_mbctohira** a **_mbctokata** testují znak *c* a, pokud je to možné, používají jeden z následujících převodů.

|Rutiny|Převedeny|
|--------------|--------------|
|**_mbctohira**, **_mbctohira_l**|Vícebajtové znaky Katakana na vícebajtové znaky Hiragana.|
|**_mbctokata**, **_mbctokata_l**|Vícebajtové znaky Hiragana na vícebajtové Katakana.|

Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md) . Verze těchto funkcí jsou identické, s tím rozdílem, že ty, které nemají příponu **_l** , používají aktuální národní prostředí pro toto chování závislé na národním prostředí a ty, které mají příponu **_l** , místo toho používají předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V dřívějších verzích bylo **_mbctohira** s názvem **jtohira** a **_mbctokata** se jmenovalo **jtokata**. Pro nový kód použijte nové názvy.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbctohira**|\<Mbstring. h >|
|**_mbctohira_l**|\<Mbstring. h >|
|**_mbctokata**|\<Mbstring. h >|
|**_mbctokata_l**|\<Mbstring. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
