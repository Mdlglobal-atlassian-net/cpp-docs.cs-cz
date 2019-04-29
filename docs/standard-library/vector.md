---
title: '&lt;vector&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 348b5c53ecd3fb7900d03fed7c1209a2c94eeb4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410851"
---
# <a name="ltvectorgt"></a>&lt;vector&gt;

Definuje kontejner šablony třídy vektoru a několik podpůrných šablon.

`vector` Je kontejner, který slouží k uspořádání prvků daného typu v lineární posloupnosti. Umožňuje rychlý náhodný přístup k libovolný element a dynamické přidání a odebrání do a z pořadí. `vector` Je kontejneru upřednostňované pořadí, když v na úrovni premium je výkon náhodný přístup.

Další informace o třídě `vector`, naleznete v tématu [vector – třída](../standard-library/vector-class.md). Informace o tom, specializace `vector<bool>`, naleznete v tématu [vektoru\<bool > třída](../standard-library/vector-bool-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
namespace std {
template <class Type, class Allocator>
class vector;
template <class Allocator>
class vector<bool>;

template <class Allocator>
struct hash<vector<bool, Allocator>>;

// TEMPLATE FUNCTIONS
template <class Type, class Allocator>
bool operator== (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator!= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<(
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator> (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator>= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
void swap (
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Parametr šablony pro typ dat uložených ve vektoru.

*Allocator –*<br/>
Parametr šablony pro uložený objekt alokátoru za přidělování a vracení paměti.

*doleva*<br/>
V operaci porovnání prvnímu vektoru (vlevo)

*doprava*<br/>
Druhý (vpravo) vektoru v operaci porovnání.

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor! =](../standard-library/vector-operators.md#op_neq)|Testuje, zda vektorový objekt na levé straně operátoru není roven vektorový objekt na pravé straně.|
|[Operator <](../standard-library/vector-operators.md#op_lt)|Testuje, zda je objekt vektoru na levé straně operátoru menší než vektorový objekt na pravé straně.|
|[– Operátor\<=](../standard-library/vector-operators.md#op_gt_eq)|Testuje, zda je objekt vektoru na levé straně operátoru je menší než nebo rovna hodnotě vektorový objekt na pravé straně.|
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|Testuje, zda vektorový objekt na levé straně operátoru roven objektu vektoru na pravé straně.|
|[operator>](../standard-library/vector-operators.md#op_gt)|Testuje, zda je objekt vektoru na levé straně operátoru větší než vektorový objekt na pravé straně.|
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|Testuje, zda vektorový objekt na levé straně operátoru větší než nebo rovna hodnotě vektorový objekt na pravé straně.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[vector – třída](../standard-library/vector-class.md)|Třída šablony kontejnery sekvence, které uspořádat prvky daného typu v lineární uspořádání a umožňují rychlý náhodný přístup k libovolnému prvku.|

### <a name="specializations"></a>Specializace

|||
|-|-|
|[vektor\<bool > třída](../standard-library/vector-bool-class.md)|Úplné specializace šablony vektoru třídu pro prvky typu `bool` s Alokátor pro základní typ používán specializací.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vektoru >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
