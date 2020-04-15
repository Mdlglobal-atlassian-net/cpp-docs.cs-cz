---
title: Explicitní vytvoření instance
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 0b1290bc23c56c0f35ddd3bb93e37ce4f5f0d2ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361951"
---
# <a name="explicit-instantiation"></a>Explicitní vytvoření instance

K vytvoření instance z šablony třídy nebo funkce bez jejího použití v kódu je možné použít explicitní vytvoření instance. Vzhledem k tomu, že to je užitečné při vytváření souborů knihovny (.lib), které používají šablony pro distribuci, nejsou definice šablon bez instancí vloženy do souborů objektů (.obj).

Tento kód explicitně `MyStack` konkretizovat **pro int** proměnné a šest položek:

```cpp
template class MyStack<int, 6>;
```

Tento příkaz vytvoří instanci `MyStack` bez rezervace jakéhokoli úložného prostoru pro objekt. Kód je vygenerován pro všechny členy.

Další řádek explicitně vytvoří pouze instanci členské funkce konstruktoru:

```cpp
template MyStack<int, 6>::MyStack( void );
```

Šablony funkcí můžete explicitně vytvořit pomocí konkrétního argumentu typu k jejich opětovnému deklarování, jak je znázorněno v příkladu v [instanci šablony funkce](../cpp/function-template-instantiation.md).

Můžete použít **extern** klíčové slovo, aby se zabránilo automatické vytváření instancí členů. Příklad:

```cpp
extern template class MyStack<int, 6>;
```

Podobně lze označit konkrétní členy jako externí a bez instance:

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Klíčové slovo **extern** můžete použít k zabránění kompilátoru ve generování stejného kódu instance ve více než jednom objektovém modulu. Pokud je volána funkce, je nutné vytvořit instanci funkce šablony použitím explicitně zadaných parametrů šablony v alespoň jednom propojeném modulu, jinak bude při sestavování programu vyvolána chyba linkeru.

> [!NOTE]
> Klíčové slovo **extern** v specializaci se vztahuje pouze na členské funkce definované mimo tělo třídy. Funkce definované uvnitř deklarace třídy jsou považovány za vložené funkce a instance jsou vytvořeny vždy.

## <a name="see-also"></a>Viz také

[Šablony funkcí](../cpp/function-templates.md)
