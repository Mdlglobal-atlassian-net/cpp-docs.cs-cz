---
title: Vytváření instancí šablon funkce
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
ms.openlocfilehash: c4667f5ae625468cdab428706ddaff92a1c1af33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154164"
---
# <a name="function-template-instantiation"></a>Vytváření instancí šablon funkce

Při prvním volání šablony funkce každého typu kompilátor vytvoří instanci. Každá instance je verze funkce vytvořená pomocí šablony specializované pro typ funkce. Tato instance bude volána vždy při použití funkce pro typ. Je-li k dispozici několik identických instancí, i v případě odlišných modelů pak bude pro spustitelný soubor použita pouze jedna kopie instance.

Převod argumentů funkce je povolen v rámci šablony funkce pro jakýkoli pár argumentu a parametru, kde parametr není závislý na argumentu šablony.

Instance šablony funkce lze explicitně vytvořit deklarováním šablony s určitým typem jako argumentem. Například následující kód je povolen:

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

## <a name="see-also"></a>Viz také:

[Šablony funkcí](../cpp/function-templates.md)