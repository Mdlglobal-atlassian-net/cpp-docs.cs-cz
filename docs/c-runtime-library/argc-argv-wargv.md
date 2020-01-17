---
title: __argc, __argv, __wargv
description: Popisuje globální konstanty knihovny modulu runtime Microsoft C __argc, __argva __wargv.
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
no-loc:
- __argc
- __argv
- __wargv
- main
- wmain
ms.openlocfilehash: 86a22a7391c7bde34d7734631a2970a45851dda3
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123978"
---
# <a name="opno-loc__argc-opno-loc__argv-opno-loc__wargv"></a>__argc, __argv, __wargv

`__argc` globální proměnná je počet argumentů příkazového řádku předaných programu. `__argv` je ukazatel na pole jednobajtových znaků nebo vícebajtových znaků, které obsahují argumenty programu a `__wargv` je ukazatel na pole řetězců s velkým znakem, které obsahují argumenty programu. Tyto globální proměnné poskytují argumenty pro `main` nebo `wmain`.

## <a name="syntax"></a>Syntaxe

```C
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>Poznámky

V programu, který používá funkci `main`, `__argc` a `__argv` jsou inicializovány při spuštění programu pomocí příkazového řádku, který se používá ke spuštění programu. Příkazový řádek se analyzuje do jednotlivých argumentů a jsou rozbalené zástupné znaky. Počet argumentů je přiřazen `__argc` a řetězce argumentu jsou přiděleny na haldu a k `__argv`je přiřazen ukazatel na pole argumentů. V programu kompilovaném pro použití velkých písmen a `wmain` funkce jsou analyzovány argumenty a zástupné znaky jsou rozšířeny jako řetězce s velkým počtem znaků a ukazatel na pole řetězců argumentu je přiřazen k `__wargv`.

V případě přenosného kódu doporučujeme použít argumenty předané `main` k získání argumentů příkazového řádku v programu.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE není definováno|_UNICODE definováno|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>Požadavky

|Globální proměnná|Požadovaný hlavičkový soubor|
|---------------------|---------------------|
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C++)|

`__argc`, `__argv`a `__wargv` jsou rozšíření společnosti Microsoft. Informace o kompatibilitě najdete v tématu [Kompatibilita](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

\ [globálních proměnných](../c-runtime-library/global-variables.md)
[funkcemain a argumenty příkazového řádku (C++)](../cpp/main-function-command-line-args.md)\
[Použití wmain místo main](../cpp/using-wmain-instead-of-main.md)
