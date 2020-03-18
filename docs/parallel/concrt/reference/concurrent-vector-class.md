---
title: concurrent_vector – třída
ms.date: 11/04/2016
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
ms.openlocfilehash: 002f1e3f691de3315810efed8f7d8f6c547cf653
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417248"
---
# <a name="concurrent_vector-class"></a>concurrent_vector – třída

Třída `concurrent_vector` je třída kontejneru sekvence, která umožňuje náhodný přístup k jakémukoli prvku. Umožňuje připojení k bezpečné souběžné souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru. V případě bezpečného zpracování v souběžnosti znamená, že ukazatele nebo iterátory jsou vždy platné. Není zárukou pro inicializaci elementu nebo z konkrétního pořadí procházení.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ prvků, které mají být uloženy ve vektoru.

*_Ax*<br/>
Typ, který představuje uložený objekt přidělování, který zapouzdřuje informace o přidělování a navracení paměti pro souběžný vektor. Tento argument je nepovinný a výchozí hodnota je `allocator<T>`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`allocator_type`|Typ, který představuje třídu přidělování pro souběžný vektor.|
|`const_iterator`|Typ, který poskytuje iterátor náhodného přístupu, který může číst `const` element v souběžném vektoru.|
|`const_pointer`|Typ, který poskytuje ukazatel na prvek `const` v souběžném vektoru.|
|`const_reference`|Typ, který poskytuje odkaz na prvek `const` uložený v souběžném vektoru pro čtení a provádění `const`ch operací.|
|`const_reverse_iterator`|Typ, který poskytuje iterátor náhodného přístupu, který může číst jakýkoli `const` element v souběžném vektoru.|
|`difference_type`|Typ, který poskytuje podepsanou vzdálenost mezi dvěma prvky v souběžném vektoru.|
|`iterator`|Typ, který poskytuje iterátor náhodného přístupu, který může číst libovolný prvek v souběžném vektoru. Úprava prvku pomocí iterátoru není bezpečná pro souběžnost.|
|`pointer`|Typ, který poskytuje ukazatel na prvek v souběžném vektoru.|
|`reference`|Typ, který poskytuje odkaz na prvek uložený v souběžném vektoru.|
|`reverse_iterator`|Typ, který poskytuje iterátor náhodného přístupu, který může číst libovolný prvek v obráceném souběžném vektoru. Úprava prvku pomocí iterátoru není bezpečná pro souběžnost.|
|`size_type`|Typ, který počítá počet prvků v souběžném vektoru.|
|`value_type`|Typ, který představuje datový typ uložený v souběžném vektoru.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[concurrent_vector](#ctor)|Přetíženo. Sestaví souběžný vektor.|
|[~ concurrent_vector destruktor](#dtor)|Smaže všechny prvky a zničí tento souběžný vektor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[řadit](#assign)|Přetíženo. Vymaže prvky souběžného vektoru a přiřadí ho buď `_N` kopie `_Item`nebo hodnoty zadané pomocí rozsahu iterátoru [`_Begin`, `_End`). Tato metoda není bezpečná pro souběžnost.|
|[Počínaje](#at)|Přetíženo. Poskytuje přístup k prvku na daném indexu v souběžném vektoru. Tato metoda je bezpečná pro operace čtení a také při rostoucím vektoru, pokud jste zajistili, že hodnota `_Index` je menší než velikost souběžného vektoru.|
|[návrat](#back)|Přetíženo. Vrátí odkaz nebo `const` odkaz na poslední prvek v souběžném vektoru. Pokud je souběžný vektor prázdný, návratová hodnota není definována. Tato metoda je bezpečná pro souběžnost.|
|[ifunctiondiscovery](#begin)|Přetíženo. Vrátí iterátor typu `iterator` nebo `const_iterator` na začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[klíčivost](#capacity)|Vrátí maximální velikost, na kterou může souběžný vektor růst, aniž by bylo nutné přidělit více paměti. Tato metoda je bezpečná pro souběžnost.|
|[cbegin](#cbegin)|Vrátí iterátor typu `const_iterator` na začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[cend](#cend)|Vrátí iterátor typu `const_iterator` na konec souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[jejich](#clear)|Vymaže všechny prvky v souběžném vektoru. Tato metoda není bezpečná pro souběžnost.|
|[crbegin –](#crbegin)|Vrátí iterátor typu `const_reverse_iterator` na začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[crend](#crend)|Vrátí iterátor typu `const_reverse_iterator` na konec souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[obsahovat](#empty)|Testuje, zda je souběžný vektor prázdný v době volání této metody. Tato metoda je bezpečná pro souběžnost.|
|[účelu](#end)|Přetíženo. Vrátí iterátor typu `iterator` nebo `const_iterator` na konec souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[dopředu](#front)|Přetíženo. Vrátí odkaz nebo `const` odkaz na první prvek v souběžném vektoru. Pokud je souběžný vektor prázdný, návratová hodnota není definována. Tato metoda je bezpečná pro souběžnost.|
|[get_allocator](#get_allocator)|Vrátí kopii přidělujícího modulu, který slouží k vytvoření souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[grow_by](#grow_by)|Přetíženo. Rozroste tento souběžný vektor pomocí `_Delta` prvků. Tato metoda je bezpečná pro souběžnost.|
|[grow_to_at_least](#grow_to_at_least)|Rozroste tento souběžný vektor, dokud neobsahuje alespoň `_N` prvky. Tato metoda je bezpečná pro souběžnost.|
|[max_size](#max_size)|Vrátí maximální počet prvků, které může souběžný vektor uchovávat. Tato metoda je bezpečná pro souběžnost.|
|[push_back](#push_back)|Přetíženo. Připojí danou položku ke konci souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[rbegin](#rbegin)|Přetíženo. Vrátí iterátor typu `reverse_iterator` nebo `const_reverse_iterator` na začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[rend](#rend)|Přetíženo. Vrátí iterátor typu `reverse_iterator` nebo `const_reverse_iterator` na konec souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[rezervační](#reserve)|Přidělí dostatek místa pro zvětšení souběžného vektoru na velikost `_N` bez nutnosti přidělit více paměti později. Tato metoda není bezpečná pro souběžnost.|
|[velikost](#resize)|Přetíženo. Změní velikost souběžného vektoru na požadovanou velikost, odstraní nebo přidá prvky podle potřeby. Tato metoda není bezpečná pro souběžnost.|
|[shrink_to_fit](#shrink_to_fit)|Zkomprimuje interní reprezentace souběžného vektoru, aby se snížila fragmentace a optimalizoval využití paměti. Tato metoda není bezpečná pro souběžnost.|
|[hodnota](#size)|Vrátí počet prvků v souběžném vektoru. Tato metoda je bezpečná pro souběžnost.|
|[adresu](#swap)|Zamění obsah dvou souběžných vektorů. Tato metoda není bezpečná pro souběžnost.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor\[\]](#operator_at)|Přetíženo. Poskytuje přístup k prvku na daném indexu v souběžném vektoru. Tato metoda je bezpečná pro operace čtení a také při rostoucím vektoru, pokud jste zajistili, že hodnota `_Index` je menší než velikost souběžného vektoru.|
|[operátor =](#operator_eq)|Přetíženo. Přiřadí obsah jiného objektu `concurrent_vector` k tomuto. Tato metoda není bezpečná pro souběžnost.|

## <a name="remarks"></a>Poznámky

Podrobné informace o třídě `concurrent_vector` naleznete v tématu [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concurrent_vector. h

**Obor názvů:** souběžnost

## <a name="assign"></a>řadit

Vymaže prvky souběžného vektoru a přiřadí ho buď `_N` kopie `_Item`nebo hodnoty zadané pomocí rozsahu iterátoru [`_Begin`, `_End`). Tato metoda není bezpečná pro souběžnost.

```cpp
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Parametry

*_InputIterator*<br/>
Typ zadaného iterátoru.

*_N*<br/>
Počet položek, které mají být zkopírovány do souběžného vektoru.

*_Item*<br/>
Odkaz na hodnotu použitou k vyplnění souběžného vektoru.

*_Begin*<br/>
Iterátor na první prvek zdrojového rozsahu.

*_End*<br/>
Iterátor k jednomu za posledním prvkem zdrojového rozsahu.

### <a name="remarks"></a>Poznámky

`assign` není bezpečná pro souběžnost. Je nutné zajistit, aby žádná jiná vlákna nevolala metody pro souběžný vektor při volání této metody.

## <a name="at"></a>Počínaje

Poskytuje přístup k prvku na daném indexu v souběžném vektoru. Tato metoda je bezpečná pro operace čtení a také při rostoucím vektoru, pokud jste zajistili, že hodnota `_Index` je menší než velikost souběžného vektoru.

```cpp
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index elementu, který má být načten.

### <a name="return-value"></a>Návratová hodnota

Odkaz na položku v daném indexu.

### <a name="remarks"></a>Poznámky

Verze funkce `at`, která vrací odkaz bez `const` nelze použít k souběžnému zápisu do elementu z různých vláken. K synchronizaci souběžných operací čtení a zápisu do stejného datového elementu by se měl použít jiný objekt synchronizace.

Metoda vyvolá `out_of_range`, pokud `_Index` je větší než nebo rovno velikosti souběžného vektoru a `range_error`, pokud je index pro poškozenou část vektoru. Podrobnosti o tom, jak se vektor může rozdělit, najdete v tématu [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="back"></a>návrat

Vrátí odkaz nebo `const` odkaz na poslední prvek v souběžném vektoru. Pokud je souběžný vektor prázdný, návratová hodnota není definována. Tato metoda je bezpečná pro souběžnost.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz nebo `const` odkaz na poslední prvek v souběžném vektoru.

## <a name="begin"></a>ifunctiondiscovery

Vrátí iterátor typu `iterator` nebo `const_iterator` na začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```cpp
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `iterator` nebo `const_iterator` na začátek souběžného vektoru.

## <a name="capacity"></a>klíčivost

Vrátí maximální velikost, na kterou může souběžný vektor růst, aniž by bylo nutné přidělit více paměti. Tato metoda je bezpečná pro souběžnost.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální velikost, na kterou může souběžný vektor růst, aniž by bylo nutné přidělit více paměti.

### <a name="remarks"></a>Poznámky

Na rozdíl od C++ standardní knihovny `vector`, objekt `concurrent_vector` nepřesouvá existující prvky, pokud přiděluje více paměti.

## <a name="cbegin"></a>cbegin

Vrátí iterátor typu `const_iterator` na začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `const_iterator` na začátek souběžného vektoru.

## <a name="cend"></a>cend

Vrátí iterátor typu `const_iterator` na konec souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `const_iterator` na konec souběžného vektoru.

## <a name="clear"></a>jejich

Vymaže všechny prvky v souběžném vektoru. Tato metoda není bezpečná pro souběžnost.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

`clear` není bezpečná pro souběžnost. Je nutné zajistit, aby žádná jiná vlákna nevolala metody pro souběžný vektor při volání této metody. `clear` neuvolňují interní pole. Chcete-li uvolnit interní pole, zavolejte funkci `shrink_to_fit` po `clear`.

## <a name="ctor"></a>concurrent_vector

Sestaví souběžný vektor.

```cpp
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```

### <a name="parameters"></a>Parametry

*M*<br/>
Typ přidělování zdrojového vektoru.

*_InputIterator*<br/>
Typ vstupního iterátoru.

*_Al*<br/>
Třída alokátoru, která se má použít s tímto objektem.

*_Vector*<br/>
Zdrojový objekt `concurrent_vector`, ze kterého se mají kopírovat nebo přesunout prvky.

*_N*<br/>
Počáteční kapacita objektu `concurrent_vector`.

*_Item*<br/>
Hodnota prvků v konstruovaném objektu.

*_Begin*<br/>
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*_End*<br/>
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt přidělování `_Al` a inicializují vektor.

První konstruktor určí prázdný počáteční vektor a explicitně určí typ přidělování. bude použit.

Druhý a třetí konstruktor určí kopii souběžného vektorového `_Vector`.

Čtvrtý konstruktor určuje přesun souběžného vektorového `_Vector`.

Pátý konstruktor určuje opakování zadaného počtu (`_N`) prvků výchozí hodnoty pro třídu `T`.

Šestý konstruktor určuje opakování (`_N`) prvků Value `_Item`.

Poslední konstruktor určuje hodnoty poskytované rozsahem iterátoru [`_Begin`, `_End`).

## <a name="dtor"></a>~ concurrent_vector

Smaže všechny prvky a zničí tento souběžný vektor.

```cpp
~concurrent_vector();
```

## <a name="crbegin"></a>crbegin –

Vrátí iterátor typu `const_reverse_iterator` na začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `const_reverse_iterator` na začátek souběžného vektoru.

## <a name="crend"></a>crend

Vrátí iterátor typu `const_reverse_iterator` na konec souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `const_reverse_iterator` na konec souběžného vektoru.

## <a name="empty"></a>obsahovat

Testuje, zda je souběžný vektor prázdný v době volání této metody. Tato metoda je bezpečná pro souběžnost.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byl vektor prázdný v okamžiku, kdy byla funkce volána, jinak **false** .

## <a name="end"></a>účelu

Vrátí iterátor typu `iterator` nebo `const_iterator` na konec souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `iterator` nebo `const_iterator` na konec souběžného vektoru.

## <a name="front"></a>dopředu

Vrátí odkaz nebo `const` odkaz na první prvek v souběžném vektoru. Pokud je souběžný vektor prázdný, návratová hodnota není definována. Tato metoda je bezpečná pro souběžnost.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz nebo `const` odkaz na první prvek v souběžném vektoru.

## <a name="get_allocator"></a>get_allocator

Vrátí kopii přidělujícího modulu, který slouží k vytvoření souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Kopie přidělování, která se používá k vytvoření objektu `concurrent_vector`.

## <a name="grow_by"></a>grow_by

Rozroste tento souběžný vektor pomocí `_Delta` prvků. Tato metoda je bezpečná pro souběžnost.

```cpp
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>Parametry

*_Delta*<br/>
Počet prvků, které se mají připojit k objektu.

*_Item*<br/>
Hodnota pro inicializaci nových elementů.

### <a name="return-value"></a>Návratová hodnota

Iterátor na první položku, která je připojena.

### <a name="remarks"></a>Poznámky

Pokud není zadán `_Item`, jsou nové prvky vytvořeny jako výchozí.

## <a name="grow_to_at_least"></a>grow_to_at_least

Rozroste tento souběžný vektor, dokud neobsahuje alespoň `_N` prvky. Tato metoda je bezpečná pro souběžnost.

```cpp
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Nová minimální velikost objektu `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na začátek připojené sekvence nebo na element na indexu `_N`, pokud nebyly připojeny žádné prvky.

## <a name="max_size"></a>max_size

Vrátí maximální počet prvků, které může souběžný vektor uchovávat. Tato metoda je bezpečná pro souběžnost.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet prvků, které může objekt `concurrent_vector` uchovávat.

## <a name="operator_eq"></a>operátor =

Přiřadí obsah jiného objektu `concurrent_vector` k tomuto. Tato metoda není bezpečná pro souběžnost.

```cpp
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```

### <a name="parameters"></a>Parametry

*M*<br/>
Typ přidělování zdrojového vektoru.

*_Vector*<br/>
Zdrojový objekt `concurrent_vector`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `concurrent_vector`.

## <a name="operator_at"></a>operator [] – operátor

Poskytuje přístup k prvku na daném indexu v souběžném vektoru. Tato metoda je bezpečná pro operace čtení a také při rostoucím vektoru, pokud jste zajistili, že hodnota `_Index` je menší než velikost souběžného vektoru.

```cpp
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index elementu, který má být načten.

### <a name="return-value"></a>Návratová hodnota

Odkaz na položku v daném indexu.

### <a name="remarks"></a>Poznámky

Verze `operator []`, která vrací odkaz bez `const` nelze použít k souběžnému zápisu do elementu z různých vláken. K synchronizaci souběžných operací čtení a zápisu do stejného datového elementu by se měl použít jiný objekt synchronizace.

Neprovádí se žádná kontrola mezí, aby se zajistilo, že `_Index` je platným indexem souběžného vektoru.

## <a name="push_back"></a>push_back

Připojí danou položku ke konci souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```cpp
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>Parametry

*_Item*<br/>
Hodnota, která má být připojena.

### <a name="return-value"></a>Návratová hodnota

Iterátor na položku, která je připojena.

## <a name="rbegin"></a>rbegin

Vrátí iterátor typu `reverse_iterator` nebo `const_reverse_iterator` na začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```cpp
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `reverse_iterator` nebo `const_reverse_iterator` na začátek souběžného vektoru.

## <a name="rend"></a>rend

Vrátí iterátor typu `reverse_iterator` nebo `const_reverse_iterator` na konec souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```cpp
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `reverse_iterator` nebo `const_reverse_iterator` na konec souběžného vektoru.

## <a name="reserve"></a>rezervační

Přidělí dostatek místa pro zvětšení souběžného vektoru na velikost `_N` bez nutnosti přidělit více paměti později. Tato metoda není bezpečná pro souběžnost.

```cpp
void reserve(size_type _N);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Počet prvků, pro které má být vyhrazen prostor.

### <a name="remarks"></a>Poznámky

`reserve` není bezpečná pro souběžnost. Je nutné zajistit, aby žádná jiná vlákna nevolala metody pro souběžný vektor při volání této metody. Kapacita souběžného vektoru po vrácení metody může být větší než požadovaná rezervace.

## <a name="resize"></a>velikost

Změní velikost souběžného vektoru na požadovanou velikost, odstraní nebo přidá prvky podle potřeby. Tato metoda není bezpečná pro souběžnost.

```cpp
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Nová velikost concurrent_vector.

*počítává*<br/>
Hodnota nových prvků přidaných do vektoru, pokud je nová velikost větší než původní velikost. Pokud je hodnota vynechána, přiřadí se nové objekty výchozí hodnota pro svůj typ.

### <a name="remarks"></a>Poznámky

Pokud je velikost kontejneru menší než požadovaná velikost, prvky jsou přidány do vektoru, dokud nedosáhne požadované velikosti. Pokud je velikost kontejneru větší než požadovaná velikost, prvky nejbližší ke konci kontejneru jsou odstraněny, dokud kontejner nedosáhne velikosti `_N`. Pokud je současná velikost kontejneru stejná jako požadovaná velikost, není provedena žádná akce.

`resize` není v bezpečí. Je nutné zajistit, aby žádná jiná vlákna nevolala metody pro souběžný vektor při volání této metody.

## <a name="shrink_to_fit"></a>shrink_to_fit

Zkomprimuje interní reprezentace souběžného vektoru, aby se snížila fragmentace a optimalizoval využití paměti. Tato metoda není bezpečná pro souběžnost.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Poznámky

Tato metoda interně znovu přidělí prvky pro přesun paměti, čímž zruší platnost všech iterátorů. `shrink_to_fit` není bezpečná pro souběžnost. Při volání této funkce je nutné zajistit, aby žádná jiná vlákna nevolala metody pro souběžný vektor.

## <a name="size"></a>hodnota

Vrátí počet prvků v souběžném vektoru. Tato metoda je bezpečná pro souběžnost.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v tomto objektu `concurrent_vector`.

### <a name="remarks"></a>Poznámky

Vrácená velikost je zaručena zahrnout všechny prvky, které jsou připojeny voláním funkce `push_back`, nebo rozšířit operace, které byly dokončeny před vyvoláním této metody. Může však také zahrnovat prvky, které jsou přiděleny, ale stále jsou v souladu se sestavou souběžným voláním libovolné metody růstu.

## <a name="swap"></a>adresu

Zamění obsah dvou souběžných vektorů. Tato metoda není bezpečná pro souběžnost.

```cpp
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>Parametry

*_Vector*<br/>
Objekt `concurrent_vector`, pomocí kterého má prohození obsahu.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md)
