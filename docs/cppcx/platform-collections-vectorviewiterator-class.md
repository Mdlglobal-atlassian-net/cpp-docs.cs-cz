---
title: 'Platform::Collections:: vectorviewiterator – třída'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 4d4a591c6febdf6e34757251c4de5d01a9e2fa87
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743739"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections:: vectorviewiterator – třída

Poskytuje standardní knihovny šablon iterátor pro objekty, které jsou odvozeny z modulu Windows Runtime`IVectorView` rozhraní.

`ViewVectorIterator` je proxy iterátor, který ukládá prvky typu `VectorProxy<T>`. Objekt proxy je však téměř nikdy viditelné pro uživatelský kód. Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vlastnost typename třídy VectorViewIterator šablony.

### <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`difference_type`|Rozdíl ukazatelů (ptrdiff_t).|
|`iterator_category`|Kategorie iterátor náhodného přístupu (:: std::random_access_iterator_tag).|
|`pointer`|Ukazatel na vnitřní typ, který se vyžaduje k provedení VectorViewIterator.|
|`reference`|Odkaz na vnitřní typ, který se vyžaduje k provedení VectorViewIterator.|
|`value_type`|`T` Typename.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[VectorViewIterator::VectorViewIterator](#ctor)|Inicializuje novou instanci třídy VectorViewIterator.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[VectorViewIterator::operator-– operátor](#operator-minus)|Odečte buď zadaný počet prvků z aktuální iterace, což má za následek nové iterátor nebo iterátor zadané z aktuální iterace, což má za následek počet prvků mezi iterátory.|
|[VectorViewIterator::operator-- Operator](#operator-decrement)|Sníží aktuální VectorViewIterator.|
|[VectorViewIterator::operator!= Operator](#operator-inequality)|Určuje, zda aktuální VectorViewIterator není roven zadané VectorViewIterator.|
|[VectorViewIterator::operator * – operátor](#operator-dereference)|Získá odkaz na prvek určeném aktuálním VectorViewIterator.|
|[VectorViewIterator::operator\[\]](#operator-at)|Získá odkaz na prvek, který je zadaný posun z aktuální VectorViewIterator.|
|[VectorViewIterator::operator + – operátor](#operator-plus)|Vrátí VectorViewIterator, odkazující na prvek na zadané posunutí ze zadaného VectorViewIterator.|
|[VectorViewIterator::operator ++ – operátor](#operator-increment)|Aktuální VectorViewIterator zvýší.|
|[VectorViewIterator::operator+= Operator](#operator-plus-assign)|Zvětší aktuální VectorViewIterator podle zadaného posunu.|
|[VectorViewIterator::operator < – operátor](#operator-less-than)|Označuje, zda aktuální VectorViewIterator je nižší než zadané VectorViewIterator.|
|[VectorViewIterator::operator\<= Operator](#operator-less-than-or-equals)|Označuje, zda aktuální VectorViewIterator je menší než nebo rovna hodnotě zadané VectorViewIterator.|
|[VectorViewIterator::operator-= Operator](#operator-minus-assign)|Sníží aktuální VectorViewIterator podle zadaného posunu.|
|[VectorViewIterator::operator== Operator](#operator-equality)|Určuje, zda aktuální VectorViewIterator rovná zadané VectorViewIterator.|
|[VectorViewIterator::operator> Operator](#operator-greater-than)|Označuje, zda je aktuální VectorViewIterator větší než zadaný VectorViewIterator.|
|[VectorViewIterator::operator-> Operator](#operator-arrow)|Načte adresu elementu, který odkazuje aktuální VectorViewIterator.|
|[VectorViewIterator::operator>= Operator](#operator-greater-than-or-equals)|Určuje, zda aktuální VectorViewIterator je větší než nebo rovna hodnotě zadané VectorViewIterator.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`VectorViewIterator`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections –

## <a name="operator-arrow"></a>  VectorViewIterator::operator -&gt; – operátor

Načte adresu elementu, který odkazuje aktuální VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota elementu, který se odkazuje aktuální VectorViewIterator.

Typ vrácené hodnoty je neurčená vnitřní typ, který se vyžaduje k provedení tohoto operátoru.

## <a name="operator-decrement"></a>  VectorViewIterator::operator--– operátor

Sníží aktuální VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

První syntaxe sníží a poté vrátí aktuální VectorViewIterator. Druhá syntaxe vrátí kopii aktuální VectorViewIterator a sníží aktuální VectorViewIterator.

### <a name="remarks"></a>Poznámky

První syntaxe VectorViewIterator předem decrements aktuální VectorViewIterator.

Druhá syntaxe po decrements aktuální VectorViewIterator. `int` v druhé syntaxi označuje operaci po snížení, není skutečný celočíselný operand.

## <a name="operator-dereference"></a>  VectorViewIterator::operator\* – operátor

Získá odkaz na prvek určeném aktuálním VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Element určeném aktuálním VectorViewIterator.

## <a name="operator-equality"></a>  VectorViewIterator::operator == – operátor

Určuje, zda aktuální VectorViewIterator rovná zadané VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud aktuální `VectorViewIterator` rovná *jiných*; v opačném případě **false**.

## <a name="operator-greater-than"></a>  VectorViewIterator::operator&gt; – operátor

Označuje, zda je aktuální VectorViewIterator větší než zadaný VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je větší než aktuální VectorViewIterator *jiných*; v opačném případě **false**.

## <a name="operator-greater-than-or-equals"></a>  VectorViewIterator::operator&gt;= – operátor

Určuje, zda aktuální `VectorViewIterator` je větší než nebo rovna hodnotě zadané `VectorViewIterator`.

### <a name="syntax"></a>Syntaxe

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud aktuální `VectorViewIterator` je větší než nebo rovna hodnotě *jiných*; v opačném případě **false**.

## <a name="operator-increment"></a>  VectorViewIterator::operator ++ – operátor

Aktuální VectorViewIterator zvýší.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První syntaxe zvýší hodnotu a vrátí aktuální VectorViewIterator. Druhá syntaxe vrátí kopii objektu aktuální VectorViewIterator a potom zvýší aktuální VectorViewIterator.

### <a name="remarks"></a>Poznámky

První syntaxe VectorViewIterator předem zvýší aktuální VectorViewIterator.

Druhá syntaxe po zvýší aktuální VectorViewIterator. `int` v druhé syntaxi označuje operaci po přírůstku není skutečný celočíselný operand.

## <a name="operator-inequality"></a>  VectorViewIterator::operator! = – operátor

Určuje, zda aktuální VectorViewIterator není roven zadané VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

**true** Pokud aktuální `VectorViewIterator` není roven *jiných*; v opačném případě **false**.

## <a name="operator-less-than"></a>  VectorViewIterator::operator&lt; – operátor

Označuje, zda aktuální VectorIterator je nižší než zadané VectorIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné `VectorIterator`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud aktuální `VectorIterator` je menší než *jiných*; v opačném případě **false**.

## <a name="operator-less-than-or-equals"></a>  VectorViewIterator::operator&lt;= – operátor

Určuje, zda aktuální `VectorIterator` je menší než nebo rovna zadané `VectorIterator`.

### <a name="syntax"></a>Syntaxe

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné `VectorIterator`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud aktuální `VectorIterator` je menší než nebo rovna hodnotě *jiných*; v opačném případě **false**.

## <a name="operator-minus"></a>  VectorViewIterator::operator-– operátor

Odečte buď zadaný počet prvků z aktuální iterace, což má za následek nové iterátor nebo iterátor zadané z aktuální iterace, což má za následek počet prvků mezi iterátory.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*n*<br/>
Počet prvků.

*Ostatní*<br/>
Jiné VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

Syntaxe první operátor vrací objekt VectorViewIterator, který je `n` prvky menší než aktuální VectorViewIterator. Syntaxe druhý operátor vrátí počet prvků mezi aktuálním a `other` VectorViewIterator.

## <a name="operator-plus-equals"></a>  VectorViewIterator::operator += – operátor

Zvětší aktuální VectorViewIterator podle zadaného posunu.

### <a name="syntax"></a>Syntaxe

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parametry

*n*<br/>
Posunutí celé číslo.

### <a name="return-value"></a>Návratová hodnota

Aktualizované VectorViewIterator.

## <a name="operator-plus"></a>  VectorViewIterator::operator + – operátor

Vrátí VectorViewIterator, odkazující na prvek na zadané posunutí ze zadaného VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator operator+(difference_type n) const;

template <typename T>
inline VectorViewIterator<T> operator+
   (ptrdiff_t n,
   const VectorViewIterator<T>& i);
```

### <a name="parameters"></a>Parametry

*T*<br/>
V druhém syntaxi typename VectorViewIterator.

*n*<br/>
Posunutí celé číslo.

*i*<br/>
V druhém syntaxi VectorViewIterator.

### <a name="return-value"></a>Návratová hodnota

V první syntaxe VectorViewIterator, který odkazuje na element na zadaný posun z aktuální VectorViewIterator.

V druhém syntaxi VectorViewIterator, který odkazuje na element na zadaný posun od začátku parametru `i`.

## <a name="operator-minus-assign"></a>  VectorViewIterator::operator-= Operator

Sníží aktuální VectorIterator podle zadaného posunu.

### <a name="syntax"></a>Syntaxe

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parametry

*n*<br/>
Posunutí celé číslo.

### <a name="return-value"></a>Návratová hodnota

Aktualizované VectorIterator.

## <a name="operator-at"></a>  VectorViewIterator::operator\[\]

Získá odkaz na prvek, který je zadaný posun z aktuální VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parametry

*n*<br/>
Posunutí celé číslo.

### <a name="return-value"></a>Návratová hodnota

Prvek, který je posunout o `n` prvky z aktuální VectorViewIterator.

## <a name="ctor"></a>  VectorViewIterator::VectorViewIterator konstruktor

Inicializuje novou instanci třídy VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>Parametry

*v*<br/>
IVectorView\<T > objektu.

### <a name="remarks"></a>Poznámky

První příklad syntaxe je výchozí konstruktor. Druhý příklad syntaxe je explicitní konstruktor, který se používá ke konstrukci VectorViewIterator ze IVectorView\<T > objektu.

## <a name="see-also"></a>Viz také:

[Platforma Namespace](platform-namespace-c-cx.md)
