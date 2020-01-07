---
title: concurrent_unordered_map – třída
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::at
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
ms.openlocfilehash: a43e52edfe223dae51737d7d2cde37e3b8238f08
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298685"
---
# <a name="concurrent_unordered_map-class"></a>concurrent_unordered_map – třída

Třída `concurrent_unordered_map` je kontejner bezpečné souběžnosti, který řídí proměnlivou délku sekvence prvků typu `std::pair<const K, _Element_type>`. Sekvence je reprezentována způsobem, který umožňuje připojení bezpečné souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru. V případě bezpečného zpracování v souběžnosti znamená, že ukazatele nebo iterátory jsou vždy platné. Není zárukou pro inicializaci elementu nebo z konkrétního pořadí procházení.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_map : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
details::_Hash_compare<K,
    _Hasher,
key_equality>,
    _Allocator_type,
false>>;
```

#### <a name="parameters"></a>Parametry

*K*<br/>
Klíčový typ

*_Element_type*<br/>
Mapovaný typ

*_Hasher*<br/>
Typ objektu hashovací funkce Tento argument je nepovinný a výchozí hodnota je `std::hash<K>`.

*key_equality*<br/>
Typ objektu funkce porovnání rovnosti Tento argument je nepovinný a výchozí hodnota je `std::equal_to<K>`.

*_Allocator_type*<br/>
Typ, který představuje uložený objekt přidělování, který zapouzdřuje informace o přidělování a navracení paměti pro souběžnou neuspořádanou mapu. Tento argument je nepovinný a výchozí hodnota je `std::allocator<std::pair<K`, `_Element_type>>`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|`allocator_type`|Typ alokátoru pro správu úložiště|
|`const_iterator`|Typ konstantního iterátoru řízené sekvence|
|`const_local_iterator`|Typ konstantního iterátoru kbelíku řízené sekvence|
|`const_pointer`|Typ konstantního ukazatele na prvek|
|`const_reference`|Typ konstantního odkazu na prvek|
|`difference_type`|Typ vzdálenosti se znaménkem mezi dvěma prvky|
|`hasher`|Typ hashovací funkce|
|`iterator`|Typ iterátoru řízené sekvence|
|`key_equal`|Typ funkce porovnání|
|`key_type`|Typ klíče řazení|
|`local_iterator`|Typ iterátoru kbelíku řízené sekvence|
|`mapped_type`|Typ mapované hodnoty přiřazené ke každému klíči|
|`pointer`|Typ ukazatele na prvek|
|`reference`|Typ odkazu na prvek|
|`size_type`|Typ vzdálenosti bez znaménka mezi dvěma prvky|
|`value_type`|Typ prvku|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[concurrent_unordered_map](#ctor)|Přetížené Vytvoří souběžnou neuspořádanou mapu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[at](#at)|Přetížené Vyhledá prvek v `concurrent_unordered_map` se zadanou hodnotou klíče.. Tato metoda je bezpečná pro souběžnost.|
|[hash_function](#hash_function)|Získá uložený objekt hashovací funkce.|
|[zadat](#insert)|Přetížené Přidá prvky do objektu `concurrent_unordered_map`.|
|[key_eq](#key_eq)|Získá uložený objekt funkce porovnání rovnosti.|
|[swap](#swap)|Zamění obsah dvou objektů `concurrent_unordered_map`. Tato metoda není bezpečná pro souběžnost.|
|[unsafe_erase](#unsafe_erase)|Přetížené Odebere prvky z `concurrent_unordered_map` na zadané pozici. Tato metoda není bezpečná pro souběžnost.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[operátor\[\]](#operator_at)|Přetížené Vyhledá nebo vloží prvek se zadaným klíčem. Tato metoda je bezpečná pro souběžnost.|
|[operátor =](#operator_eq)|Přetížené Přiřadí obsah jiného objektu `concurrent_unordered_map` k tomuto. Tato metoda není bezpečná pro souběžnost.|

## <a name="remarks"></a>Poznámky

Podrobné informace o třídě `concurrent_unordered_map` naleznete v tématu [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_map`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concurrent_unordered_map. h

**Obor názvů:** souběžnost

##  <a name="at"></a>Počínaje

Vyhledá prvek v `concurrent_unordered_map` se zadanou hodnotou klíče.. Tato metoda je bezpečná pro souběžnost.

