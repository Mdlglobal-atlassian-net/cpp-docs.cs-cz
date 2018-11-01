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
ms.openlocfilehash: 367a5ed6bf9d42730a309570c93afd1b315bae25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501748"
---
# <a name="concurrentvector-class"></a>concurrent_vector – třída

`concurrent_vector` Třídy je třída kontejneru sekvence, která umožňuje náhodný přístup k libovolnému prvku. Umožňuje bezpečné na souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru připojit.

## <a name="syntax"></a>Syntaxe

```
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ prvků, které mají být uloženy ve vektoru.

*_Ax*<br/>
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navracení zpět paměti pro souběžný vektor. Tento argument je nepovinný a výchozí hodnota je `allocator<T>`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`allocator_type`|Typ, který představuje třídu alokátoru pro souběžný vektor.|
|`const_iterator`|Typ, který poskytuje iterátor náhodného přístupu, který může přečíst `const` prvek souběžného vektoru.|
|`const_pointer`|Typ, který poskytuje ukazatel `const` prvek souběžného vektoru.|
|`const_reference`|Typ, který poskytuje odkaz na `const` prvek uložený v souběžného vektoru pro čtení a provádění `const` operace.|
|`const_reverse_iterator`|Typ, který poskytuje iterátor náhodného přístupu, který může přečíst jakýkoli `const` prvek souběžného vektoru.|
|`difference_type`|Typ, který poskytuje podepsaný vzdálenosti mezi dvěma prvky v souběžného vektoru.|
|`iterator`|Typ, který poskytuje iterátor náhodného přístupu, který může číst libovolný prvek v souběžného vektoru. Úpravy z elementu s použitím iterátor není bezpečná pro souběžnost.|
|`pointer`|Typ, který poskytuje ukazatel na prvek v souběžného vektoru.|
|`reference`|Typ, který poskytuje odkaz na prvek uložený v souběžného vektoru.|
|`reverse_iterator`|Typ, který poskytuje iterátor náhodného přístupu, který může číst libovolný prvek v obráceném objektu souběžného vektoru. Úpravy z elementu s použitím iterátor není bezpečná pro souběžnost.|
|`size_type`|Typ, který vrátí počet prvků v souběžného vektoru.|
|`value_type`|Typ, který představuje typ dat uložených v souběžného vektoru.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[concurrent_vector –](#ctor)|Přetíženo. Konstrukce souběžného vektoru.|
|[~ concurrent_vector – destruktor](#dtor)|Vymaže všechny prvky a odstraní tento souběžného vektoru.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[přiřazení](#assign)|Přetíženo. Odstraní prvky souběžného vektoru a přiřadí ji buď `_N` kopie `_Item`, nebo hodnoty zadané rozsahem iterátoru [ `_Begin`, `_End`). Tato metoda není bezpečná pro souběžnost.|
|[at](#at)|Přetíženo. Poskytuje přístup k prvku na daném indexu v souběžného vektoru. Tato metoda je bezpečná pro souběžnost pro operace čtení a také při rostoucí vektoru, za předpokladu, zajistíte, hodnota `_Index` je menší než velikost souběžného vektoru.|
|[Zpět](#back)|Přetíženo. Vrátí odkaz nebo `const` odkazovat na poslední prvek v souběžného vektoru. Pokud souběžného vektoru je prázdný, návratová hodnota není definována. Tato metoda je bezpečná pro souběžnost.|
|[začít](#begin)|Přetíženo. Vrátí iterátor typu `iterator` nebo `const_iterator` začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[Kapacita](#capacity)|Vrátí maximální velikost, ke kterému můžou růst souběžného vektoru bez nutnosti přidělení více paměti. Tato metoda je bezpečná pro souběžnost.|
|[cbegin](#cbegin)|Vrátí iterátor typu `const_iterator` začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[cend](#cend)|Vrátí iterátor typu `const_iterator` za účelem souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[Vymazat](#clear)|Vymaže všechny prvky v souběžného vektoru. Tato metoda není bezpečná pro souběžnost.|
|[crbegin](#crbegin)|Vrátí iterátor typu `const_reverse_iterator` začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[crend –](#crend)|Vrátí iterátor typu `const_reverse_iterator` za účelem souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[prázdný](#empty)|Testuje, zda je souběžného vektoru je prázdný v době tato metoda je volána. Tato metoda je bezpečná pro souběžnost.|
|[ukončení](#end)|Přetíženo. Vrátí iterátor typu `iterator` nebo `const_iterator` za účelem souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[Přední](#front)|Přetíženo. Vrátí odkaz nebo `const` odkaz na první prvek v souběžného vektoru. Pokud souběžného vektoru je prázdný, návratová hodnota není definována. Tato metoda je bezpečná pro souběžnost.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu Alokátor použitý k vytvoření souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[grow_by –](#grow_by)|Přetíženo. Roste tento souběžného vektoru pomocí `_Delta` elementy. Tato metoda je bezpečná pro souběžnost.|
|[grow_to_at_least](#grow_to_at_least)|Roste tento souběžného vektoru, dokud je nejméně `_N` elementy. Tato metoda je bezpečná pro souběžnost.|
|[max_size](#max_size)|Vrátí maximální počet prvků, které může obsahovat souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[push_back](#push_back)|Přetíženo. Daná položka se připojí na konec souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[rbegin –](#rbegin)|Přetíženo. Vrátí iterátor typu `reverse_iterator` nebo `const_reverse_iterator` začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[rend –](#rend)|Přetíženo. Vrátí iterátor typu `reverse_iterator` nebo `const_reverse_iterator` za účelem souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[Rezervovat](#reserve)|Přidělí dostatek místa pro souběžného vektoru zvětšení velikosti `_N` bez nutnosti přidělit víc paměti později. Tato metoda není bezpečná pro souběžnost.|
|[Změna velikosti](#resize)|Přetíženo. Změní velikost souběžného vektoru na požadovanou velikost, odstranění nebo přidání prvků podle potřeby. Tato metoda není bezpečná pro souběžnost.|
|[shrink_to_fit](#shrink_to_fit)|Zkomprimuje vnitřní reprezentaci souběžného vektoru snížit fragmentaci a optimalizovat využití paměti. Tato metoda není bezpečná pro souběžnost.|
|[Velikost](#size)|Vrátí počet prvků v souběžného vektoru. Tato metoda je bezpečná pro souběžnost.|
|[Prohození](#swap)|Zamění obsah dvou souběžných vektorů. Tato metoda není bezpečná pro souběžnost.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Operator [].](#operator_at)|Přetíženo. Poskytuje přístup k prvku na daném indexu v souběžného vektoru. Tato metoda je bezpečná pro souběžnost pro operace čtení a také při rostoucí vektoru, za předpokladu, zajistíte, která hodnota `_Index` je menší než velikost souběžného vektoru.|
|[operátor =](#operator_eq)|Přetíženo. Přiřadí obsah jiného `concurrent_vector` do tohoto objektu. Tato metoda není bezpečná pro souběžnost.|

## <a name="remarks"></a>Poznámky

Podrobné informace o `concurrent_vector` najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concurrent_vector.h

**Namespace:** souběžnosti

##  <a name="assign"></a> přiřazení

Odstraní prvky souběžného vektoru a přiřadí ji buď `_N` kopie `_Item`, nebo hodnoty zadané rozsahem iterátoru [ `_Begin`, `_End`). Tato metoda není bezpečná pro souběžnost.

```
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Parametry

