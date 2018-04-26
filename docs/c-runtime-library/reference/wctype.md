---
title: wctype – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbad04d3c56015ddea10a058ae8b262d7f94d40f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="wctype"></a>wctype

Určuje pravidla klasifikace pro široká charakterová kódy.

## <a name="syntax"></a>Syntaxe

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>Parametry

*property*<br/>
Vlastnost řetězec.

## <a name="return-value"></a>Návratová hodnota

Pokud **LC_CTYPE –** kategorie aktuální národní prostředí nedefinuje pravidla klasifikace, jejíž název odpovídá řetězci vlastnost *vlastnost*, funkce vrátí hodnotu nula. Jinak vrátí nenulovou hodnotu vhodné pro použití jako druhý argument pro následné volání [towctrans –](towctrans.md).

## <a name="remarks"></a>Poznámky

Funkce určuje pravidla klasifikace pro široká charakterová kódy. Následující páry volání mají stejné chování ve všech národních prostředí (ale implementace můžete definovat pravidla další klasifikace i v národním prostředí "C"):

|Funkce|Stejné jako|
|--------------|-------------|
|iswalnum(c)|iswctype – (c, wctype – ("alnum"))|
|iswalpha(c)|iswctype – (c, wctype – ("Alfa"))|
|iswcntrl(c)|iswctype – (c, wctype – ("stisknutím kláves CTRL +"))|
|iswdigit(c)|iswctype – (c, wctype – ("číslice"))|
|iswgraph(c)|iswctype – (c, wctype – ("grafu"))|
|iswlower(c)|iswctype – (c, wctype – ("malá"))|
|iswprint(c)|iswctype – (c, wctype – ("Tisk"))|
|iswpunct(c)|iswctype – (c, wctype – ("punct"))|
|iswspace(c)|iswctype – (c, wctype – ("místo"))|
|iswupper(c)|iswctype – (c, wctype – ("horní"))|
|iswxdigit(c)|iswctype – (c, wctype – ("xdigit"))|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wctype**|\<wctype.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
