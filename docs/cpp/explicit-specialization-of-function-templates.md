---
title: Explicitní specializace šablon funkcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8b6a56a0a1dce5d07007898dec486d0e3b080c4
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407686"
---
# <a name="explicit-specialization-of-function-templates"></a>Explicitní specializace šablon funkcí
Pomocí šablony funkce lze definovat zvláštní chování konkrétního typu poskytnutím explicitní specializace (přepsáním) šablony funkce daného typu. Příklad:  
  
```cpp
template<> void MySwap(double a, double b);  
```  
  
 Tato deklarace umožňuje definovat různé funkce pro **double** proměnné. Nešablonové funkce, převody standardních typů, jako je (například povýšením proměnné typu **float** k **double**) se použijí.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Šablony funkcí](../cpp/function-templates.md)