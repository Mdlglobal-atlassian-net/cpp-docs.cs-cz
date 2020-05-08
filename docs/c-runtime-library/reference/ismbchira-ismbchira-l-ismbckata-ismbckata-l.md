---
title: _ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l
ms.date: 4/2/2020
api_name:
- _ismbckata
- _ismbchira_l
- _ismbchira
- _ismbckata_l
- _o__ismbchira
- _o__ismbchira_l
- _o__ismbckata
- _o__ismbckata_l
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
- ismbckata_l
- _ismbckata_l
- ismbckata
- ismbchira
- _ismbckata
- ismbchira_l
- _ismbchira_l
- _ismbchira
helpviewer_keywords:
- _ismbckata function
- _ismbchira function
- _ismbckata_l function
- Katakana
- ismbchira function
- _ismbchira_l function
- ismbchira_l function
- ismbdkata_l function
- Hiragana
- ismbckata function
ms.assetid: 2db388a2-be31-489b-81c8-f6bf3f0582d3
ms.openlocfilehash: 89c6aacbb6726165703d38e3ea519806b1f970d2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910699"
---
# <a name="_ismbchira-_ismbchira_l-_ismbckata-_ismbckata_l"></a>_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l

**Specifické funkce znakové stránky 932**

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbchira(
   unsigned int c
);
int _ismbchira_l(
   unsigned int c,
   _locale_t locale
);
int _ismbckata(
   unsigned int c
);
int _ismbckata_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*r*<br/>
Testovaný znak.

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrací nenulovou hodnotu, pokud znak splňuje testovací podmínku, nebo 0, pokud tomu tak není. Pokud *c* <= 255 a existuje odpovídající rutina **_ismbb** (například **_ismbcalnum** odpovídá **_ismbbalnum**), výsledkem je návratová hodnota odpovídající **_ismbb** rutiny.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí testuje daný vícebajtový znak pro danou podmínku.

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předané národní prostředí namísto aktuálního národního prostředí pro své chování závislé na národním prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

|Rutina|Testovací podmínka (pouze znaková stránka 932)|
|-------------|-------------------------------------------|
|**_ismbchira**|Dvoubajtové znaky Hiragana: 0x829F<=*c*<= 0x82F1.|
|**_ismbchira_l**|Dvoubajtové znaky Hiragana: 0x829F<=*c*<= 0x82F1.|
|**_ismbckata**|Dvojité Byte Katakana: 0x8340<=*c*<= 0x8396.|
|**_ismbckata_l**|Dvojité Byte Katakana: 0x8340<=*c*<= 0x8396.|

**Konec konkrétní kódové stránky 932**

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbchira**|\<Mbstring. h>|
|**_ismbchira_l**|\<Mbstring. h>|
|**_ismbckata**|\<Mbstring. h>|
|**_ismbckata_l**|\<Mbstring. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[je, rutiny ISW](../../c-runtime-library/is-isw-routines.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
