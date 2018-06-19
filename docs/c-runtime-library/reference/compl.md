---
title: compl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- compl
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
- std::compl
- std.compl
- compl
dev_langs:
- C++
helpviewer_keywords:
- compl function
ms.assetid: e03f6fb5-cb8b-4afa-99c0-905f4105fb34
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14d1a4d643dd18a51b7e5dd29bc8ce282be5c9ef
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393671"
---
# <a name="compl"></a>compl

Alternativa k operátoru ~.

## <a name="syntax"></a>Syntaxe

```C

#define compl ~

```

## <a name="remarks"></a>Poznámky

Makro provede operátor ~.

## <a name="example"></a>Příklad

```cpp
// iso646_compl.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 1, result;

   result = ~a;
   cout << result << endl;

   result= compl(a);
   cout << result << endl;
}
```

```Output
-2
-2
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iso646.h – >