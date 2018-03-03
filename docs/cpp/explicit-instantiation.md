---
title: "Explicitní vytvoření instance | Microsoft Docs"
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
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e272652ecc82b65d0251194f17a746ddde58fcc1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="explicit-instantiation"></a>Explicitní vytvoření instance
K vytvoření instance z šablony třídy nebo funkce bez jejího použití v kódu je možné použít explicitní vytvoření instance. Vzhledem k tomu, že to je užitečné při vytváření souborů knihovny (.lib), které používají šablony pro distribuci, nejsou definice šablon bez instancí vloženy do souborů objektů (.obj).  
  
 Tento kód explicitně vytvoří instanci `MyStack` pro proměnné `int` a šest položek:  
  
```cpp  
template class MyStack<int, 6>;  
```  
  
 Tento příkaz vytvoří instanci `MyStack` bez rezervace jakéhokoli úložného prostoru pro objekt. Kód je vygenerován pro všechny členy.  
  
 Další řádek explicitně vytvoří pouze instanci členské funkce konstruktoru:  
  
```cpp  
template MyStack<int, 6>::MyStack( void );  
```  
  
 Můžete explicitně vytvořit instanci šablony funkcí s použitím konkrétního typu argument znovu deklarovat, jak je znázorněno v příkladu v [vytváření instancí šablon funkce](../cpp/function-template-instantiation.md).  
  
 Pro zabránění automatickému vytváření instancí členů lze použít klíčové slovo `extern`. Příklad:  
  
```cpp  
extern template class MyStack<int, 6>;  
```  
  
 Podobně lze označit konkrétní členy jako externí a bez instance:  
  
```cpp  
extern template MyStack<int, 6>::MyStack( void );  
```  
  
 Pro zabránění kompilátoru v generování stejného kódu instance pro více než jeden modul objektů lze použít klíčové slovo `extern`. Pokud je volána funkce, je nutné vytvořit instanci funkce šablony použitím explicitně zadaných parametrů šablony v alespoň jednom propojeném modulu, jinak bude při sestavování programu vyvolána chyba linkeru.  
  
> [!NOTE]
>  Klíčové slovo `extern` se ve specializaci vztahuje pouze na členské funkce definované mimo tělo třídy. Funkce definované uvnitř deklarace třídy jsou považovány za vložené funkce a instance jsou vytvořeny vždy.  
  
## <a name="see-also"></a>Viz také  
 [Šablony funkcí](../cpp/function-templates.md)