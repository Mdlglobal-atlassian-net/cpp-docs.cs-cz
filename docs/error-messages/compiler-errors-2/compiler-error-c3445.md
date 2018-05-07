---
title: C3445 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3445
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c37f04b907183b883772fd144ae0179683f088f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3445"></a>C3445 chyby kompilátoru

> kopie – seznam inicializace '*typ*' nelze použít explicitní konstruktor

Podle ISO standardu C ++ 17 kompilátor je potřeba vzít v úvahu explicitní konstruktor pro rozlišení přetížení v kopírování. seznam inicializace, ale musíte zvýšit chybu, pokud je ve skutečnosti vybrali této přetížení.

Od verze Visual Studio 2017, kompilátor vyhledá chyby související s vytvoření objektu pomocí inicializátoru seznamu, které nebyly nalezeny ve Visual Studiu 2015. Tyto chyby by mohlo vést k havárie nebo nedefinované chování za běhu.

## <a name="example"></a>Příklad

Následující ukázka generuje C3445.

```cpp
// C3445.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of
                      //     'A' cannot use an explicit constructor
}
```

Chcete-li chybu opravit, použijte místo toho přímé inicializace:

```cpp
// C3445b.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1{ 1 };
}
```
