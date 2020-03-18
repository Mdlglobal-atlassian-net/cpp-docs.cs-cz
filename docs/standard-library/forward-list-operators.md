---
title: operátory &lt;forward_list&gt;
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
ms.openlocfilehash: 1ddfb56c7ff68ec10c7bb56af3495e4042acb83c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421791"
---
# <a name="ltforward_listgt-operators"></a>operátory &lt;forward_list&gt;

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt předávaného seznamu na levé straně operátoru roven objektu dopředný seznam na pravé straně.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `forward_list`.

*pravé*\
Objekt typu `forward_list`.

### <a name="remarks"></a>Poznámky

Tato funkce šablony přetěžuje `operator==` k porovnání dvou objektů `forward_list`šablony třídy. Funkce vrátí `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.

## <a name="op_neq"></a>! = – operátor

Testuje, zda je objekt předávaného seznamu na levé straně operátoru roven objektu dopředný seznam na pravé straně.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `forward_list`.

*pravé*\
Objekt typu `forward_list`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se seznamy neshodují; **false** , pokud jsou seznamy stejné.

### <a name="remarks"></a>Poznámky

Tato funkce šablony vrací `!(left == right)`.

## <a name="op_lt"></a>operátor&lt;

Testuje, zda je objekt předávaného seznamu na levé straně operátoru menší než objekt dopředný seznam na pravé straně.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `forward_list`.

*pravé*\
Objekt typu `forward_list`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam na levé straně operátoru menší než, ale není rovno seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce šablony přetěžuje `operator<` k porovnání dvou objektů `forward_list`šablony třídy. Funkce vrátí `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.

## <a name="op_lt_eq"></a>operátor&lt;=

Testuje, zda je objekt předávaného seznamu na levé straně operátoru menší než nebo roven objektu dopředný seznam na pravé straně.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `forward_list`.

*pravé*\
Objekt typu `forward_list`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam na levé straně operátoru menší než nebo rovný seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce šablony vrací `!(right < left)`.

## <a name="op_gt"></a>operátor&gt;

Testuje, zda je objekt předávaného seznamu na levé straně operátoru větší než objekt dopředný seznam na pravé straně.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `forward_list`.

*pravé*\
Objekt typu `forward_list`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam na levé straně operátoru větší než seznam na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce šablony vrací `right < left`.

## <a name="op_gt_eq"></a>operátor&gt;=

Testuje, zda je objekt předávaného seznamu na levé straně operátoru větší než nebo roven objektu dopředný seznam na pravé straně.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `forward_list`.

*pravé*\
Objekt typu `forward_list`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam předek na levé straně operátoru větší než nebo roven seznamu pro dopředek na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Funkce šablony vrací `!(left < right)`.
