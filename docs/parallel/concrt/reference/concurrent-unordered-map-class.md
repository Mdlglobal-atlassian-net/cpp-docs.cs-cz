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
ms.openlocfilehash: 43ad777b0dfb1285a82d662f37329c079410c78d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262564"
---
# <a name="concurrentunorderedmap-class"></a>concurrent_unordered_map – třída

`concurrent_unordered_map` Třídy je kontejner bezpečné souběžnosti, který řídí různé délky sekvence elementů typu `std::pair<const K, _Element_type>`. Sekvence je reprezentována způsobem, který umožňuje bezpečné na souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru připojit.

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
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navracení zpět paměti pro souběžnou neuspořádanou mapu. Tento argument je nepovinný a výchozí hodnota je `std::allocator<std::pair<K`, `_Element_type>>`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
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

|Název|Popis|
|----------|-----------------|
|[concurrent_unordered_map](#ctor)|Přetíženo. Sestaví souběžnou neuspořádanou mapu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[at](#at)|Přetíženo. Vyhledá prvek v `concurrent_unordered_map` se zadanou hodnotou klíče... Tato metoda je bezpečná pro souběžnost.|
|[hash_function –](#hash_function)|Získá uložený objekt hashovací funkce.|
|[Vložit](#insert)|Přetíženo. Přidá prvky do `concurrent_unordered_map` objektu.|
|[key_eq](#key_eq)|Získá uložené rovnosti objektu funkce porovnání.|
|[swap](#swap)|Zamění obsah dvou `concurrent_unordered_map` objekty. Tato metoda není bezpečná pro souběžnost.|
|[unsafe_erase](#unsafe_erase)|Přetíženo. Odebere prvky z `concurrent_unordered_map` v určených pozicích. Tato metoda není bezpečná pro souběžnost.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[– Operátor\[\]](#operator_at)|Přetíženo. Vyhledá nebo vloží prvek se zadaným klíčem. Tato metoda je bezpečná pro souběžnost.|
|[operátor =](#operator_eq)|Přetíženo. Přiřadí obsah jiného `concurrent_unordered_map` do tohoto objektu. Tato metoda není bezpečná pro souběžnost.|

## <a name="remarks"></a>Poznámky

Podrobné informace o `concurrent_unordered_map` najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_map`

## <a name="requirements"></a>Požadavky

**Header:** concurrent_unordered_map.h

**Namespace:** souběžnosti

##  <a name="at"></a> v

Vyhledá prvek v `concurrent_unordered_map` se zadanou hodnotou klíče... Tato metoda je bezpečná pro souběžnost.

```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Hodnota klíče k vyhledání.

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu dat nalezeného prvku.

### <a name="remarks"></a>Poznámky

Pokud není nalezena klíčová hodnota argumentu, funkce vyvolá objekt třídy `out_of_range`.

##  <a name="begin"></a> začít

Vrátí iterátor odkazující na první prvek v kontejneru souběžných. Tato metoda je bezpečné na souběžnosti.

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor na první prvek v kontejneru souběžných.

##  <a name="cbegin"></a> cbegin

Vrátí konstantní iterátor odkazující na první prvek v kontejneru souběžných. Tato metoda je bezpečné na souběžnosti.

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní iterátor na první prvek v kontejneru souběžných.

##  <a name="cend"></a> cend

Vrátí konstantní iterátor odkazující na umístění následující po posledním prvku v souběžné kontejneru. Tato metoda je bezpečné na souběžnosti.

```
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní iterátor adresující poslední prvek v kontejneru souběžných umístění.

##  <a name="clear"></a> Vymazat

Vymaže všechny prvky v kontejneru souběžných. Tato funkce není bezpečné na souběžnosti.

```
void clear();
```

##  <a name="ctor"></a> concurrent_unordered_map

Sestaví souběžnou neuspořádanou mapu.

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
Počáteční počet kbelíků pro tento neuspořádanou mapu.

*_Hasher*<br/>
Funkce hash pro tuto neuspořádanou mapu.

*key_equality*<br/>
Funkce porovnání rovnosti pro tento neuspořádanou mapu.

*_Allocator*<br/>
Alokátor pro tento neuspořádanou mapu.

*_Zahájit*<br/>
Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.

*_End*<br/>
Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.

*_Umap*<br/>
Zdroj `concurrent_unordered_map` objektu, který chcete zkopírovat nebo přesunout elementy ze.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt alokátoru `_Allocator` a inicializovat neuspořádanou mapu.

První konstruktor určí prázdný počáteční mapování a explicitně určuje počet kbelíků, hashovací funkce, funkce rovnosti a alokátoru typu má být použit.

Druhý konstruktor určuje alokátoru pro neuspořádanou mapu.

Třetí konstruktor určuje hodnoty poskytnuté rozsahem iterátoru [ `_Begin`, `_End`).

Čtvrtý a pátý konstruktor určuje kopii souběžnou neuspořádanou mapu `_Umap`.

Poslední konstruktor určuje pohyb souběžnou neuspořádanou mapu `_Umap`.

##  <a name="count"></a> Počet

Spočítá počet prvků odpovídající zadanému klíči. Tato funkce je bezpečné na souběžnosti.

```
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Klíč k vyhledání.

### <a name="return-value"></a>Návratová hodnota

Počet opakování, kolikrát se zobrazí klíče v kontejneru.

##  <a name="empty"></a> prázdný

Zkouší, zda nejsou přítomny žádné prvky. Tato metoda je bezpečné na souběžnosti.

```
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je prázdný, souběžné kontejner **false** jinak.

### <a name="remarks"></a>Poznámky

Za přítomnosti souběžné operace vložení Určuje, jestli je prázdný souběžných kontejneru se může změnit ihned po volání této funkce, než je návratová hodnota i čtení.

##  <a name="end"></a> ukončení

Vrátí iterátor odkazující na umístění následující po posledním prvku v souběžné kontejneru. Tato metoda je bezpečné na souběžnosti.

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor adresující poslední prvek v kontejneru souběžných umístění.

##  <a name="equal_range"></a> equal_range –

Najde rozsah, který odpovídá zadanému klíči. Tato funkce je bezpečné na souběžnosti.

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
Hodnota klíče pro hledání.

### <a name="return-value"></a>Návratová hodnota

A [pár](../../../standard-library/pair-structure.md) kde první prvek je iterace na začátek a druhý prvek je iterátor na konec rozsahu.

### <a name="remarks"></a>Poznámky

Je možné pro souběžné operace vložení způsobit další klíče má být vložen iterátoru počáteční a koncový iterátor.

##  <a name="find"></a> Najít

Vyhledá prvek, který odpovídá zadanému klíči. Tato funkce je bezpečné na souběžnosti.

```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Hodnota klíče pro hledání.

### <a name="return-value"></a>Návratová hodnota

Iterátor odkazující na umístění prvního prvku, který odpovídá klíči poskytovaném nebo iterátor `end()` Pokud žádný takový prvek neexistuje.

##  <a name="get_allocator"></a> get_allocator

Vrátí uložený objekt alokátoru pro tento souběžný kontejner. Tato metoda je bezpečné na souběžnosti.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt alokátoru pro tento souběžný kontejner.

##  <a name="hash_function"></a> hash_function –

Získá uložený objekt hashovací funkce.

```
hasher hash_function() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt hashovací funkce.

##  <a name="insert"></a> Vložit

Přidá prvky do `concurrent_unordered_map` objektu.

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
Typ hodnoty vložen do objektu map.

*value*<br/>
Hodnota má být vložen.

*_Where*<br/>
Výchozí umístění pro vyhledávání pro kurzor.

*první*<br/>
Začátek rozsahu, který chcete vložit.

*last*<br/>
Konec rozsahu, který chcete vložit.

### <a name="return-value"></a>Návratová hodnota

Pár, který obsahuje iterátoru a logickou hodnotu. Další podrobnosti v části poznámky.

### <a name="remarks"></a>Poznámky

První členská funkce určuje, zda element X existuje v sekvenci, jehož klíč má ekvivalentní řazení, která `value`. Pokud ne, takový prvek X vytvoří a inicializuje ji s `value`. Funkce pak určuje iterátor `where` , který označí X. Pokud došlo k vložení, funkce vrátí `std::pair(where, true)`. V opačném případě vrátí `std::pair(where, false)`.

Druhá členská funkce vrátí vložit ( `value`) s použitím `_Where` jako výchozí bod v řízené sekvenci k vyhledání kurzor.

Třetí členská funkce vloží sekvenci hodnot prvku v rozsahu [ `first`, `last`).

Poslední dva členské funkce se chovají stejně jako první dva, s výjimkou, že `value` se používá ke konstrukci Vložená hodnota.

##  <a name="key_eq"></a> key_eq

Získá uložené rovnosti objektu funkce porovnání.

```
key_equal key_eq() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložené porovnání rovnosti objektu funkce.

##  <a name="load_factor"></a> load_factor –

Vypočítá a vrátí aktuální faktor zaplnění kontejneru. Faktor zaplnění je počet elementů v kontejneru dělený počet kbelíků.

```
float load_factor() const;
```

### <a name="return-value"></a>Návratová hodnota

Faktor zaplnění pro kontejner.

##  <a name="max_load_factor"></a> max_load_factor –

Získává nebo nastavuje faktor maximálního zatížení kontejneru. Faktor maximálního zatížení je největší číslo z prvků, než může být v jakékoli intervalu než kontejner roste příslušné interní tabulky.

```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>Parametry

`_Newmax`

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí faktor maximálního zatížení uložené. Druhá členská funkce nevrací hodnotu, ale vyvolá [out_of_range –](../../../standard-library/out-of-range-class.md) výjimku, pokud je neplatný zadaný vytížení...

##  <a name="max_size"></a> max_size

Vrátí maximální velikost kontejneru souběžných určené přidělujícího modulu. Tato metoda je bezpečné na souběžnosti.

```
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet prvků, které mohou být zařazeny do tohoto souběžných kontejneru.

### <a name="remarks"></a>Poznámky

Tato hodnota horní mez, ve skutečnosti může být vyšší, než co kontejner ve skutečnosti, podržte.

##  <a name="operator_at"></a> Operator [].

Vyhledá nebo vloží prvek se zadaným klíčem. Tato metoda je bezpečná pro souběžnost.

```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Hodnotu klíče pro

vyhledat nebo vložit.

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu data nalezen nebo vložený element.

### <a name="remarks"></a>Poznámky

Pokud není nalezena hodnota klíče argumentu, je vložen spolu s výchozí hodnotou datového typu.

`operator[]` slouží k vložit prvky do mapy `m` pomocí `m[key] = DataValue;`, kde `DataValue` je hodnota `mapped_type` prvku s hodnotou klíče `key`.

Při použití `operator[]` vložit prvky, vrácený odkaz neudává, zda je vložení změna již existující element nebo vytvoří nový. Členské funkce `find` a [vložit](#insert) slouží k určení, zda element s určeným klíčem již existuje před vložením.

##  <a name="operator_eq"></a> operátor =

Přiřadí obsah jiného `concurrent_unordered_map` do tohoto objektu. Tato metoda není bezpečná pro souběžnost.

```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>Parametry

*_Umap*<br/>
Zdroj `concurrent_unordered_map` objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `concurrent_unordered_map` objektu.

### <a name="remarks"></a>Poznámky

Po odstranění jakýchkoli prvků souběžného vektoru `operator=` kopíruje nebo přesouvá obsah `_Umap` do souběžného vektoru.

##  <a name="rehash"></a> rehash

Znovu vytvoří hashovací tabulku.

```
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>Parametry

*_Buckets*<br/>
Požadovaný počet kbelíků.

### <a name="remarks"></a>Poznámky

Členská funkce mění počet kbelíků nejméně `_Buckets` a znovu vytvoří hashovací tabulku podle potřeby. Počet kbelíků musí být mocninou čísla 2. Pokud není mocninou čísla 2, ho budou zaokrouhleny nahoru na další největší mocninu 2.

Vyvolá [out_of_range –](../../../standard-library/out-of-range-class.md) výjimku, pokud počet kbelíků je neplatný (0 nebo větší než maximální počet kbelíků).

##  <a name="size"></a> Velikost

Vrátí počet prvků v tomto souběžných kontejneru. Tato metoda je bezpečné na souběžnosti.

```
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v kontejneru.

### <a name="remarks"></a>Poznámky

Za přítomnosti souběžné operace vložení může změnit počet prvků v kontejneru souběžných ihned po volání této funkce, než je návratová hodnota i čtení.

##  <a name="swap"></a> Prohození

Zamění obsah dvou `concurrent_unordered_map` objekty. Tato metoda není bezpečná pro souběžnost.

```
void swap(concurrent_unordered_map& _Umap);
```

### <a name="parameters"></a>Parametry

*_Umap*<br/>
`concurrent_unordered_map` Objektu, který chcete Prohodit s.

##  <a name="unsafe_begin"></a> unsafe_begin –

Vrátí iterátor na první prvek v tomto kontejneru pro konkrétní blok.

```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Index kontejneru.

### <a name="return-value"></a>Návratová hodnota

Iterátor odkazující na začátku bloku.

##  <a name="unsafe_bucket"></a> unsafe_bucket –

Vrátí index kontejneru, který se mapuje konkrétního klíče v tomto kontejneru.

```
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>Parametry

*KVal*<br/>
Klíč elementu, vyhledaly.

### <a name="return-value"></a>Návratová hodnota

Index kontejneru klíče v tomto kontejneru.

##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count

Vrátí aktuální počet kbelíků v tomto kontejneru.

```
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální počet kbelíků, v tomto kontejneru.

##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size

Vrátí počet položek v konkrétním intervalu tohoto kontejneru.

```
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Interval pro hledání.

### <a name="return-value"></a>Návratová hodnota

Aktuální počet kbelíků, v tomto kontejneru.

##  <a name="unsafe_cbegin"></a> unsafe_cbegin –

Vrátí iterátor na první prvek v tomto kontejneru pro konkrétní blok.

```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Index kontejneru.

### <a name="return-value"></a>Návratová hodnota

Iterátor odkazující na začátku bloku.

##  <a name="unsafe_cend"></a> unsafe_cend

Vrátí iterátor na umístění následující po posledním prvku v konkrétním intervalu.

```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Index kontejneru.

### <a name="return-value"></a>Návratová hodnota

Iterátor odkazující na začátku bloku.

##  <a name="unsafe_end"></a> unsafe_end –

Vrátí iterátor na poslední prvek v tomto kontejneru pro konkrétní blok.

```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>Parametry

*_Bucket*<br/>
Index kontejneru.

### <a name="return-value"></a>Návratová hodnota

Iterátorem ukazujícím na konec bloku.

##  <a name="unsafe_erase"></a> unsafe_erase –

Odebere prvky z `concurrent_unordered_map` v určených pozicích. Tato metoda není bezpečná pro souběžnost.

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
Pozice iterátoru, který chcete smazat.

*_Zahájit*<br/>
Pozice prvního prvku v rozsahu prvků, které mají být vymazány.

*_End*<br/>
Pozice prvního prvku mimo rozsah prvků, které mají být vymazány.

*KVal*<br/>
Hodnota klíče vymazat.

### <a name="return-value"></a>Návratová hodnota

První dvě členské funkce vrátí iterátor, který určuje první prvek zbývající za všemi odstraněnými prvky, nebo `concurrent_unordered_map::end`(), pokud žádný takový prvek neexistuje. Třetí členská funkce vrátí počet prvků, které odebere.

### <a name="remarks"></a>Poznámky

První členská funkce odstraní prvek řízené sekvence, na které odkazuje `_Where`. Druhá členská funkce odebere prvky v rozsahu [ `_Begin`, `_End`).

Třetí členská funkce odebere prvky v rozsahu odděleny `concurrent_unordered_map::equal_range`(KVal).

##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count

Vrátí maximální počet kbelíků v tomto kontejneru.

```
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet kbelíků, v tomto kontejneru.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md)
