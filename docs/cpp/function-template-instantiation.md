---
title: "Vytváření instancí šablon funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 41bf7f6ba3a2a17c6355ee9239cadb6e5014ee96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
