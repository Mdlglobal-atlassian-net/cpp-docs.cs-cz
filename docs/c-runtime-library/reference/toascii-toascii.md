---
title: toascii, __toascii
ms.date: 11/04/2016
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
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
ms.openlocfilehash: 22f76bdbdb21eb5b3cc9a226c111e321ee2fd0ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155512"
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
Znak pro převod.

## <a name="return-value"></a>Návratová hodnota

**__toascii –** převede hodnotu *c* do ASCII 7 bitů v rozsahu a vrátí výsledek. Vyhrazená k indikaci chyby není žádnou návratovou hodnotu.

## <a name="remarks"></a>Poznámky

**__Toascii –** rutina převede daný znak na znak ASCII zkrácením 7 bity nižšího řádu. Je použita žádná transformace.

**__Toascii –** rutina je definován jako makra, pokud _CTYPE_DISABLE_MACROS preprocesor makro je definováno. Z důvodu zpětné kompatibility **toascii** je definován jako makra pouze tehdy, když [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) není definované nebo je definováno jako 0; v opačném případě není definováno.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**toascii**, **__toascii**|C: \<ctype.h ><br /><br /> Jazyk C++: \<cctype – > nebo \<ctype.h >|

**Toascii** – makro je rozšířením POSIX a **__toascii –** je implementace POSIX rozšíření specifické pro společnost Microsoft. Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[to – funkce](../../c-runtime-library/to-functions.md)<br/>
