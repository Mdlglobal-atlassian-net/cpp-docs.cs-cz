---
title: ___lc_codepage_func
ms.date: 11/04/2016
api_name:
- ___lc_codepage_func
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
helpviewer_keywords:
- ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
ms.openlocfilehash: dbadf8239652f5c96e7177dedd91d340e545b9fe
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944924"
---
# <a name="___lc_codepage_func"></a>___lc_codepage_func

Vnitřní funkce CRT. Načte aktuální znakovou stránku vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Návratová hodnota

Aktuální znaková stránka vlákna.

## <a name="remarks"></a>Poznámky

`___lc_codepage_func`je interní funkce CRT, kterou používají jiné funkce CRT k získání aktuální znakové stránky z thread localho úložiště pro data CRT. Tyto informace jsou také k dispozici pomocí funkce [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) .

*Znaková stránka* je mapování jednobajtových nebo dvoubajtových kódů na jednotlivé znaky. Různé znakové stránky obsahují různé speciální znaky, obvykle přizpůsobené pro jazyk nebo skupinu jazyků. Další informace o znakových stránkách naleznete v tématu [Code Pages](../c-runtime-library/code-pages.md).

Interní funkce CRT jsou specifické pro konkrétní implementaci a můžou se měnit s každou vydanou verzí. Nedoporučujeme jejich použití ve vašem kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___lc_codepage_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Viz také:

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
