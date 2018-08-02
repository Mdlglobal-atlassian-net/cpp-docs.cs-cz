---
title: void (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- void_cpp
dev_langs:
- C++
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbb46302c2ae8834ab9a2a626a3bfb77c41996a2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461475"
---
# <a name="void-c"></a>void (C++)
Při použití jako návratový typ funkce **void** – klíčové slovo určuje, že funkce nevrací hodnotu. Při použití pro seznam parametrů funkce určuje void, že funkce nepřebírá žádné parametry. Při použití v deklaraci ukazatele určuje void, že je ukazatel „univerzální“.  
  
 Pokud je ukazatel typu `void *`, může odkazovat na libovolnou proměnnou, která není deklarována s **const** nebo **volatile** – klíčové slovo. Ukazatel void nelze přímo odkázat, pokud není přetypován na jiný typ. Ukazatel void lze převést na libovolný typ datového ukazatele.  
  
 Ukazatel void může v jazyce C++ odkazovat na funkci, ale nikoli na člen třídy.  
  
 Nelze deklarovat proměnnou typu void.  
  
## <a name="example"></a>Příklad  
  
```cpp 
// void.cpp  
void vobject;   // C2182  
void *pv;   // okay  
int *pint; int i;  
int main() {  
   pv = &i;  
   // Cast optional in C required in C++  
   pint = (int *)pv;  
}   
``` 
  
## <a name="see-also"></a>Viz také:  
 [klíčová slova](../cpp/keywords-cpp.md)   
 [Základní typy](../cpp/fundamental-types-cpp.md)