```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Hodnota klíče, která se má najít

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu dat nalezeného prvku.

### <a name="remarks"></a>Poznámky

Pokud hodnota klíče argumentu nebyla nalezena, funkce vyvolá objekt třídy `out_of_range`.

##  <a name="begin"></a>ifunctiondiscovery

Vrátí iterátor odkazující na první prvek v souběžném kontejneru. Tato metoda je bezpečná pro souběžnost.

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor na první prvek v souběžném kontejneru.

##  <a name="cbegin"></a>cbegin

Vrátí konstantní iterátor odkazující na první prvek v souběžném kontejneru. Tato metoda je bezpečná pro souběžnost.

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní iterátor na první prvek v souběžném kontejneru.

##  <a name="cend"></a>cend

Vrátí konstantní iterátor ukazující na umístění, které následuje po posledním prvku v souběžném kontejneru. Tato metoda je bezpečná pro souběžnost.

```
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní iterátor na umístění, který následuje po posledním prvku v souběžném kontejneru.

##  <a name="clear"></a>jejich

Smaže všechny prvky v souběžném kontejneru. Tato funkce není bezpečná pro souběžnost.

```
void clear();
```

##  <a name="ctor"></a> concurrent_unordered_map

Vytvoří souběžnou neuspořádanou mapu.

```
explicit concurrent_unordered_map(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_map(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap);

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_map(
    concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>Parametry

*_Iterator*<br/>
Typ vstupního iterátoru.

*_Number_of_buckets*<br/>
Počáteční počet intervalů pro tuto neuspořádanou mapu.

*_Hasher*<br/>
Funkce hash pro tuto neuspořádanou mapu.

*key_equality*<br/>
Funkce porovnání rovnosti pro tuto neuspořádanou mapu.

*_Allocator*<br/>
Alokátor pro tuto neuspořádanou mapu.

*_Begin*<br/>
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*_End*<br/>
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

*_Umap*<br/>
Zdrojový objekt `concurrent_unordered_map`, ze kterého se mají kopírovat nebo přesunout prvky.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt přidělování `_Allocator` a inicializují neuspořádané mapování.

První konstruktor určuje prázdnou počáteční mapu a explicitně určuje počet intervalů, funkcí hash, funkcí rovnosti a typu přidělujícího typu, které se mají použít.

Druhý konstruktor určuje přidělování pro neuspořádanou mapu.

Třetí konstruktor určuje hodnoty poskytované rozsahem iterátoru [`_Begin`, `_End`).

Čtvrtý a pátý konstruktor určuje kopii souběžného neuspořádaného `_Umap`mapy.

Poslední konstruktor určuje přesun souběžné neuspořádané `_Umap`mapy.

##  <a name="count"></a>výpočtu

Spočítá počet prvků, které odpovídají zadanému klíči. Tato funkce je bezpečná pro souběžnost.

```
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Klíč, který chcete vyhledat.

### <a name="return-value"></a>Návratová hodnota

Počet pokusů, kolikrát se klíč zobrazuje v kontejneru.

##  <a name="empty"></a>obsahovat

Zkouší, zda nejsou přítomny žádné prvky. Tato metoda je bezpečná pro souběžnost.

```
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je souběžný kontejner prázdný, jinak **false** .

### <a name="remarks"></a>Poznámky

V případě souběžných vložení, bez ohledu na to, jestli je souběžný kontejner prázdný, se může po volání této funkce změnit hned, než se hodnota návratové hodnoty ještě přečte.

##  <a name="end"></a>účelu

Vrátí iterátor ukazující na umístění, které následuje po posledním prvku v souběžném kontejneru. Tato metoda je bezpečná pro souběžnost.

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor do umístění následující po posledním prvku v souběžném kontejneru.

##  <a name="equal_range"></a>equal_range

Najde rozsah, který odpovídá zadanému klíči. Tato funkce je bezpečná pro souběžnost.

```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Hodnota klíče, která se má vyhledat

### <a name="return-value"></a>Návratová hodnota

[Pár](../../../standard-library/pair-structure.md) , kde je prvním prvkem iterátor na začátek a druhý prvek je iterátorem na konci rozsahu.

### <a name="remarks"></a>Poznámky

Souběžné vkládání může způsobit vložení dalších klíčů za počáteční iterátor a před konečným iterátorem.

##  <a name="find"></a>najít

Vyhledá prvek, který odpovídá zadanému klíči. Tato funkce je bezpečná pro souběžnost.

```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Hodnota klíče, která se má vyhledat

### <a name="return-value"></a>Návratová hodnota

Iterátor ukazující na umístění prvního prvku, který odpovídá zadanému klíči, nebo iterátoru `end()`, pokud žádný takový prvek neexistuje.

##  <a name="get_allocator"></a>get_allocator

Vrátí uložený objekt přidělování pro tento souběžný kontejner. Tato metoda je bezpečná pro souběžnost.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt přidělování pro tento souběžný kontejner.

##  <a name="hash_function"></a>hash_function

Získá uložený objekt hashovací funkce.

```
hasher hash_function() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt funkce hash.

