---
title: ___lc_codepage_func
ms.date: 11/04/2016
apiname:
- ___lc_codepage_func
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
helpviewer_keywords:
- ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
ms.openlocfilehash: aebd978839cc59c94c01e9c24432b69add72c4dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343499"
---
# <a name="lccodepagefunc"></a>___lc_codepage_func

Vnitřní funkce CRT. Načte aktuální znakové stránce vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Návratová hodnota

Aktuální znakové stránce vlákna.

## <a name="remarks"></a>Poznámky

`___lc_codepage_func` je interní funkce CRT, který používá jiné funkce CRT se získat aktuální znakové stránce z úložiště thread local data CRT. Tyto informace jsou k dispozici také pomocí [_get_current_locale –](../c-runtime-library/reference/get-current-locale.md) funkce.

A *znaková stránka* obsahuje mapování jednobajtových a dvoubajtových kódy jednotlivých znaků. Různé znakové stránky zahrnovat jiné speciální znaky, které jsou obvykle přizpůsobené pro jazyk nebo skupinu z jazyků. Další informace o znakových stránkách naleznete v tématu [znakové stránky](../c-runtime-library/code-pages.md).

Vnitřní funkce CRT jsou specifický pro implementaci a může změnit jednotlivých vydání. Nedoporučujeme jejich použití ve vašem kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___lc_codepage_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Viz také:

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
