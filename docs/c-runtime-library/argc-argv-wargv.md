---
title: __argc, __argv, __wargv
ms.date: 11/04/2016
api_name:
- __wargv
- __argv
- __argc
api_location:
- msvcrt120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __argv
- __argc
- __wargv
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
ms.openlocfilehash: 59ab1f5ba52e6dc84d44e8cb5465cfa412d01895
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940627"
---
# <a name="__argc-__argv-__wargv"></a>__argc, __argv, __wargv

`__argc` Globální proměnná je počet argumentů příkazového řádku předaných programu. `__argv`je ukazatel na pole jednobajtových znaků nebo vícebajtových řetězců, které obsahují argumenty programu, a `__wargv` je ukazatel na pole řetězců s velkým znakem, které obsahují argumenty programu. Tyto globální proměnné poskytují argumenty pro `main` nebo. `wmain`

## <a name="syntax"></a>Syntaxe

```
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>Poznámky

V programu, který používá `main` `__argc` funkci a `__argv` jsou inicializovány při spuštění programu pomocí příkazového řádku, který je použit ke spuštění programu. Příkazový řádek se analyzuje do jednotlivých argumentů a jsou rozbalené zástupné znaky. Počet argumentů je přiřazen k `__argc` a řetězce argumentů jsou přiděleny na haldu a k poli je `__argv`přiřazena ukazatel na pole argumentů. V programu, který je zkompilován pro použití velkých znaků `wmain` a funkce, jsou analyzovány argumenty a zástupné znaky jsou rozšířeny jako řetězce s velkým počtem znaků a ukazatel na pole řetězců argumentů je `__wargv`přiřazen.

V případě přenosného kódu doporučujeme použít argumenty předané `main` pro k získání argumentů příkazového řádku v programu.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE není definován.|_UNICODE definováno|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>Požadavky

|Globální proměnná|Požadovaný hlavičkový soubor|
|---------------------|---------------------|
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C++)|

`__argc`, `__argv` a`__wargv` jsou rozšířeními společnosti Microsoft. Informace o kompatibilitě najdete v tématu [Kompatibilita](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Globální proměnné](../c-runtime-library/global-variables.md)<br/>
[main: spuštění programu](../cpp/main-program-startup.md)<br/>
[Použití funkce wmain namísto main](../cpp/using-wmain-instead-of-main.md)