##  <a name="insert"></a>zadat

Přidá prvky do objektu `concurrent_unordered_map`.

```
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```

### <a name="parameters"></a>Parametry

*_Iterator*<br/>
Typ iterátoru, který se používá pro vložení.

*V*<br/>
Typ hodnoty vložené do mapy

*value*<br/>
Hodnota, která má být vložena.

*_Where*<br/>
Počáteční umístění, ve kterém se má hledat bod vložení

*first*<br/>
Začátek rozsahu, který má být vložen.

*posledního*<br/>
Konec rozsahu, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Pár, který obsahuje iterátor a logickou hodnotu. Další podrobnosti najdete v části s poznámkami.

### <a name="remarks"></a>Poznámky

První členská funkce určuje, zda element X existuje v sekvenci, jejíž klíč má ekvivalentní řazení `value`. Pokud ne, vytvoří takový element X a inicializuje jej pomocí `value`. Funkce pak určí `where` iterátoru, který určí X. Pokud došlo k vložení, funkce vrátí `std::pair(where, true)`. V opačném případě vrátí `std::pair(where, false)`.

Druhá členská funkce vrátí INSERT (`value`), pomocí `_Where` jako počáteční místo v kontrolované sekvenci pro vyhledání bodu vložení.

Třetí členská funkce vloží sekvenci hodnot prvků z rozsahu [`first`, `last`).

Poslední dvě členské funkce se chovají stejně jako první dva, s tím rozdílem, že `value` slouží k vytvoření vložené hodnoty.

##  <a name="key_eq"></a>key_eq

Získá uložený objekt funkce porovnání rovnosti.

```
key_equal key_eq() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt funkce porovnání rovnosti.

##  <a name="load_factor"></a>load_factor

Vypočítá a vrátí aktuální faktor zatížení kontejneru. Faktor zatížení je počet prvků v kontejneru dělený počtem kontejnerů.

```
float load_factor() const;
```

### <a name="return-value"></a>Návratová hodnota

Faktor zatížení pro kontejner.

##  <a name="max_load_factor"></a>max_load_factor

Získá nebo nastaví maximální faktor zatížení kontejneru. Maximální faktor zatížení je největší počet prvků, než může být v libovolném kontejneru, než se zvětší vnitřní tabulka.

```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>Parametry

`_Newmax`

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí uložený maximální faktor zatížení. Druhá členská funkce nevrací hodnotu, ale vyvolá výjimku [out_of_range](../../../standard-library/out-of-range-class.md) , pokud zadaný faktor zatížení není platný.

##  <a name="max_size"></a>max_size

Vrátí maximální velikost souběžného kontejneru určenou přidělováním. Tato metoda je bezpečná pro souběžnost.

```
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet prvků, které mohou být vloženy do tohoto souběžného kontejneru.

### <a name="remarks"></a>Poznámky

Tato hodnota horní meze může být ve skutečnosti vyšší, než kolik může kontejner skutečně uchovávat.

##  <a name="operator_at"></a>operator [] – operátor

Vyhledá nebo vloží prvek se zadaným klíčem. Tato metoda je bezpečná pro souběžnost.

```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Hodnota klíče, na kterou se má

najít nebo vložit.

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu dat nalezeného nebo vloženého prvku.

### <a name="remarks"></a>Poznámky

Pokud není nalezena hodnota klíče argumentu, je vložen spolu s výchozí hodnotou datového typu.

`operator[]` lze použít k vložení prvků do mapy `m` pomocí `m[key] = DataValue;`, kde `DataValue` je hodnota `mapped_type` prvku s hodnotou klíče `key`.

