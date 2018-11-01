---
title: 'Platform::Collections:: vectoriterator – třída'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: 8e776e0f5d479ee8633efa647ac41e6b1b5f9c0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595595"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections:: vectoriterator – třída

Pro objekty, které jsou odvozeny z rozhraní Windows Runtime IVector poskytuje iterátor standardní knihovny šablon.

VectorIterator je proxy iterátor, který ukládá prvky typu VectorProxy\<T >. Objekt proxy je však téměř nikdy viditelné pro uživatelský kód. Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class VectorIterator;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vlastnost typename třídy VectorIterator šablony.

### <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`difference_type`|Rozdíl ukazatelů (ptrdiff_t).|
|`iterator_category`|Kategorie iterátor náhodného přístupu (:: std::random_access_iterator_tag).|
|`pointer`|Ukazatel na vnitřní typ Platform::Collections::Details::VectorProxy\<T >, která je požadované pro provádění VectorIterator.|
|`reference`|Odkaz na vnitřní typ Platform::Collections::Details::VectorProxy\<T >,,, který je požadované pro provádění VectorIterator.|
|`value_type`|`T` Typename.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[VectorIterator::VectorIterator](#ctor)|Inicializuje novou instanci třídy VectorIterator.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[VectorIterator::operator-– operátor](#operator-minus)|Odečte buď zadaný počet prvků z aktuální iterace, což má za následek nové iterátor nebo iterátor zadané z aktuální iterace, což má za následek počet prvků mezi iterátory.|
|[VectorIterator::operator--– operátor](#operator-decrement)|Sníží aktuální VectorIterator.|
|[VectorIterator::operator! = – operátor](#operator-inequality)|Určuje, zda aktuální VectorIterator není roven zadané VectorIterator.|
|[VectorIterator::operator * – operátor](#operator-dereference)|Získá odkaz na prvek určeném aktuálním VectorIterator.|
|[VectorIterator::operator\[\]](#operator-at)|Získá odkaz na prvek, který je zadaný posun z aktuální VectorIterator.|
|[VectorIterator::operator + – operátor](#operator-plus)|Vrátí VectorIterator, odkazující na prvek na zadané posunutí ze zadaného VectorIterator.|
|[VectorIterator::operator ++ – operátor](#operator-increment)|Aktuální VectorIterator zvýší.|
|[VectorIterator::operator += – operátor](#operator-plus-assign)|Zvětší aktuální VectorIterator podle zadaného posunu.|
|[VectorIterator::operator < – operátor](#operator-less-than)|Označuje, zda aktuální VectorIterator je nižší než zadané VectorIterator.|
|[VectorIterator::operator\<= – operátor](#operator-less-than-or-equals)|Označuje, zda aktuální VectorIterator je menší než nebo rovna hodnotě zadané VectorIterator.|
|[VectorIterator::operator-= – operátor](#operator-subtract-assign)|Sníží aktuální VectorIterator podle zadaného posunu.|
|[VectorIterator::operator == – operátor](#operator-equality)|Určuje, zda aktuální VectorIterator rovná zadané VectorIterator.|
|[VectorIterator::operator > – operátor](#operator-greater-than)|Označuje, zda je aktuální VectorIterator větší než zadaný VectorIterator.|
|[VectorIterator::operator -> – operátor](#operator-arrow)|Načte adresu elementu, který odkazuje aktuální VectorIterator.|
|[VectorIterator::operator > = – operátor](#operator-greater-than-or-equal)|Určuje, zda aktuální VectorIterator je větší než nebo rovna hodnotě zadané VectorIterator.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`VectorIterator`

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Platform::Collections –

## <a name="operator-arrow"></a>  VectorIterator::operator -&gt; – operátor

Načte adresu elementu, který odkazuje aktuální VectorIterator.

### <a name="syntax"></a>Syntaxe

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota elementu, který se odkazuje aktuální VectorIterator.

Typ vrácené hodnoty je neurčená vnitřní typ, který se vyžaduje k provedení tohoto operátoru.

## <a name="operator-decrement"></a>  VectorIterator::operator--– operátor

Sníží aktuální VectorIterator.

### <a name="syntax"></a>Syntaxe

```

VectorIterator& operator--();
VectorIterator operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

První syntaxe sníží a poté vrátí aktuální VectorIterator. Druhá syntaxe vrátí kopii aktuální VectorIterator a sníží aktuální VectorIterator.

### <a name="remarks"></a>Poznámky

První syntaxe VectorIterator předem decrements aktuální VectorIterator.

Druhá syntaxe po decrements aktuální VectorIterator. `int` v druhé syntaxi označuje operaci po snížení, není skutečný celočíselný operand.

## <a name="operator-dereference"></a>  VectorIterator::operator\* – operátor

Načte adresu určeném aktuálním VectorIterator elementu.

### <a name="syntax"></a>Syntaxe

```
reference operator*() const;
```

### <a name="return-value"></a>Návratová hodnota

Element určeném aktuálním VectorIterator.

## <a name="operator-equality"></a>  VectorIterator::operator == – operátor

Určuje, zda aktuální VectorIterator rovná zadané VectorIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud rovná aktuální VectorIterator *jiných*; v opačném případě **false**.

## <a name="operator-greater-than"></a>  VectorIterator::operator&gt; – operátor

Označuje, zda je aktuální VectorIterator větší než zadaný VectorIterator.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je větší než aktuální VectorIterator *jiných*; v opačném případě **false**.

## <a name="operator-greater-than-or-equals"></a>  VectorIterator::operator&gt;= – operátor

Určuje, zda aktuální VectorIterator je větší než nebo rovna hodnotě zadané VectorIterator.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud aktuální VectorIterator je větší než nebo rovna hodnotě *jiných*; v opačném případě **false**.

## <a name="operator-increment"></a>  VectorIterator::operator ++ – operátor

Aktuální VectorIterator zvýší.

### <a name="syntax"></a>Syntaxe

```
VectorIterator& operator++();
VectorIterator operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První syntaxe zvýší hodnotu a vrátí aktuální VectorIterator. Druhá syntaxe vrátí kopii objektu aktuální VectorIterator a potom zvýší aktuální VectorIterator.

### <a name="remarks"></a>Poznámky

První syntaxe VectorIterator předem zvýší aktuální VectorIterator.

Druhá syntaxe po zvýší aktuální VectorIterator. `int` v druhé syntaxi označuje operaci po přírůstku není skutečný celočíselný operand.

## <a name="operator-inequality"></a>  VectorIterator::operator! = – operátor

Určuje, zda aktuální VectorIterator není roven zadané VectorIterator.

### <a name="syntax"></a>Syntaxe

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**true** Pokud aktuální VectorIterator není roven *jiných*; v opačném případě **false**.

## <a name="operator-less-than"></a>  VectorIterator::operator&lt; – operátor

Označuje, zda aktuální VectorIterator je nižší než zadané VectorIterator.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**true** Pokud aktuální VectorIterator je menší než *jiných*; v opačném případě **false**.

## <a name="operator-less-than-or-equals"></a>  VectorIterator::operator&lt;= – operátor

Označuje, zda aktuální VectorIterator je menší než nebo rovna hodnotě zadané VectorIterator.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Jiné VectorIterator.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud aktuální VectorIterator je menší než nebo rovna *jiných*; v opačném případě **false**.

## <a name="operator-minus"></a>  VectorIterator::operator-– operátor

Odečte buď zadaný počet prvků z aktuální iterace, což má za následek nové iterátor nebo iterátor zadané z aktuální iterace, což má za následek počet prvků mezi iterátory.

### <a name="syntax"></a>Syntaxe

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*n*<br/>
Počet prvků.

*Ostatní*<br/>
Jiné VectorIterator.

### <a name="return-value"></a>Návratová hodnota

Syntaxe první operátor vrací objekt VectorIterator, který je `n` prvky menší než aktuální VectorIterator. Syntaxe druhý operátor vrátí počet prvků mezi aktuálním a `other` VectorIterator.

## <a name="operator-plus-assign"></a>  VectorIterator::operator += – operátor

Zvětší aktuální VectorIterator podle zadaného posunu.

### <a name="syntax"></a>Syntaxe

```
VectorIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parametry

*n*<br/>
Posunutí celé číslo.

### <a name="return-value"></a>Návratová hodnota

Aktualizované VectorIterator.

## <a name="operator-plus"></a>  VectorIterator::operator + – operátor

Vrátí VectorIterator, odkazující na prvek na zadané posunutí ze zadaného VectorIterator.

### <a name="syntax"></a>Syntaxe

```

VectorIterator operator+(difference_type n);

template <typename T>
inline VectorIterator<T> operator+(
  ptrdiff_t n,
  const VectorIterator<T>& i);
```

### <a name="parameters"></a>Parametry

*T*<br/>
V druhém syntaxi typename VectorIterator.

*n*<br/>
Posunutí celé číslo.

*i*<br/>
V druhém syntaxi VectorIterator.

### <a name="return-value"></a>Návratová hodnota

V první syntaxe VectorIterator, který odkazuje na element na zadaný posun z aktuální VectorIterator.

V druhém syntaxi VectorIterator, který odkazuje na element na zadaný posun od začátku parametru `i`.

### <a name="remarks"></a>Poznámky

První příklad syntaxe

## <a name="operator-minus-equals"></a>  VectorIterator::operator-= – operátor

Sníží aktuální VectorIterator podle zadaného posunu.

### <a name="syntax"></a>Syntaxe

```
VectorIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parametry

*n*<br/>
Posunutí celé číslo.

### <a name="return-value"></a>Návratová hodnota

Aktualizované VectorIterator.

## <a name="operator-at"></a>  VectorIterator::operator\[\]

Získá odkaz na prvek, který je zadaný posun z aktuální VectorIterator.

### <a name="syntax"></a>Syntaxe

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parametry

*n*<br/>
Posunutí celé číslo.

### <a name="return-value"></a>Návratová hodnota

Prvek, který je posunout o `n` prvky z aktuální VectorIterator.

## <a name="ctor"></a>  VectorIterator::VectorIterator konstruktor

Inicializuje novou instanci třídy VectorIterator.

### <a name="syntax"></a>Syntaxe

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>Parametry

*v*<br/>
IVector\<T > objektu.

### <a name="remarks"></a>Poznámky

První příklad syntaxe je výchozí konstruktor. Druhý příklad syntaxe je explicitní konstruktor, který se používá ke konstrukci VectorIterator ze IVector\<T > objektu.

## <a name="see-also"></a>Viz také

[Platforma Namespace](platform-namespace-c-cx.md)
