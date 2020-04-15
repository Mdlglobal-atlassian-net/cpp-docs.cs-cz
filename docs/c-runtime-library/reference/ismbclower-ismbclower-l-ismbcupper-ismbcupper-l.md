---
title: _ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l
ms.date: 4/2/2020
api_name:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
- _o__ismbclower
- _o__ismbclower_l
- _o__ismbcupper
- _o__ismbcupper_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbcupper
- _ismbclower
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
ms.openlocfilehash: 9a0991d974c33cff22044364f7a4351f160215a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342931"
---
# <a name="_ismbclower-_ismbclower_l-_ismbcupper-_ismbcupper_l"></a>_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l

Zkontroluje, zda je vícebajtový znak malý nebo velký.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbclower(
   unsigned int c
);
int _ismbclower_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcupper(
   unsigned int c
);
int _ismbcupper_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Znak, který má být testován.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud znak splňuje testovací podmínku, nebo 0, pokud tomu tak není. Pokud *c*<= 255 a existuje odpovídající **rutina _ismbb** (například **_ismbcalnum** odpovídá **_ismbbalnum**), výsledkem je vrácená hodnota odpovídající **_ismbb** rutiny.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí testuje daný vícebajtový znak pro danou podmínku.

Verze těchto funkcí s **příponou _l** jsou identické s tím rozdílem, že používají národní prostředí předané namísto aktuálního národního prostředí pro jejich chování závislé na národním prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

|Rutina|Zkušební podmínka|Příklad znakové stránky 932|
|-------------|--------------------|---------------------------|
|**_ismbclower**|Malá abecední|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtová reprezentace malé písmeno ASCII v angličtině: 0x61<=*c*<=0x7A.|
|**_ismbclower_l**|Malá abecední|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtová reprezentace malé písmeno ASCII v angličtině: 0x61<=*c*<=0x7A.|
|**_ismbcupper**|Velká abeceda|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtová reprezentace velké anglické písmeno ASCII: 0x41<=*c*<=0x5A.|
|**_ismbcupper_l**|Velká abeceda|Vrátí nenulovou hodnotu pouze v případě, že *c* je jednobajtová reprezentace velké anglické písmeno ASCII: 0x41<=*c*<=0x5A.|

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbclower**|\<mbstring.h>|
|**_ismbclower_l**|\<mbstring.h>|
|**_ismbcupper**|\<mbstring.h>|
|**_ismbcupper_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is, isw Rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
