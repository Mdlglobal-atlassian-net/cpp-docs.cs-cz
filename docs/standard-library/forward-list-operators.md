---
title: '&lt;forward_list –&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
dev_langs:
- C++
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: f4dd02275364b611ef5f9011041840a10709aa3f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965627"
---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list –&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[– Operátor&gt;](#op_gt)|[– Operátor&gt;=](#op_gt_eq)|
|[– Operátor&lt;](#op_lt)|[– Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  Operator ==

Testuje, zda objekt dopředu seznamu na levé straně operátoru roven objektu dopředné seznamu na pravé straně.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Objekt typu `forward_list`.|
|*doprava*|Objekt typu `forward_list`.|

### <a name="remarks"></a>Poznámky

Tato funkce šablony přetížení `operator==` k porovnání dvou objektů třídy šablony `forward_list`. Funkce vrátí `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.

## <a name="op_neq"></a>  Operator! =

Testuje, zda je objekt dopředu seznamu na levé straně operátoru není roven objektu dopředné seznamu na pravé straně.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Objekt typu `forward_list`.|
|*doprava*|Objekt typu `forward_list`.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud nejsou stejné; seznamy **false** Pokud seznamy jsou si rovny.

### <a name="remarks"></a>Poznámky

Tato šablona funkce vrátí `!(left == right)`.

## <a name="op_lt"></a>  – Operátor&lt;

Testuje, zda objekt dopředu seznamu na levé straně operátoru menší než objekt dopředu seznamu na pravé straně.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Objekt typu `forward_list`.|
|*doprava*|Objekt typu `forward_list`.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** -li v seznamu na levé straně operátoru menší než, ale není v seznamu na pravé straně operátoru roven; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce šablony přetížení `operator<` k porovnání dvou objektů třídy šablony `forward_list`. Funkce vrátí `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Testuje, zda je objekt seznamu vpřed na levé straně operátoru je menší než nebo roven objektu dopředné seznamu na pravé straně.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Objekt typu `forward_list`.|
|*doprava*|Objekt typu `forward_list`.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** -li v seznamu na levé straně operátoru menší než nebo rovna hodnotě v seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato šablona funkce vrátí `!(right < left)`.

## <a name="op_gt"></a>  – Operátor&gt;

Testuje, zda objekt dopředu seznamu na levé straně operátoru větší než objekt dopředu seznamu na pravé straně.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Objekt typu `forward_list`.|
|*doprava*|Objekt typu `forward_list`.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je v seznamu na levé straně operátoru větší než v seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato šablona funkce vrátí `right < left`.

## <a name="op_gt_eq"></a>  – Operátor&gt;=

Testuje, zda je objekt dopředu seznamu na levé straně operátoru větší než nebo roven objektu dopředné seznamu na pravé straně.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doleva*|Objekt typu `forward_list`.|
|*doprava*|Objekt typu `forward_list`.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** při přesměrování seznamu na levé straně operátoru větší než nebo rovna seznamu vpřed na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí `!(left < right)`.

## <a name="see-also"></a>Viz také:

[<forward_list>](../standard-library/forward-list.md)<br/>
