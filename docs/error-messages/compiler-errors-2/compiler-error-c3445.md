---
title: "C3445 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 04/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3445
dev_langs: C++
helpviewer_keywords: C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e880eca87816973d531a2662486dde0ae7c77987
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3445"></a>C3445 chyby kompilátoru
kopie – seznam inicializace '*typ*' nelze použít explicitní konstruktor  
  
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
  