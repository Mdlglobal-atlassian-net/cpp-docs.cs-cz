---
title: Vytváření instancí šablon funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6374dcd9dad263afd0961be91971d3283ba863ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="function-template-instantiation"></a>Vytváření instancí šablon funkce
Při prvním volání šablony funkce každého typu kompilátor vytvoří instanci. Každá instance je verze funkce vytvořená pomocí šablony specializované pro typ funkce. Tato instance bude volána vždy při použití funkce pro typ. Je-li k dispozici několik identických instancí, i v případě odlišných modelů pak bude pro spustitelný soubor použita pouze jedna kopie instance.  
  
 Převod argumentů funkce je povolen v rámci šablony funkce pro jakýkoli pár argumentu a parametru, kde parametr není závislý na argumentu šablony.  
  
 Instance šablony funkce lze explicitně vytvořit deklarováním šablony s určitým typem jako argumentem. Například je povoleno následující kód:  
  
```cpp
// function_template_instantiation.cpp  
template<class T> void f(T) { }  
  
// Instantiate f with the explicitly specified template.  
// argument 'int'  
//  
template void f<int> (int);  
  
// Instantiate f with the deduced template argument 'char'.  
template void f(char);  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Šablony funkcí](../cpp/function-templates.md)
