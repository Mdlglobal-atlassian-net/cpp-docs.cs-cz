---
title: _ismbblead –, _ismbblead_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ismbblead_l
- _ismbblead
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ismbblead_l
- istlead
- _ismbblead
- _ismbblead_l
- ismbblead
- _istlead
dev_langs:
- C++
helpviewer_keywords:
- _ismbblead_l function
- ismbblead function
- _ismbblead function
- istlead function
- ismbblead_l function
- _istlead function
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2d85459f4addf0688acb5a82b0108ec6133b749
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ismbblead-ismbbleadl"></a>_ismbblead, _ismbblead_l

Testy znak zjistit, zda je bajt realizace vícebajtových znaků.

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

*c*<br/>
Celé číslo má být testována.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Vrátí nenulovou hodnotu, pokud na celé číslo *c* je první bajt vícebajtových znaků.

## <a name="remarks"></a>Poznámky

Více-bajtové znaky obsahovat úvodní bajt následuje koncové bajtů. Vést bajtů rozlišují tím, že je v konkrétní rozsahu pro danou znakovou sadu. Například v kódu stránka 932 pouze, vést bajtů v rozsahu od 0x81-0x9F a 0xE0 - 0xFC.

**_ismbblead –** používá aktuální národní prostředí pro chování závislých na národním prostředí. **_ismbblead_l –** se shoduje s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead –**|Vždy vrátí hodnotu false|**_ismbblead –**|Vždy vrátí hodnotu false|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_ismbblead –**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<Limits.h – >, \<stdlib.h >|
|**_ismbblead_l**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<Limits.h – >, \<stdlib.h >|

\* Pro manifest konstanty podmínky testu.

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
