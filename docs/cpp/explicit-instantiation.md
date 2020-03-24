---
title: Explicitní vytvoření instance
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: dbe8bebf91a174e07c7c5cce8e9caf1cf3432edf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180027"
---
# <a name="explicit-instantiation"></a>Explicitní vytvoření instance

K vytvoření instance z šablony třídy nebo funkce bez jejího použití v kódu je možné použít explicitní vytvoření instance. Vzhledem k tomu, že to je užitečné při vytváření souborů knihovny (.lib), které používají šablony pro distribuci, nejsou definice šablon bez instancí vloženy do souborů objektů (.obj).

Tento kód explicitně vytvoří instanci `MyStack` pro proměnné typu **int** a šest položek:

```cpp
template class MyStack<int, 6>;
```

Tento příkaz vytvoří instanci `MyStack` bez rezervace jakéhokoli úložného prostoru pro objekt. Kód je vygenerován pro všechny členy.

Další řádek explicitně vytvoří pouze instanci členské funkce konstruktoru:

```cpp
template MyStack<int, 6>::MyStack( void );
```

Můžete explicitně vytvořit instance šablon funkcí pomocí konkrétního argumentu typu, aby je bylo možné znovu deklarovat, jak je znázorněno v příkladu v [instanci šablony funkce](../cpp/function-template-instantiation.md).

Pomocí klíčového slova **extern** můžete zabránit automatickému vytváření instancí členů. Příklad:

```cpp
extern template class MyStack<int, 6>;
```

Podobně lze označit konkrétní členy jako externí a bez instance:

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Klíčové slovo **extern** můžete použít k zachování, že kompilátor generuje stejný kód vytváření instancí ve více než jednom modulu objektu. Pokud je volána funkce, je nutné vytvořit instanci funkce šablony použitím explicitně zadaných parametrů šablony v alespoň jednom propojeném modulu, jinak bude při sestavování programu vyvolána chyba linkeru.

> [!NOTE]
>  Klíčové slovo **extern** v specializaci se vztahuje pouze na členské funkce definované mimo tělo třídy. Funkce definované uvnitř deklarace třídy jsou považovány za vložené funkce a instance jsou vytvořeny vždy.

## <a name="see-also"></a>Viz také

[Šablony funkcí](../cpp/function-templates.md)
