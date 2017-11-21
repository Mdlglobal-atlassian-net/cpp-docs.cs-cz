---
title: "Funkce objekty ve standardní knihovně C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functors
- C++ Standard Library, functors
- C++ Standard Library, function objects
- function objects
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 90b37372123031026017e23c683a5a65555577ca
ms.sourcegitcommit: b3ffb717e2af6ca8072b56bf4aa96b3afff73414
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2017
---
# <a name="function-objects-in-the-c-standard-library"></a>Objekty funkcí ve standardní knihovně C++
A *objekt funkce*, nebo *functor*, je žádný typ, který implementuje Operator() –. Tento operátor odkazuje jako *operátor volání* nebo někdy *operátor aplikací*. Standardní knihovna C++ pomocí funkce objektů především jako kritéria pro kontejnery a algoritmy řazení.  
  
 Objekty funkcí poskytují dvě hlavní výhody přes volání přímých funkce. První je, že objekt funkce může obsahovat stavu. Druhý je, že je typu objekt funkce a proto je lze použít jako parametr šablony.  
  
## <a name="creating-a-function-object"></a>Vytvoření objektu – funkce  
 Pokud chcete vytvořit objekt funkce, vytvoření typu a implementovat Operator() –, jako například:  
  
```
class Functor  
{  
public:  
    int operator()(int a, int b)  
    {  
        return a < b;  
    }  
};  
```

 Poslední řádek `main` funkce ukazuje, jak volat objekt funkce. Toto volání vypadá volání funkce, ale ve skutečnosti volá Operator() – Functor typu. Tato podobnosti mezi volání objekt funkce a funkce je, jak objekt funkce termín pocházejí.  
  
## <a name="function-objects-and-containers"></a>Funkce objektů a kontejnerů  
 Standardní knihovna C++ obsahuje několik objektů funkce v [ \<funkční >](../standard-library/functional.md) soubor hlaviček. Jedno použití těchto objektů funkce je jako kritérium řazení pro kontejnery. Například `set` kontejneru je deklarovaná následujícím způsobem:  
  
```  
template <class Key,  
    class Traits=less<Key>,  
    class Allocator=allocator<Key>>  
class set  
```  
  
 Druhý argument šablony je objekt funkce `less`. Tento objekt funkce vrátí `true` Pokud první parametr předaný je menší než druhý parametr předaný. Vzhledem k tomu, že některé kontejnery seřadit jejich elementů, potřebuje způsob porovnání dva elementy kontejneru a toho dosahuje pomocí funkce objekt. Můžete definovat vlastní řazení kritéria pro kontejnery vytvořením objekt funkce a zadáte v seznamu šablon pro příslušný kontejner.  
  
## <a name="function-objects-and-algorithms"></a>Objekty funkcí a algoritmy  
 Další používání funkční objekty se v algoritmy. Například `remove_if` algoritmus je deklarovaná následujícím způsobem:  
  
```  
template <class ForwardIterator, class Predicate>  
ForwardIterator remove_if(
    ForwardIterator first,  
    ForwardIterator last,  
    Predicate pred);
```  
  
 Poslední argument `remove_if` je objekt funkce, který vrací logickou hodnotu ( *predikát*). Pokud je výsledek objektu funkce `true`, pak se odebere element z kontejneru přistupuje iterátory `first` a `last`. Můžete použít libovolnou funkce objektů v deklarována [ \<funkční >](../standard-library/functional.md) záhlaví pro argument `pred` nebo můžete vytvořit vlastní.  
  
## <a name="see-also"></a>Viz také  
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)

