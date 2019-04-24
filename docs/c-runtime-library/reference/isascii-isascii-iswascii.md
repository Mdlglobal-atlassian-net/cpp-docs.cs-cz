---
title: isascii, __isascii, iswascii
ms.date: 11/04/2016
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
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
ms.openlocfilehash: d150e7bb335dc77ed86f445128eebf97b8be5ac3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287466"
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

*c*<br/>
Celé číslo k testování.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí nenulovou hodnotu, pokud **c** je konkrétní reprezentace znaku ASCII. **__isascii –** vrací nenulovou hodnotu, pokud **c** je znak ASCII (v rozsahu 0x00 – 0x7F). **iswascii –** vrací nenulovou hodnotu, pokud **c** je širokoznaká reprezentace znaku ASCII. Každá z těchto rutin vrátí hodnotu 0, pokud **c** nesplňuje testovací podmínku.

## <a name="remarks"></a>Poznámky

Obě **__isascii –** a **iswascii –** jsou implementovány jako makra, pokud je definován _CTYPE_DISABLE_MACROS preprocesor makro.

Z důvodu zpětné kompatibility **isascii –** je implementovaný jako makra pouze v případě [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) není definované nebo je definováno jako 0; v opačném případě není definováno.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**isascii**, **__isascii**|C: \<ctype.h ><br /><br /> Jazyk C++: \<cctype – > nebo \<ctype.h >|
|**iswascii**|C: \<wctype.h >, \<ctype.h >, nebo \<wchar.h ><br /><br /> Jazyk C++: \<cwctype – >, \<cctype – >, \<wctype.h >, \<ctype.h >, nebo \<wchar.h >|

**Isascii –**, **__isascii –** a **iswascii –** funkce jsou specifické pro Microsoft. Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
