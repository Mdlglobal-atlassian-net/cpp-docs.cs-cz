---
title: isascii, __isascii, iswascii
ms.date: 4/2/2020
api_name:
- iswascii
- __isascii
- _o_iswascii
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
ms.openlocfilehash: aeb9c27fee4d179cc16caa50c6f0aae521402beb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343909"
---
# <a name="isascii-__isascii-iswascii"></a>isascii, __isascii, iswascii

Určuje, zda je určitý znak znakem ASCII.

## <a name="syntax"></a>Syntaxe

```C
int __isascii(
   int c
);
int iswascii(
   wint_t c
);

#define isascii __isascii
```

### <a name="parameters"></a>Parametry

*C*<br/>
Celé číslo k testování.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou, pokud **c** je konkrétní reprezentace znaku ASCII. **__isascii** vrátí nenulovou hodnotu, pokud **c** je znak ASCII (v rozsahu 0x00 - 0x7F). **iswascii** vrátí nenulovou **hodnotu,** pokud c je širokoúhlá reprezentace znaku ASCII. Každá z těchto rutin vrátí hodnotu 0, pokud **c** nesplňuje zkušební podmínku.

## <a name="remarks"></a>Poznámky

**__isascii** i **iswascii** jsou implementovány jako makra, pokud není definována makro _CTYPE_DISABLE_MACROS preprocesoru.

Z důvodu zpětné kompatibility je **isascii** implementována jako makro pouze v případě, [že&#95;&#95;&#95;&#95;STDC](../../preprocessor/predefined-macros.md) není definováno nebo je definováno jako 0; jinak není definován.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isascii**, **__isascii**|C: \<ctype.h><br /><br /> C++: \<cctype \<> nebo ctype.h>|
|**iswascii**|C: \<wctype.h \<>, ctype.h \<> nebo wchar.h><br /><br /> C++: \<cwctype \<>, cctype>, \<wctype.h>, \< \<ctype.h> nebo wchar.h>|

Funkce **isascii**, **__isascii** a **iswascii** jsou specifické pro společnost Microsoft. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw Rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
