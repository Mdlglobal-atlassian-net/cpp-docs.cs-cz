---
title: Objekty funkcí ve standardní knihovně C++
ms.date: 03/15/2019
helpviewer_keywords:
- functors
- C++ Standard Library, functors
- C++ Standard Library, function objects
- function objects
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
ms.openlocfilehash: 310d846285612ad94ec9d66672fcb996557b07e2
ms.sourcegitcommit: 9e85c2e029d06b4c1c69837437468718b4d54908
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2019
ms.locfileid: "58172956"
---
# <a name="function-objects-in-the-c-standard-library"></a>Objekty funkcí ve standardní knihovně C++

A *objektu funkce*, nebo *funktor*, je libovolný typ, který implementuje operator(). Tento operátor se označuje jako *operátor volání* nebo někdy také *operátor aplikací*. Objekty funkce standardní knihovny C++ používá především jako kritéria pro kontejnery a algoritmy řazení.

Objekty funkce poskytují dvě hlavní výhody oproti volání rovný funkce. První je, že objekt funkce může obsahovat stavu. Druhým je, že objekt funkce je typ a proto může sloužit jako parametr šablony.

## <a name="creating-a-function-object"></a>Vytvoření objektu – funkce

Chcete-li vytvořit objekt funkce, vytvoření typu a implementaci operator(), jako například:

```cpp
class Functor
{
public:
    int operator()(int a, int b)
    {
        return a < b;
    }
};

int main()
{
    Functor f;
    int a = 5;
    int b = 7;
    int ans = f(a, b);
}
```

Poslední řádek `main` funkce ukazuje, jak volat funkce objektu. Toto volání vypadá jako volání funkce, ale jeho skutečně volání operator() typu Funktor. Tato podobnosti mezi volání objektu funkce a funkce je, jak objekt funkce termín přišel.

## <a name="function-objects-and-containers"></a>Funkce objektů a kontejnerů

Standardní knihovny C++ obsahuje několik objektů funkce v [ \<funkční >](../standard-library/functional.md) hlavičkový soubor. Jeden z těchto objektů funkce slouží jako kritérium řazení pro kontejnery. Například `set` kontejneru je deklarována následovně:

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

Druhý argument šablony je objekt funkce `less`. Tento objekt funkce vrátí **true** Pokud první parametr je menší než druhý parametr. Některé kontejnery řadí jejich prvky, musí kontejneru způsob porovnání dvou prvků. Porovnání se provádí pomocí objektu funkce. Můžete definovat vlastní řazení kritéria pro kontejnery vytvořením funkce objektu a jeho zadáním v seznamu šablon pro kontejner.

## <a name="function-objects-and-algorithms"></a>Objekty funkcí a algoritmy

Další možností použití funkční objektů je v algoritmy. Například `remove_if` algoritmus je deklarována následovně:

```cpp
template <class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);
```

Poslední argument `remove_if` je objekt funkce, který vrací logickou hodnotu ( *predikátu*). Pokud je výsledek objektu funkce **true**, pak element se odebere z kontejneru přistupuje iterátory `first` a `last`. Můžete použít některý z objektů funkce deklarované v [ \<funkční >](../standard-library/functional.md) záhlaví pro argument `pred` nebo můžete vytvořit svoje vlastní.

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
