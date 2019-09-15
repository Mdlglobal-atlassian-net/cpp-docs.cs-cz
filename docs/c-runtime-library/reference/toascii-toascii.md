---
title: toascii, __toascii
ms.date: 11/04/2016
api_name:
- __toascii
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
ms.openlocfilehash: 09df829511b38b87cb41e32a59bee9f38a9b8f32
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957462"
---
# <a name="toascii-__toascii"></a>toascii, __toascii

Převede znaky na 7 bitů ASCII zkrácením.

## <a name="syntax"></a>Syntaxe

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak, který se má převést

## <a name="return-value"></a>Návratová hodnota

**__toascii** převede hodnotu *c* na 7 bitů rozsahu ASCII a vrátí výsledek. Není vyhrazena žádná návratová hodnota pro indikaci chyby.

## <a name="remarks"></a>Poznámky

Rutina **__toascii** Převede daný znak na znak ASCII tím, že ho ořízne na nižší pořadí 7 bitů. Není použita žádná jiná transformace.

Rutina **__toascii** je definována jako makro, pokud není definován preprocesor makra _CTYPE_DISABLE_MACROS. Z důvodu zpětné kompatibility je **ToAscii** definováno jako makro pouze v případě, že [ &#95; &#95;STDC&#95; ](../../preprocessor/predefined-macros.md) není definován nebo je definován jako 0; v opačném případě není definován.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**toascii**, **__toascii**|C: \<CType. h ><br /><br /> C++: \<cctype > nebo \<CType. h >|

**ToAscii** makro je rozšíření POSIX a **__toascii** je implementace rozšíření POSIX specifická pro společnost Microsoft. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[to – funkce](../../c-runtime-library/to-functions.md)<br/>