Při použití `operator[]` pro vložení prvků, vrácený odkaz neurčuje, zda vložení mění již existující prvek nebo vytváří nový. Členské funkce `find` a [INSERT](#insert) lze použít k určení, zda je prvek se zadaným klíčem již přítomen před vložením.

##  <a name="operator_eq"></a>operátor =

Přiřadí obsah jiného objektu `concurrent_unordered_map` k tomuto. Tato metoda není bezpečná pro souběžnost.

```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>Parametry

*_Umap*<br/>
Zdrojový objekt `concurrent_unordered_map`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `concurrent_unordered_map`.

### <a name="remarks"></a>Poznámky

Po vymazání všech existujících prvků v souběžném vektoru `operator=` buď zkopírování nebo přesunutí obsahu `_Umap` do souběžného vektoru.

##  <a name="rehash"></a>rehash –

Znovu vytvoří hashovací tabulku.

```
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>Parametry

*_Buckets*<br/>
Požadovaný počet kontejnerů.

### <a name="remarks"></a>Poznámky

Členská funkce mění počet intervalů, aby byly alespoň `_Buckets` a znovu sestaví zatřiďovací tabulku podle potřeby. Počet intervalů musí být mocninou čísla 2. Pokud není mocninou 2, zaokrouhlí se na nejbližší největší mocninu 2.

Vyvolá výjimku [out_of_range](../../../standard-library/out-of-range-class.md) , pokud je počet intervalů neplatný (0 nebo vyšší než maximální počet intervalů).

##  <a name="size"></a>hodnota

Vrátí počet prvků v tomto souběžném kontejneru. Tato metoda je bezpečná pro souběžnost.

```
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v kontejneru.

### <a name="remarks"></a>Poznámky

V přítomnosti souběžných vložení se počet prvků v souběžném kontejneru může změnit hned po volání této funkce, před tím, než je návratová hodnota ještě přečtena.

##  <a name="swap"></a>adresu

Zamění obsah dvou objektů `concurrent_unordered_map`. Tato metoda není bezpečná pro souběžnost.

```
void swap(concurrent_unordered_map& _Umap);
```

### <a name="parameters"></a>Parametry

*_Umap*<br/>
Objekt `concurrent_unordered_map` pro prohození.

##  <a name="unsafe_begin"></a>unsafe_begin

Vrátí iterátor na první prvek v tomto kontejneru pro konkrétní kontejner.

```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Index kontejneru.

### <a name="return-value"></a>Návratová hodnota

Iterátor ukazující na začátek kontejneru.

##  <a name="unsafe_bucket"></a>unsafe_bucket

Vrátí index kontejneru, na který se v tomto kontejneru mapuje konkrétní klíč.

```
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Klíč elementu, který se má vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index intervalu pro klíč v tomto kontejneru.

##  <a name="unsafe_bucket_count"></a>unsafe_bucket_count

Vrátí aktuální počet kontejnerů v tomto kontejneru.

```
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální počet kontejnerů v tomto kontejneru.

##  <a name="unsafe_bucket_size"></a>unsafe_bucket_size

Vrátí počet položek v určitém intervalu tohoto kontejneru.

```
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Interval, ve kterém se má hledat.

### <a name="return-value"></a>Návratová hodnota

Aktuální počet kontejnerů v tomto kontejneru.

##  <a name="unsafe_cbegin"></a>unsafe_cbegin

Vrátí iterátor na první prvek v tomto kontejneru pro konkrétní kontejner.

```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Index kontejneru.

### <a name="return-value"></a>Návratová hodnota

Iterátor ukazující na začátek kontejneru.

##  <a name="unsafe_cend"></a>unsafe_cend

Vrátí iterátor do umístění, které následuje po posledním prvku v určitém kontejneru.

```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Index kontejneru.

### <a name="return-value"></a>Návratová hodnota

Iterátor ukazující na začátek kontejneru.

##  <a name="unsafe_end"></a>unsafe_end

Vrátí iterátor pro poslední prvek v tomto kontejneru pro konkrétní kontejner.

```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Index kontejneru.

### <a name="return-value"></a>Návratová hodnota

Iterátor ukazující na konec intervalu.

##  <a name="unsafe_erase"></a>unsafe_erase

Odebere prvky z `concurrent_unordered_map` na zadané pozici. Tato metoda není bezpečná pro souběžnost.

```
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator _Begin,
    const_iterator _End);

size_type unsafe_erase(
    const key_type& KVal);
```

### <a name="parameters"></a>Parametry

*_Where*<br/>
Pozice iterátoru, ze které se má vymazat.

*_Begin*<br/>
Pozice prvního prvku v rozsahu prvků, které mají být smazány.

*_End*<br/>
Pozice prvního prvku mimo rozsah prvků, které mají být smazány.

*KVal*<br/>
Hodnota klíče, která se má vymazat

### <a name="return-value"></a>Návratová hodnota

První dvě členské funkce vrátí iterátor, který určí první prvek zbývající za odebranými prvky, nebo `concurrent_unordered_map::end`(), pokud žádný takový prvek neexistuje. Třetí členská funkce vrátí počet prvků, které odebere.

### <a name="remarks"></a>Poznámky

První členská funkce odstraní prvek řízené sekvence, na kterou ukazuje `_Where`. Druhá členská funkce odstraní prvky v rozsahu [`_Begin`, `_End`).

Třetí členská funkce odstraní prvky v rozsahu, který je oddělený `concurrent_unordered_map::equal_range`(KVal).

##  <a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count

Vrátí maximální počet kontejnerů v tomto kontejneru.

```
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet kontejnerů v tomto kontejneru.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md)
