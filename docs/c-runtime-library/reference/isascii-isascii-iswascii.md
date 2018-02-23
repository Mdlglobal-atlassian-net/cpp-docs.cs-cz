---
title: "isascii – __isascii –, iswascii – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- iswascii
- __isascii
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
dev_langs:
- C++
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e76d91aef22c3a01d4ee9321baf1165f3ae97412
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="isascii-isascii-iswascii"></a>isascii, __isascii, iswascii

Určuje, zda určitý znak je znak ASCII.

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

*c*  
Celé číslo pro testování.

## <a name="return-value"></a>Návratová hodnota

Všechny tyto rutiny vrátí nenulové hodnoty, pokud `c` je konkrétní reprezentace znaku ASCII. `__isascii` vrátí nenulovou hodnotu, pokud `c` je znak ASCII (v rozsahu 0x00 – 0x7F). `iswascii` vrátí nenulovou hodnotu, pokud `c` je široká charakterová reprezentace znaku ASCII. Všechny tyto rutiny vrátí hodnotu 0, pokud `c` nesplňuje podmínky testu.

## <a name="remarks"></a>Poznámky

Obě `__isascii` a `iswascii` jsou implementované jako makra, pokud je definována _CTYPE_DISABLE_MACROS makro preprocesoru.

Z důvodu zpětné kompatibility `isascii` je implementovaný jako makro pouze v případě [&#95; &#95; STDC &#95; &#95; ](../../preprocessor/predefined-macros.md) není definované nebo je definován jako 0; jinak není definován.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_istascii`|`__isascii`|`__isascii`|`iswascii`|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`isascii`, `__isascii`|C: \<ctype.h ><br /><br /> C++: \<cctype – > nebo \<ctype.h >|
|`iswascii`|C: \<wctype.h >, \<ctype.h >, nebo \<wchar.h ><br /><br /> C++: \<cwctype – >, \<cctype – >, \<wctype.h >, \<ctype.h >, nebo \<wchar.h >|

`isascii`, `__isascii` a `iswascii` funkce se konkrétní společnosti Microsoft. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)   
[Národní prostředí](../../c-runtime-library/locale.md)   
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)