---
title: _ismbblead, _ismbblead_l
description: Popisuje funkce knihovny CRT (Microsoft C Runtime Library) _ismbblead a _ismbblead_l.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 7680793b71c4535ed75433ac98167e52a39896ba
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918670"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead, _ismbblead_l

Testuje znak pro určení, zda se jedná o vedoucí bajt vícebajtového znaku.

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

*r*\
Celé číslo, které se má testovat.

*jazyka*\
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Vrací nenulovou hodnotu, pokud je celé číslo *c* první bajt vícebajtového znaku.

## <a name="remarks"></a>Poznámky

Vícebajtové znaky se skládají z vedoucího bajtu následovaného koncovým bajtem. Vedoucí bajty jsou odlišeny v určitém rozsahu pro danou znakovou sadu. Například pouze v kódové stránce 932 je v rozsahu od 0x81-0x9F a 0xE0-0xFC.

**_ismbblead** používá aktuální národní prostředí pro chování závislé na národním prostředí. **_ismbblead_l** je totožný s tím rozdílem, že místo toho používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud je národní prostředí UTF-8, **_ismbblead** a **_ismbblead_l** vždycky vracet 0 (false) *, ať už je to vedoucí* bajt, nebo ne.

**_ismbblead** a **_ismbblead_l** jsou specifické pro společnost Microsoft, nikoli součástí standardní knihovny jazyka C. Nedoporučujeme je používat tam, kde chcete použít přenosný kód. V případě kompatibility Standard C použijte místo toho **mbrlen** .

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|Vždycky vrátí hodnotu false.|**_ismbblead**|Vždycky vrátí hodnotu false.|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<Mbctype. h> nebo \<Mbstring. h>|\<CType. h>, * \<Limits. h> \<, Stdlib. h>|
|**_ismbblead_l**|\<Mbctype. h> nebo \<Mbstring. h>|\<CType. h>, * \<Limits. h> \<, Stdlib. h>|

\*Pro konstanty manifestu pro podmínky testu.

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)\
[rutiny _ismbb](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
