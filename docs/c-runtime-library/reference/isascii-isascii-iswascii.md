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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3e04b85c9ce7519593802c21311315d534dce6a5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919790"
---
# <a name="isascii-__isascii-iswascii"></a>isascii, __isascii, iswascii

Určuje, zda je určitý znak znak ASCII.

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

*r*<br/>
Celé číslo k otestování.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud je **c** konkrétní reprezentace znaku ASCII. **__isascii** vrátí nenulovou hodnotu, pokud je **c** znak ASCII (v rozsahu 0x00-0x7F). **iswascii** vrací nenulovou hodnotu, pokud je **c** znaková reprezentace znaku ASCII. Každá z těchto rutin vrátí hodnotu 0, pokud **c** nesplňuje podmínky testu.

## <a name="remarks"></a>Poznámky

**__Isascii** i **iswascii** jsou implementovány jako makra, pokud není definováno makro preprocesoru _CTYPE_DISABLE_MACROS.

Z důvodu zpětné kompatibility je **standardně** implementován jako makro pouze v případě, že [&#95;&#95;STDC&#95;&#95;](../../preprocessor/predefined-macros.md) není definováno nebo je definováno jako 0; v opačném případě není definován.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**kódování** **__isascii**|C: \<CType. h><br /><br /> C++: \<cctype> nebo \<CType. h>|
|**iswascii**|C: \<wctype. h>, \<CType. h> nebo \<WCHAR. h><br /><br /> C++: \<cwctype>, \<cctype>, \<wctype. h>, \<ctype. h> nebo \<WCHAR. h>|

Funkce **iswascii** jsou specifické **__Isascii** **pro společnost**Microsoft. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[je, rutiny ISW](../../c-runtime-library/is-isw-routines.md)<br/>