*_InputIterator*<br/>
Typ zadaný iterátor.

*_N*<br/>
Počet položek do souběžného vektoru.

*_Položku*<br/>
Odkaz na hodnotu použitou k vyplnění souběžného vektoru.

*_Zahájit*<br/>
Iterátor na první prvek zdrojové oblasti.

*_Ukončit*<br/>
Iterátor na jedno místo za posledním prvkem zdrojové oblasti.

### <a name="remarks"></a>Poznámky

`assign` není bezpečná pro souběžnost. Ujistěte se, že jsou nejsou žádná jiná vlákna po volání této metody vyvolání metody souběžného vektoru.

##  <a name="at"></a> v

Poskytuje přístup k prvku na daném indexu v souběžného vektoru. Tato metoda je bezpečná pro souběžnost pro operace čtení a také při rostoucí vektoru, za předpokladu, zajistíte, hodnota `_Index` je menší než velikost souběžného vektoru.

```
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index prvku, který se má načíst.

### <a name="return-value"></a>Návratová hodnota

Odkaz na položku na daném indexu.

### <a name="remarks"></a>Poznámky

Verze funkce `at` , která vrací non - `const` odkaz nelze použít současně zapisovat do prvku z různých vláken. Objekt různých synchronizace by měla sloužit k synchronizaci souběžných čtení a operací zápisu na stejný datový element.

Metoda vyvolá `out_of_range` Pokud `_Index` je větší než nebo roven velikosti souběžného vektoru a `range_error` Pokud je index poškozený část vektoru. Podrobnosti o tom, jak vektor může být poškozený, naleznete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).

##  <a name="back"></a> Zpět

Vrátí odkaz nebo `const` odkazovat na poslední prvek v souběžného vektoru. Pokud souběžného vektoru je prázdný, návratová hodnota není definována. Tato metoda je bezpečná pro souběžnost.

```
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz nebo `const` odkazovat na poslední prvek v souběžného vektoru.

