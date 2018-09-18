---
title: ___lc_collate_cp_func | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- ___lc_collate_cp_func
apilocation:
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- ___lc_collate_cp_func
dev_langs:
- C++
helpviewer_keywords:
- ___lc_collate_cp_func
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d239820221c696dbb8d27e2824ed871a7e2d5ad8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063046"
---
# <a name="lccollatecpfunc"></a>___lc_collate_cp_func

Vnitřní funkce CRT. Načte aktuální znakové stránce kolace vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Návratová hodnota

Aktuální znakové stránce kolace vlákna.

## <a name="remarks"></a>Poznámky

`___lc_collate_cp_func` je interní funkce CRT, který používá jiné funkce CRT získat aktuální znakové stránce kolace pro CRT data z úložiště thread local. Tyto informace jsou k dispozici také pomocí [_get_current_locale –](../c-runtime-library/reference/get-current-locale.md) funkce.

Vnitřní funkce CRT jsou specifický pro implementaci a může změnit jednotlivých vydání. Nedoporučujeme jejich použití ve vašem kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___lc_collate_cp_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Viz také

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)