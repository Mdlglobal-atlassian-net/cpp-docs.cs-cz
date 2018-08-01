---
title: Explicitní vytváření instancí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb2f1c14028820525748c8e770a7263eedd3099f
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405198"
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