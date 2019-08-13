---
title: '&lt;vektorový&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 59424a9f6a9434b5d7d3f4298cbb0bc03926621c
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957054"
---
# <a name="ltvectorgt"></a>&lt;vektorový&gt;

Definuje vektor třídy šablony kontejneru a několik pomocných šablon.

`vector` Je kontejner, který organizuje prvky daného typu v lineární sekvenci. Umožňuje rychlý náhodný přístup k jakémukoli prvku a dynamické přidávání a odebírání do a z sekvence. `vector` Je upřednostňovaný kontejner pro sekvenci, pokud je výkon náhodného přístupu na úrovni Premium.

> [!NOTE]
> Vektorová knihovna > také `#include <initializer_list>` používá příkaz. \<

Další informace o třídě `vector`naleznete v tématu [Vector Class](../standard-library/vector-class.md). Informace o specializaci `vector<bool>`naleznete v tématu [Vector\<bool > Class](../standard-library/vector-bool-class.md).

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

*Textový*\
Parametr šablony pro typ dat uložených ve vektoru.

*Dělující*\
Parametr šablony pro uložený objekt přidělování zodpovědný za přidělení a zrušení přidělení paměti.

*zbývá*\
První (levý) vektor v operaci porovnání

*Kliknutím*\
Druhý (pravý) vektor v operaci porovnání.

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[podnikatel! =](../standard-library/vector-operators.md#op_neq)|Testuje, zda vektorový objekt na levé straně operátoru není roven objektu Vector na pravé straně.|
|[operátor <](../standard-library/vector-operators.md#op_lt)|Testuje, zda je objekt Vector na levé straně operátoru menší než objekt Vector na pravé straně.|
|[podnikatel\<=](../standard-library/vector-operators.md#op_gt_eq)|Testuje, zda je vektorový objekt na levé straně operátoru menší než nebo roven objektu Vector na pravé straně.|
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|Testuje, zda je objekt Vector na levé straně operátoru roven objektu Vector na pravé straně.|
|[operátor >](../standard-library/vector-operators.md#op_gt)|Testuje, zda je objekt Vector na levé straně operátoru větší než objekt Vector na pravé straně.|
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|Testuje, zda je objekt Vector na levé straně operátoru větší než nebo roven objektu Vector na pravé straně.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[vector – třída](../standard-library/vector-class.md)|Šablona třídy sekvenčních kontejnerů, které uspořádávají prvky daného typu v lineárním uspořádání a umožňují rychlý náhodný přístup k jakémukoli prvku.|

### <a name="specializations"></a>Specializace

|||
|-|-|
|hash|Vrátí hodnotu hash vektoru.|
|[Vector\<– logická > – třída](../standard-library/vector-bool-class.md)|Plná specializace vektoru třídy šablony pro prvky typu `bool` s přidělováním pro podkladový typ používaný specializací.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> vektoru

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
