---
title: '&lt;forward_list –&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: 64a49273cafd72158f176ee34ec271557ebee097
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240665"
---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list –&gt; operátory

## <a name="op_eq_eq"></a> Operator ==

Testuje, zda objekt dopředu seznamu na levé straně operátoru roven objektu dopředné seznamu na pravé straně.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `forward_list`.

*doprava*\
Objekt typu `forward_list`.

### <a name="remarks"></a>Poznámky

Tato funkce šablony přetížení `operator==` k porovnání dvou objektů třídy šablony `forward_list`. Funkce vrátí `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.

## <a name="op_neq"></a> Operator! =

Testuje, zda je objekt dopředu seznamu na levé straně operátoru není roven objektu dopředné seznamu na pravé straně.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `forward_list`.

*doprava*\
Objekt typu `forward_list`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nejsou stejné; seznamy **false** Pokud seznamy jsou si rovny.

### <a name="remarks"></a>Poznámky

Tato šablona funkce vrátí `!(left == right)`.

## <a name="op_lt"></a> – Operátor&lt;

Testuje, zda objekt dopředu seznamu na levé straně operátoru menší než objekt dopředu seznamu na pravé straně.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `forward_list`.

*doprava*\
Objekt typu `forward_list`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** -li v seznamu na levé straně operátoru menší než, ale není v seznamu na pravé straně operátoru roven; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce šablony přetížení `operator<` k porovnání dvou objektů třídy šablony `forward_list`. Funkce vrátí `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.

## <a name="op_lt_eq"></a> – Operátor&lt;=

Testuje, zda je objekt seznamu vpřed na levé straně operátoru je menší než nebo roven objektu dopředné seznamu na pravé straně.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `forward_list`.

*doprava*\
Objekt typu `forward_list`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** -li v seznamu na levé straně operátoru menší než nebo rovna hodnotě v seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato šablona funkce vrátí `!(right < left)`.

## <a name="op_gt"></a> – Operátor&gt;

Testuje, zda objekt dopředu seznamu na levé straně operátoru větší než objekt dopředu seznamu na pravé straně.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `forward_list`.

*doprava*\
Objekt typu `forward_list`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je v seznamu na levé straně operátoru větší než v seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato šablona funkce vrátí `right < left`.

## <a name="op_gt_eq"></a> – Operátor&gt;=

Testuje, zda je objekt dopředu seznamu na levé straně operátoru větší než nebo roven objektu dopředné seznamu na pravé straně.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `forward_list`.

*doprava*\
Objekt typu `forward_list`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** při přesměrování seznamu na levé straně operátoru větší než nebo rovna seznamu vpřed na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí `!(left < right)`.
