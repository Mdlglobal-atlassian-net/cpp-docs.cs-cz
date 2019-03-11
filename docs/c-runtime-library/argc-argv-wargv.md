---
title: __argc __argv, __wargv
ms.date: 11/04/2016
apiname:
- __wargv
- __argv
- __argc
apilocation:
- msvcrt120.dll
apitype: DLLExport
f1_keywords:
- __argv
- __argc
- __wargv
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
ms.openlocfilehash: f428d81215193361a409473a411eb5c4d91fa997
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743308"
---
# <a name="argc-argv-wargv"></a>__argc __argv, __wargv

`__argc` Počet argumentů příkazového řádku předané do programu je globální proměnná. `__argv` ukazatel na pole řetězců jedním jednobajtového znaku nebo více byte znaků, které obsahují argumenty programu a `__wargv` je ukazatel na pole řetězce širokého znaku obsahující argumenty programu. Tyto globální proměnné poskytují argumenty, které mají `main` nebo `wmain`.

## <a name="syntax"></a>Syntaxe

```
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>Poznámky

V programu v jazyce, který používá `main` funkci `__argc` a `__argv` jsou inicializovány při spuštění programu pomocí příkazového řádku, který se používá ke spuštění programu. Příkazový řádek je analyzován do jednotlivé argumenty a zástupné znaky jsou rozbaleny. Počet argumentů je přiřazena k `__argc` argument řetězce jsou přidělený k haldě a ukazatel na pole argumentů je přiřazena k `__argv`. V programu kompilovaného použití širokých znaků a `wmain` funkce, argumenty jsou analyzovány a zástupné znaky jsou rozbaleny jako řetězce širokého znaku a ukazatel na pole řetězců argument je přiřazena k `__wargv`.

Přenositelný kód, doporučujeme použít argumenty předané `main` získat argumenty příkazového řádku ve svém programu.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE nedefinovaná.|_UNICODE definováno|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>Požadavky

|Globální proměnná|Požadovaný hlavičkový soubor|
|---------------------|---------------------|
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C++)|

`__argc`, `__argv`, a `__wargv` jsou rozšíření společnosti Microsoft. Informace o kompatibilitě naleznete v tématu [kompatibility](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Globální proměnné](../c-runtime-library/global-variables.md)<br/>
[hlavní: Spuštění programu](../cpp/main-program-startup.md)<br/>
[Použití funkce wmain namísto main](../cpp/using-wmain-instead-of-main.md)
