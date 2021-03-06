---
title: _STATIC_ASSERT – makro
ms.date: 11/04/2016
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _STATIC_ASSERT
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: ac609fc7af937b6f56cd5b310341409187df7de4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957935"
---
# <a name="_static_assert-macro"></a>_STATIC_ASSERT – makro

Vyhodnoťte výraz v době kompilace a vygenerujte chybu, pokud je výsledek **nepravdivý**.

## <a name="syntax"></a>Syntaxe

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Výraz (včetně ukazatelů), jejichž výsledkem je nenulová hodnota (**true**) nebo 0 (**false**).

## <a name="remarks"></a>Poznámky

Toto makro se podobá [makrům _ASSERT a _ASSERTE](assert-asserte-assert-expr-macros.md)s tím rozdílem, že *booleanExpression* je vyhodnocena v době kompilace místo za běhu. Pokud se *booleanExpression* vyhodnotí jako **false** (0), vygeneruje se [Chyba kompilátoru C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) .

## <a name="example"></a>Příklad

V tomto příkladu zkontrolujeme, zda je typ [sizeof](../../c-language/sizeof-operator-c.md) , který je **int** , větší nebo roven 2 bajtů a zda je typ [sizeof](../../c-language/sizeof-operator-c.md) a **Long** roven 1 bajt. Program se nezkompiluje a vygeneruje [chybu kompilátoru C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) , protože **Long** je větší než 1 bajt.

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
