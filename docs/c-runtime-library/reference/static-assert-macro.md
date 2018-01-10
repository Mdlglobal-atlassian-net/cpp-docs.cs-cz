---
title: "_Static_assert – makro | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
f1_keywords: _STATIC_ASSERT
dev_langs: C++
helpviewer_keywords: _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ec3d90f9bfcf51b3a5f48baea1c6e3cf06e7d72f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="staticassert-macro"></a>_STATIC_ASSERT – makro
Vyhodnocení výrazu v době kompilace a generuje chybu, pokud je výsledek `FALSE`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_STATIC_ASSERT(  
    booleanExpression  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Výraz (včetně ukazatele), který se vyhodnotí na nenulové hodnoty (`TRUE`) nebo 0 (`FALSE`).  
  
## <a name="remarks"></a>Poznámky  
 Toto makro vypadá takto: [_ASSERT a _asserte – makra](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)kromě toho, že `booleanExpression` je vyhodnocován v době kompilace místo v době běhu. Pokud `booleanExpression` vyhodnotí jako `FALSE` (0), [C2466 Chyba kompilátoru](../../error-messages/compiler-errors-1/compiler-error-c2466.md) se vygeneruje.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu jsme zkontrolujte, zda `sizeof` `int` je větší než nebo rovna 2 bajtů a jestli `sizeof` `long` je 1 bajtů. Program nebude zkompilování a vygeneruje [C2466 Chyba kompilátoru](../../error-messages/compiler-errors-1/compiler-error-c2466.md) protože `long` je větší než 1 bajtů.  
  
```  
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
|`_STATIC_ASSERT`|\<crtdbg.h >|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)