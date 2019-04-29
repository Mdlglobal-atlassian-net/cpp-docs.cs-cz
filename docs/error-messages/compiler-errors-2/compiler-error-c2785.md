---
title: Compiler Error C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: fcf2bbb01f2aac668ff52884a6ccfb36c66aa89d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395375"
---
# <a name="compiler-error-c2785"></a>Compiler Error C2785

"declaration1" a 'declaration2' mají rozdílné návratové typy

Návratový typ specializace šablony funkce se liší od návratový typ šablony primární funkce.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zkontrolujte všechny specializace šablony funkce pro zajištění konzistence.

## <a name="example"></a>Příklad

Následující ukázka generuje C2785:

```
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```