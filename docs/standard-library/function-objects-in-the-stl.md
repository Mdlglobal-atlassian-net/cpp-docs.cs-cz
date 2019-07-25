---
title: Objekty funkce ve C++ standardní knihovně
ms.date: 03/15/2019
helpviewer_keywords:
- functors
- C++ Standard Library, functors
- C++ Standard Library, function objects
- function objects
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
ms.openlocfilehash: 4df8096603b53d05e050750a860c76528a44b28c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454065"
---
# <a name="function-objects-in-the-c-standard-library"></a>Objekty funkce ve C++ standardní knihovně

*Objekt funkce*, nebo *funktor*, je jakýkoli typ, který implementuje operátor (). Tento operátor je označován jako *operátor volání* nebo někdy *operátorem aplikace*. C++ Standardní knihovna používá objekty funkce primárně jako kritéria řazení pro kontejnery a v algoritmech.

Objekty funkce poskytují dvě hlavní výhody v rámci přímého volání funkce. První je, že objekt funkce může obsahovat stav. Druhým je, že objekt funkce je typu, a proto lze použít jako parametr šablony.

## <a name="creating-a-function-object"></a>Vytvoření objektu funkce

Chcete-li vytvořit objekt funkce, vytvořte typ a implementujte operátor (), například:

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

Poslední řádek `main` funkce ukazuje, jak zavolat objekt funkce. Toto volání vypadá jako volání funkce, ale ve skutečnosti volá operátor () typu funktor. Tato podobnost mezi voláním objektu funkce a funkcí je způsob, jakým se dorazila pojem objektu funkce.

## <a name="function-objects-and-containers"></a>Objekty funkce a kontejnery

Standardní knihovna obsahuje několik objektů funkcí v [ \<](../standard-library/functional.md) souboru hlaviček funkčního >. C++ Jedno použití těchto objektů funkcí je jako kritérium řazení pro kontejnery. Například `set` kontejner je deklarován následujícím způsobem:

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

Druhý argument šablony je objekt `less`funkce. Tento objekt funkce vrátí **hodnotu true** , pokud je první parametr menší než druhý parametr. Vzhledem k tomu, že některé kontejnery řadí jejich prvky, kontejner vyžaduje způsob porovnávání dvou prvků. Porovnání je provedeno pomocí objektu Function. Můžete definovat vlastní kritéria řazení pro kontejnery vytvořením objektu funkce a jeho zadáním v seznamu šablon pro kontejner.

## <a name="function-objects-and-algorithms"></a>Objekty a algoritmy funkcí

Jiné použití funkčních objektů je v algoritmech. Například `remove_if` algoritmus je deklarován následujícím způsobem:

```cpp
template <class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);
```

Poslední argument pro `remove_if` je objekt funkce, který vrací logickou hodnotu ( *predikát*). Pokud je výsledkem objektu funkce **hodnota true**, pak je element odebrán z kontejneru, ke kterému přistupovali iterátory `first` a. `last` Můžete použít kterýkoli z objektů Function deklarovaných v `pred` [ \<hlavičce funkční >](../standard-library/functional.md) pro argument nebo můžete vytvořit vlastní.

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