##  <a name="begin"></a> začít

Vrátí iterátor typu `iterator` nebo `const_iterator` začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `iterator` nebo `const_iterator` začátek souběžného vektoru.

##  <a name="capacity"></a> Kapacita

Vrátí maximální velikost, ke kterému můžou růst souběžného vektoru bez nutnosti přidělení více paměti. Tato metoda je bezpečná pro souběžnost.

```
size_type capacity() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální velikost, ke kterému můžou růst souběžného vektoru bez nutnosti přidělení více paměti.

### <a name="remarks"></a>Poznámky

Na rozdíl od standardní knihovny C++ `vector`, `concurrent_vector` objekt nepřesouvá stávající elementy, pokud se přiděluje víc paměti.

##  <a name="cbegin"></a> cbegin

Vrátí iterátor typu `const_iterator` začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `const_iterator` začátek souběžného vektoru.

##  <a name="cend"></a> cend

Vrátí iterátor typu `const_iterator` za účelem souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `const_iterator` za účelem souběžného vektoru.

##  <a name="clear"></a> Vymazat

Vymaže všechny prvky v souběžného vektoru. Tato metoda není bezpečná pro souběžnost.

```
void clear();
```

### <a name="remarks"></a>Poznámky

`clear` není bezpečná pro souběžnost. Ujistěte se, že jsou nejsou žádná jiná vlákna po volání této metody vyvolání metody souběžného vektoru. `clear` vnitřní pole neuvolní. Chcete-li uvolnit vnitřní pole, zavolejte funkci `shrink_to_fit` po `clear`.

##  <a name="ctor"></a> concurrent_vector –

Konstrukce souběžného vektoru.

```
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
Typ alokátoru zdrojového vektoru.

*_InputIterator*<br/>
Typ vstupního iterátoru.

*_Al*<br/>
Třída alokátoru, která se má použít s tímto objektem.

*_Vector*<br/>
Zdroj `concurrent_vector` objektu, který chcete zkopírovat nebo přesunout elementy ze.

*_N*<br/>
Počáteční kapacita objektu `concurrent_vector` objektu.

*_Položku*<br/>
Hodnota prvků ve vytvořeném objektu.

*_Zahájit*<br/>
Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.

*_Ukončit*<br/>
Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt alokátoru `_Al` a inicializují vektor.

První konstruktor zadejte prázdný počáteční vektor a explicitně určuje typ alokátoru. který se má použít.

Druhý a třetí konstruktor určují kopii souběžného vektoru `_Vector`.

Čtvrtý konstruktor určuje pohyb souběžného vektoru `_Vector`.

