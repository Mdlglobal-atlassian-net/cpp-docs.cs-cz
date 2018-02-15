---
title: toascii, __toascii | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf4c29934d22d3f20d79650faa406f217ffdd4c6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
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

*c*  
Znak, který má převést.

## <a name="return-value"></a>Návratová hodnota

`__toascii` Převede hodnotu *c* do verze 7 ASCII v rozsahu a vrátí výsledek. Je rezervovaný pro označení chybu žádnou návratovou hodnotu.

## <a name="remarks"></a>Poznámky

`__toascii` Rutina převede daného znaku znaku ASCII zkrácením nejnižší 7 bitů. Žádné jiné transformací.

`__toascii` Rutiny je definován jako makra, pokud je definována _CTYPE_DISABLE_MACROS makro preprocesoru. Z důvodu zpětné kompatibility `toascii` je definován jako makra pouze tehdy, když [&#95; &#95; STDC &#95; &#95; ](../../preprocessor/predefined-macros.md) není definované nebo je definován jako 0; jinak není definován.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`toascii`, `__toascii`|C: \<ctype.h ><br /><br /> C++: \<cctype – > nebo \<ctype.h >|

`toascii` Makro je POSIX rozšíření, a `__toascii` je specifické pro společnost Microsoft implementace POSIX rozšíření. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)   
[je, isw – rutiny](../../c-runtime-library/is-isw-routines.md)   
[to – funkce](../../c-runtime-library/to-functions.md)