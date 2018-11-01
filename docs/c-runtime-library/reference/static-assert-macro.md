---
title: _STATIC_ASSERT – makro
ms.date: 11/04/2016
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
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: 5d3aa1d9665b48a0690d8eb62353fc98c5a550f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539539"
---
# <a name="staticassert-macro"></a>_STATIC_ASSERT – makro

Vyhodnocení výrazu v době kompilace a vygenerují chybu, pokud je výsledek **FALSE**.

## <a name="syntax"></a>Syntaxe

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Výraz (včetně odkazů), který se vyhodnotí na nenulovou hodnotu (**TRUE**) nebo 0 (**FALSE**).

## <a name="remarks"></a>Poznámky

Vypadá podobně jako toto makro [_ASSERT a _asserte – makra](assert-asserte-assert-expr-macros.md), s tím rozdílem, že *booleanExpression* je vyhodnocen v době kompilace místo za běhu. Pokud *booleanExpression* vyhodnotí jako **FALSE** (0), [Chyba kompilátoru C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) je generován.

## <a name="example"></a>Příklad

V tomto příkladu zkontrolujeme, jestli [sizeof](../../c-language/sizeof-operator-c.md) **int** je větší než nebo rovna hodnotě 2 bajty a zda [sizeof](../../c-language/sizeof-operator-c.md) **dlouhé** 1 bajt. Program nebude kompilovat a bude generovat [Chyba kompilátoru C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) protože **dlouhé** je větší než 1 bajt.

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

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](assert-asserte-assert-expr-macros.md)<br/>
