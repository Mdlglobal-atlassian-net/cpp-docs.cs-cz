---
title: ___lc_locale_name_func
ms.date: 11/04/2016
api_name:
- ___lc_locale_name_func
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: abc1ade393538586ad07f57e6838591833c9948b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944234"
---
# <a name="___lc_locale_name_func"></a>___lc_locale_name_func

Vnitřní funkce CRT. Načte aktuální název národního prostředí vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
wchar_t** ___lc_locale_name_func(void);
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který obsahuje aktuální název národního prostředí vlákna.

## <a name="remarks"></a>Poznámky

`___lc_locale_name_func`je interní funkce CRT, kterou používají jiné funkce CRT k získání aktuálního názvu národního prostředí z thread localho úložiště pro data CRT. Tyto informace jsou také k dispozici pomocí funkce [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) nebo [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Functions.

Interní funkce CRT jsou specifické pro konkrétní implementaci a můžou se měnit s každou vydanou verzí. Nedoporučujeme jejich použití ve vašem kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Viz také:

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
