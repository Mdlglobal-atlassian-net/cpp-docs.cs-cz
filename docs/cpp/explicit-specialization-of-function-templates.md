---
title: Explicitní specializace šablon funkcí
ms.date: 11/04/2016
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
ms.openlocfilehash: c9d77cef790bdd0a65651ffb7246e685175482b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179988"
---
# <a name="explicit-specialization-of-function-templates"></a>Explicitní specializace šablon funkcí

Pomocí šablony funkce lze definovat zvláštní chování konkrétního typu poskytnutím explicitní specializace (přepsáním) šablony funkce daného typu. Příklad:

```cpp
template<> void MySwap(double a, double b);
```

Tato deklarace umožňuje definovat jinou funkci pro **dvojité** proměnné. Podobně jako jiné funkce než šablony jsou aplikovány převody standardních typů (například zvýšení úrovně proměnné typu **float** na hodnotu **Double**).

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
