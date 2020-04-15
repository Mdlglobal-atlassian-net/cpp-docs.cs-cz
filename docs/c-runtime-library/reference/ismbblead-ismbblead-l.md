---
title: _ismbblead, _ismbblead_l
description: Popisuje _ismbblead a _ismbblead_l funkce knihovny Runtime (Microsoft C Runtime Library).
ms.date: 4/2/2020
api_name:
- _ismbblead_l
- _ismbblead
- _o__ismbblead
- _o__ismbblead_l
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
- ismbblead_l
- istlead
- _ismbblead
- _ismbblead_l
- ismbblead
- _istlead
helpviewer_keywords:
- _ismbblead_l function
- ismbblead function
- _ismbblead function
- istlead function
- ismbblead_l function
- _istlead function
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
ms.openlocfilehash: ee3085d49a27f2f3c97c6578463cf3a0598b73c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343582"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead, _ismbblead_l

Testuje znak k určení, zda se jedná o úvodní bajt vícebajtového znaku.

## <a name="syntax"></a>Syntaxe

```C
int _ismbblead(
   unsigned int c
);
int _ismbblead_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*\
Celé číslo, které má být testováno.

*Národní prostředí*\
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu, pokud je celé číslo *c* prvním bajtem vícebajtového znaku.

## <a name="remarks"></a>Poznámky

Vícebajtové znaky se skládají z úvodního bajtu následovaného koncovým bajtem. Hlavní bajty se rozlišují podle toho, že jsou v určitém rozsahu pro danou znakovou sadu. Například pouze v znakové stránce 932 se v rozsahu bajtů zájemců pohybuje od 0x81 do 0x9F a 0xE0 - 0xFC.

**_ismbblead** používá aktuální národní prostředí pro chování závislé na národním prostředí. **_ismbblead_l** je identická s tím rozdílem, že místo toho používá národní prostředí předané. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Pokud národní prostředí je UTF-8, **_ismbblead** a **_ismbblead_l** vždy vrátí 0 (false), zda *c* je úvodní bajt nebo ne.

**_ismbblead** a **_ismbblead_l** jsou specifické pro microsoft, nikoli součástí knihovny Standard C. Nedoporučujeme je používat tam, kde chcete přenosný kód. Pro kompatibilitu se standardem C použijte místo toho **mbrlen.**

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecných textů

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|Vždy vrátí false|**_ismbblead**|Vždy vrátí false|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<mbctype.h> \<nebo mbstring.h>|\<ctype.h>,* \<limits.h \<>, stdlib.h>|
|**_ismbblead_l**|\<mbctype.h> \<nebo mbstring.h>|\<ctype.h>,* \<limits.h \<>, stdlib.h>|

\*Pro manifestové konstanty pro zkušební podmínky.

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)\
[_ismbb rutiny](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
