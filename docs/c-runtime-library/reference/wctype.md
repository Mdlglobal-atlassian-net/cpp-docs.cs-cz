---
title: wctype
ms.date: 11/04/2016
api_name:
- wctype
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
ms.openlocfilehash: f77082bbcc5f3cd9d82fb40993c3ac678e7e7ba2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957804"
---
# <a name="wctype"></a>wctype

Určuje pravidlo klasifikace pro kódy s velkým znakem.

## <a name="syntax"></a>Syntaxe

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>Parametry

*property*<br/>
Řetězec vlastnosti

## <a name="return-value"></a>Návratová hodnota

Pokud kategorie **LC_CTYPE** aktuálního národního prostředí nedefinuje pravidlo klasifikace, jehož název odpovídá *vlastnosti*řetězce vlastnosti, vrátí funkce hodnotu nula. V opačném případě vrátí nenulovou hodnotu vhodnou pro použití jako druhý argument u následného volání [towctrans](towctrans.md).

## <a name="remarks"></a>Poznámky

Funkce Určuje pravidlo klasifikace pro kódy s velkým znakem. Následující páry volání mají stejné chování ve všech národních prostředích (ale implementace může definovat další pravidla klasifikace i v národním prostředí "C"):

|Funkce|Stejné jako|
|--------------|-------------|
|iswalnum (c)|iswctype (c; wctype ("alnum"))|
|iswalpha (c)|iswctype (c; wctype ("alfa"))|
|iswcntrl(c)|iswctype (c; wctype ("TAB"))|
|iswdigit (c)|iswctype (c; wctype ("číslice"))|
|iswgraph (c)|iswctype (c; wctype ("Graph"))|
|iswlower (c)|iswctype (c; wctype ("Lower"))|
|iswprint (c)|iswctype (c; wctype ("Tisk"))|
|iswpunct (c)|iswctype (c; wctype ("punct"))|
|iswspace (c)|iswctype (c; wctype ("prostor"))|
|iswupper (c)|iswctype (c; wctype ("Upper"))|
|iswxdigit (c)|iswctype (c; wctype ("xdigit"))|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wctype**|\<wctype. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
