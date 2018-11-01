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
ms.openlocfilehash: 3d91383f895f1a8be983efe42f685419ca988823
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665176"
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