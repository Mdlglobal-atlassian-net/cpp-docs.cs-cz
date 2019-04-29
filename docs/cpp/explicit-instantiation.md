---
title: Explicitní vytvoření instance
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 45661653b4b8f1a4f94ece1c53aa86f4a431700b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392203"
---
# <a name="explicit-instantiation"></a>Explicitní vytvoření instance

K vytvoření instance z šablony třídy nebo funkce bez jejího použití v kódu je možné použít explicitní vytvoření instance. Vzhledem k tomu, že to je užitečné při vytváření souborů knihovny (.lib), které používají šablony pro distribuci, nejsou definice šablon bez instancí vloženy do souborů objektů (.obj).

Tento kód explicitně vytvoří instanci `MyStack` pro **int** proměnné a šest položek:

```cpp
template class MyStack<int, 6>;
```

Tento příkaz vytvoří instanci `MyStack` bez rezervace jakéhokoli úložného prostoru pro objekt. Kód je vygenerován pro všechny členy.

Další řádek explicitně vytvoří pouze instanci členské funkce konstruktoru:

```cpp
template MyStack<int, 6>::MyStack( void );
```

Lze explicitně vytvořit instanci šablony funkce s použitím specifického argumentu typu pro jejich opětovné deklarování, jak je znázorněno v příkladu v [vytváření instancí šablon funkce](../cpp/function-template-instantiation.md).

Můžete použít **extern** – klíčové slovo zabránit automatickému vytváření instancí členů. Příklad:

```cpp
extern template class MyStack<int, 6>;
```

Podobně lze označit konkrétní členy jako externí a bez instance:

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Můžete použít **extern** – klíčové slovo pro zabránění kompilátoru v generování stejného kódu instance ve více než jeden modul objektů. Pokud je volána funkce, je nutné vytvořit instanci funkce šablony použitím explicitně zadaných parametrů šablony v alespoň jednom propojeném modulu, jinak bude při sestavování programu vyvolána chyba linkeru.

> [!NOTE]
>  **Extern** – klíčové slovo ve specializaci vztahuje pouze na členské funkce definované mimo tělo třídy. Funkce definované uvnitř deklarace třídy jsou považovány za vložené funkce a instance jsou vytvořeny vždy.

## <a name="see-also"></a>Viz také:

[Šablony funkcí](../cpp/function-templates.md)