Pátý konstruktor určuje opakování zadaného počtu ( `_N`) prvků výchozí hodnoty pro třídu `T`.

Šestý konstruktor určuje opakování ( `_N`) prvků hodnoty `_Item`.

Poslední konstruktor určuje hodnoty poskytnuté rozsahem iterátoru [ `_Begin`, `_End`).

##  <a name="dtor"></a> ~ concurrent_vector –

Vymaže všechny prvky a odstraní tento souběžného vektoru.

```
~concurrent_vector();
```

##  <a name="crbegin"></a> crbegin –

Vrátí iterátor typu `const_reverse_iterator` začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `const_reverse_iterator` začátek souběžného vektoru.

##  <a name="crend"></a> crend –

Vrátí iterátor typu `const_reverse_iterator` za účelem souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `const_reverse_iterator` za účelem souběžného vektoru.

##  <a name="empty"></a> prázdný

Testuje, zda je souběžného vektoru je prázdný v době tato metoda je volána. Tato metoda je bezpečná pro souběžnost.

```
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud v tuto chvíli byla volána funkce, byl prázdný vektor **false** jinak.

##  <a name="end"></a> ukončení

Vrátí iterátor typu `iterator` nebo `const_iterator` za účelem souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `iterator` nebo `const_iterator` za účelem souběžného vektoru.

##  <a name="front"></a> Přední

Vrátí odkaz nebo `const` odkaz na první prvek v souběžného vektoru. Pokud souběžného vektoru je prázdný, návratová hodnota není definována. Tato metoda je bezpečná pro souběžnost.

```
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz nebo `const` odkaz na první prvek v souběžného vektoru.

##  <a name="get_allocator"></a> get_allocator

Vrátí kopii objektu Alokátor použitý k vytvoření souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor použitý k vytvoření kopie `concurrent_vector` objektu.

##  <a name="grow_by"></a> grow_by –

Roste tento souběžného vektoru pomocí `_Delta` elementy. Tato metoda je bezpečná pro souběžnost.

```
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>Parametry

*_Delta*<br/>
Počet prvků, které se připojí k objektu.

*_Položku*<br/>
Hodnota určená k inicializaci nové elementy.

### <a name="return-value"></a>Návratová hodnota

Iterátor na první položku připojí.

### <a name="remarks"></a>Poznámky

Pokud `_Item` nezadáte, nové prvky jsou výchozí vyrobený.

##  <a name="grow_to_at_least"></a> grow_to_at_least –

Roste tento souběžného vektoru, dokud je nejméně `_N` elementy. Tato metoda je bezpečná pro souběžnost.

```
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Nový minimální velikost `concurrent_vector` objektu.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na začátek pořadí připojený, nebo element v indexu `_N` Pokud byly přidány žádné elementy.

##  <a name="max_size"></a> max_size

Vrátí maximální počet prvků, které může obsahovat souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet prvků `concurrent_vector` objekt může obsahovat.

##  <a name="operator_eq"></a> operátor =

Přiřadí obsah jiného `concurrent_vector` do tohoto objektu. Tato metoda není bezpečná pro souběžnost.

```
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
Typ alokátoru zdrojového vektoru.

*_Vector*<br/>
Zdroj `concurrent_vector` objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `concurrent_vector` objektu.

##  <a name="operator_at"></a> Operator [].

Poskytuje přístup k prvku na daném indexu v souběžného vektoru. Tato metoda je bezpečná pro souběžnost pro operace čtení a také při rostoucí vektoru, za předpokladu, zajistíte, která hodnota `_Index` je menší než velikost souběžného vektoru.

```
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index prvku, který se má načíst.

### <a name="return-value"></a>Návratová hodnota

Odkaz na položku na daném indexu.

### <a name="remarks"></a>Poznámky

Verze `operator []` , která vrací non - `const` odkaz nelze použít současně zapisovat do prvku z různých vláken. Objekt různých synchronizace by měla sloužit k synchronizaci souběžných čtení a operací zápisu na stejný datový element.

