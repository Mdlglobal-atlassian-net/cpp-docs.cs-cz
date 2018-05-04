---
title: _Static_assert – makro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
- _STATIC_ASSERT
dev_langs:
- C++
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbbab8314a038d796ebd1a13342f3054e59f3e68
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="staticassert-macro"></a>_STATIC_ASSERT – makro

Vyhodnocení výrazu v době kompilace a generuje chybu, pokud je výsledek **FALSE**.

## <a name="syntax"></a>Syntaxe

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>Parametry

*booleanExpression* výraz (včetně ukazatele), který se vyhodnotí na nenulové hodnoty (**TRUE**) nebo 0 (**FALSE**).

## <a name="remarks"></a>Poznámky

Toto makro vypadá takto: [_ASSERT a _asserte – makra](assert-asserte-assert-expr-macros.md)kromě toho, že *booleanExpression* je vyhodnocován v době kompilace místo v době běhu. Pokud *booleanExpression* vyhodnotí jako **FALSE** (0), [C2466 Chyba kompilátoru](../../error-messages/compiler-errors-1/compiler-error-c2466.md) se vygeneruje.

## <a name="example"></a>Příklad

V tomto příkladu jsme zkontrolujte zda [sizeof](../../c-language/sizeof-operator-c.md) **int** je větší než nebo rovna 2 bajtů a jestli [sizeof](../../c-language/sizeof-operator-c.md) **dlouho** je 1 bajtů. Program nebude zkompilování a vygeneruje [C2466 Chyba kompilátoru](../../error-messages/compiler-errors-1/compiler-error-c2466.md) protože **dlouho** je větší než 1 bajtů.

```C
// crt__static_assert.c

#include <crtdbg.h>
#include <stdio.h>

_STATIC_ASSERT(sizeof(int) >= 2);
_STATIC_ASSERT(sizeof(long) == 1);  // C2466

int main()
{
    printf("I am sure that sizeof(int) will be >= 2: %d\n",
        sizeof(int));
    printf("I am not so sure that sizeof(long) == 1: %d\n",
        sizeof(long));
}
```

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-----------|---------------------|
|**_STATIC_ASSERT**|\<crtdbg.h>|

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](assert-asserte-assert-expr-macros.md)<br/>
