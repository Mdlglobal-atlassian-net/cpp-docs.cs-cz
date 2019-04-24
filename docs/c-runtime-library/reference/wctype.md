---
title: wctype
ms.date: 11/04/2016
apiname:
- wctype
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
apitype: DLLExport
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
ms.openlocfilehash: 81caf8e1ab04635d205d7b01af2d4c2896eec01c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155313"
---
# <a name="wctype"></a>wctype

Určuje pravidlo klasifikace pro kódy širokého znaku.

## <a name="syntax"></a>Syntaxe

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>Parametry

*property*<br/>
Vlastnost řetězce.

## <a name="return-value"></a>Návratová hodnota

Pokud **LC_CTYPE** kategorie aktuálního národního prostředí nedefinuje pravidlo klasifikace, jejíž název odpovídá řetězci vlastnost *vlastnost*, vrátí funkce hodnotu nula. V opačném případě se vrací nenulovou hodnotu, vhodný pro použití jako druhý argument pro následné volání [towctrans –](towctrans.md).

## <a name="remarks"></a>Poznámky

Funkce určuje pravidla klasifikace pro kódy širokého znaku. Následující páry volání mají stejné chování ve všech národních prostředích (ale implementace můžete definovat další klasifikační pravidla i v národním prostředí "C"):

|Funkce|Stejné jako|
|--------------|-------------|
|iswalnum(c)|iswctype (c, wctype ("alnum"))|
|iswalpha(c)|iswctype (c, wctype ("Alfa"))|
|iswcntrl(c)|iswctype(c, wctype( "cntrl" ) )|
|iswdigit(c)|iswctype (c, wctype ("číslice"))|
|iswgraph(c)|iswctype (c, wctype ("graf"))|
|iswlower(c)|iswctype (c, wctype ("malé"))|
|iswprint(c)|iswctype (c, wctype ("print"))|
|iswpunct(c)|iswctype (c, wctype ("punct"))|
|iswspace(c)|iswctype (c, wctype ("místo"))|
|iswupper(c)|iswctype (c, wctype ("horní"))|
|iswxdigit(c)|iswctype (c, wctype ("xdigit"))|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wctype**|\<wctype.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
