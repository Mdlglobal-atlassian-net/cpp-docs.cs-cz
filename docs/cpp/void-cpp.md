---
title: void (C++) | Microsoft Docs
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
ms.openlocfilehash: de70ec6758109bc765d0cec3552762288d51ded2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="void-c"></a>void (C++)
Při použití jako návratový typ funkce určuje klíčové slovo `void`, že funkce nevrací hodnotu. Při použití pro seznam parametrů funkce určuje void, že funkce nepřebírá žádné parametry. Při použití v deklaraci ukazatele určuje void, že je ukazatel „univerzální“.  
  
 Pokud je typ ukazatele **void \***, ukazatele může ukazovat na všechny proměnné, která není deklarovaný s **const** nebo `volatile` – klíčové slovo. Ukazatel void nelze přímo odkázat, pokud není přetypován na jiný typ. Ukazatel void lze převést na libovolný typ datového ukazatele.  
  
 Ukazatel void může v jazyce C++ odkazovat na funkci, ale nikoli na člen třídy.  
  
 Nelze deklarovat proměnnou typu void.  
  
## <a name="example"></a>Příklad  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Základní typy](../cpp/fundamental-types-cpp.md)