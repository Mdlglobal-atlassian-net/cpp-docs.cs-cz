---
title: Funkce vytváření instancí šablon | Dokumentace Microsoftu
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
ms.openlocfilehash: fb94a54c4f99b79e3be742c5b1448151cff140c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116786"
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