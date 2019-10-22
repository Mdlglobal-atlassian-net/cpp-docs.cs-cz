---
title: '&lt;vector &gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 19068de41cfdcb17ae624858c137bf624851479f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684071"
---
# <a name="ltvectorgt"></a>&lt;vector &gt;

Definuje vektor šablony třídy kontejneru a několik podpůrných šablon.

@No__t_0 je kontejner, který organizuje prvky daného typu v lineární sekvenci. Umožňuje rychlý náhodný přístup k jakémukoli prvku a dynamické přidávání a odebírání do a z sekvence. @No__t_0 je preferovaným kontejnerem pro sekvenci, když je výkon náhodného přístupu na úrovni Premium.

> [!NOTE]
> Knihovna \<vector > používá také příkaz `#include <initializer_list>`.

Další informace o třídě `vector` naleznete v tématu [Vector Class](../standard-library/vector-class.md). Informace o `vector<bool>` specializace naleznete v tématu [vector \<bool > Class](../standard-library/vector-bool-class.md).

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

*Zadejte* \
Parametr šablony pro typ dat uložených ve vektoru.

@No__t_1 *přidělování*
Parametr šablony pro uložený objekt přidělování zodpovědný za přidělení a zrušení přidělení paměti.

*levý* \
První (levý) vektor v operaci porovnání

*pravé* \
Druhý (pravý) vektor v operaci porovnání.

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[podnikatel! =](../standard-library/vector-operators.md#op_neq)|Testuje, zda vektorový objekt na levé straně operátoru není roven objektu Vector na pravé straně.|
|[operátor <](../standard-library/vector-operators.md#op_lt)|Testuje, zda je objekt Vector na levé straně operátoru menší než objekt Vector na pravé straně.|
|[operátor \< =](../standard-library/vector-operators.md#op_gt_eq)|Testuje, zda je vektorový objekt na levé straně operátoru menší než nebo roven objektu Vector na pravé straně.|
|[operator = = – operátor](../standard-library/vector-operators.md#op_eq_eq)|Testuje, zda je objekt Vector na levé straně operátoru roven objektu Vector na pravé straně.|
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
|[Třída Vector \<bool >](../standard-library/vector-bool-class.md)|Plná specializace vektoru šablony třídy pro prvky typu `bool` s přidělováním pro podkladový typ používaný specializací.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vector >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
