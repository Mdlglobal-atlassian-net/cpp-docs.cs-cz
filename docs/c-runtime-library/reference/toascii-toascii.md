---
title: ToAscii –, __toascii – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __toascii
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
dev_langs:
- C++
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cead516a7e298e56d13d8f1a09a054057796ca64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408419"
---
# <a name="toascii-toascii"></a>toascii, __toascii

Převede znaky ASCII 7 bitů na zkrácení.

## <a name="syntax"></a>Syntaxe

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak, který má převést.

## <a name="return-value"></a>Návratová hodnota

**__toascii –** převede hodnotu *c* do verze 7 ASCII v rozsahu a vrátí výsledek. Je rezervovaný pro označení chybu žádnou návratovou hodnotu.

## <a name="remarks"></a>Poznámky

**__Toascii –** rutina převede daného znaku znaku ASCII zkrácením nejnižší 7 bitů. Žádné jiné transformací.

**__Toascii –** rutiny je definován jako makra, pokud je definována _CTYPE_DISABLE_MACROS makro preprocesoru. Z důvodu zpětné kompatibility **ToAscii –** je definován jako makra pouze tehdy, když [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) není definované nebo je definován jako 0; jinak není definován.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ToAscii –**, **__toascii –**|C: \<ctype.h ><br /><br /> C++: \<cctype – > nebo \<ctype.h >|

**ToAscii –** makro je POSIX rozšíření, a **__toascii –** je specifické pro společnost Microsoft implementace POSIX rozšíření. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[to – funkce](../../c-runtime-library/to-functions.md)<br/>
