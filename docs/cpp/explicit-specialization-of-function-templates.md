---
title: "Explicitní specializace šablon funkcí | Microsoft Docs"
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
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58480c4f118a083dc7c9f97f3a0014e9d0cc294a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="explicit-specialization-of-function-templates"></a>Explicitní specializace šablon funkcí
Pomocí šablony funkce lze definovat zvláštní chování konkrétního typu poskytnutím explicitní specializace (přepsáním) šablony funkce daného typu. Příklad:  
  
```cpp
template<> void MySwap(double a, double b);  
```  
  
 Toto prohlášení umožňuje definovat různé funkce pro **dvojité** proměnné. Jako funkce bez šablony, převody standardní typu (například povýšení proměnné typu **float** k **dvojité**) se použijí.  
  
## <a name="example"></a>Příklad  
  
```cpp
// explicit_specialization.cpp  
template<class T> void f(T t)  
{  
};  
  
// Explicit specialization of f with 'char' with the  
// template argument explicitly specified:  
//  
template<> void f<char>(char c)  
{  
}  
  
// Explicit specialization of f with 'double' with the  
// template argument deduced:  
//  
template<> void f(double d)  
{  
}  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Šablony funkcí](../cpp/function-templates.md)