Žádná kontrola se provádí za účelem zajištění toho, aby hranic `_Index` je platný index do souběžného vektoru.

##  <a name="push_back"></a> push_back

Daná položka se připojí na konec souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>Parametry

*_Položku*<br/>
Hodnota, které se mají připojit.

### <a name="return-value"></a>Návratová hodnota

Iterátor s položkou připojí.

##  <a name="rbegin"></a> rbegin –

Vrátí iterátor typu `reverse_iterator` nebo `const_reverse_iterator` začátek souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `reverse_iterator` nebo `const_reverse_iterator` začátek souběžného vektoru.

##  <a name="rend"></a> rend –

Vrátí iterátor typu `reverse_iterator` nebo `const_reverse_iterator` za účelem souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `reverse_iterator` nebo `const_reverse_iterator` za účelem souběžného vektoru.

##  <a name="reserve"></a> Rezervovat

Přidělí dostatek místa pro souběžného vektoru zvětšení velikosti `_N` bez nutnosti přidělit víc paměti později. Tato metoda není bezpečná pro souběžnost.

```
void reserve(size_type _N);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Počet prvků, které mají rezervovat místa pro.

### <a name="remarks"></a>Poznámky

`reserve` není bezpečná pro souběžnost. Ujistěte se, že jsou nejsou žádná jiná vlákna po volání této metody vyvolání metody souběžného vektoru. Kapacita souběžného vektoru po vrátí metoda může být větší než požadovaný rezervace.

##  <a name="resize"></a> Změna velikosti

Změní velikost souběžného vektoru na požadovanou velikost, odstranění nebo přidání prvků podle potřeby. Tato metoda není bezpečná pro souběžnost.

```
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>Parametry

*_N*<br/>
Nová velikost concurrent_vector –.

*Val*<br/>
Hodnota nové elementy přidané do vektoru, pokud je nová velikost větší než původní velikost. Pokud je hodnota vynechána, nové objekty jsou přiřazeny výchozí hodnotě pro jejich typu.

### <a name="remarks"></a>Poznámky

Pokud je velikost kontejneru menší než požadovaná velikost, prvky jsou přidány do vektoru, dokud nedosáhne požadované velikosti. Pokud velikost kontejneru je větší než požadovaná velikost, prvky nejblíže konci kontejneru jsou odstraněny, dokud nedosáhne velikosti kontejneru `_N`. Pokud je k dispozici velikost kontejneru je stejná jako požadovaná velikost, nedojde k žádné akci.

`resize` není souběžnosti bezpečné. Ujistěte se, že jsou nejsou žádná jiná vlákna po volání této metody vyvolání metody souběžného vektoru.

##  <a name="shrink_to_fit"></a> shrink_to_fit –

Zkomprimuje vnitřní reprezentaci souběžného vektoru snížit fragmentaci a optimalizovat využití paměti. Tato metoda není bezpečná pro souběžnost.

```
void shrink_to_fit();
```

### <a name="remarks"></a>Poznámky

Tato metoda se interně znovu přidělit paměti přesunout elementy, zrušení platnosti všech iterátorů. `shrink_to_fit` není bezpečná pro souběžnost. Ujistěte se, že se žádná vlákna po volání této funkce volání metod na souběžného vektoru.

##  <a name="size"></a> Velikost

Vrátí počet prvků v souběžného vektoru. Tato metoda je bezpečná pro souběžnost.

```
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v tomto `concurrent_vector` objektu.

### <a name="remarks"></a>Poznámky

Je zaručeno, že vrácená velikost zahrnout všechny prvky, které se připojí pomocí volání funkce `push_back`, nebo růst operací, které byly dokončeny před vyvoláním této metody. Ale může také obsahovat elementy, které jsou přiděleny, ale stále vytvářený souběžných volání metod růstu.

##  <a name="swap"></a> Prohození

Zamění obsah dvou souběžných vektorů. Tato metoda není bezpečná pro souběžnost.

```
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>Parametry

*_Vector*<br/>
`concurrent_vector` Objektu k výměně obsahu s.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md)

