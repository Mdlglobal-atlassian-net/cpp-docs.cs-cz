---
title: concurrent_unordered_multiset – třída
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_multiset
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::concurrent_unordered_multiset
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::hash_function
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::insert
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::key_eq
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::swap
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_multiset::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_multiset class
ms.assetid: 219d7d67-1ff0-45f4-9400-e9cc272991a4
ms.openlocfilehash: 8b03245790bf011941cabcb18600bbb1e69c37d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543933"
---
# <a name="concurrentunorderedmultiset-class"></a>concurrent_unordered_multiset – třída

`concurrent_unordered_multiset` Třídy je kontejner bezpečné souběžnosti, který řídí různé délky sekvence elementů typu K. Sekvence je reprezentována způsobem, který umožňuje bezpečné na souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru připojit.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>
>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>> class concurrent_unordered_multiset : public details::_Concurrent_hash<details::_Concurrent_unordered_set_traits<K,
    details::_Hash_compare<K,
_Hasher,
    key_equality>,
_Allocator_type,
    true>>;
```

#### <a name="parameters"></a>Parametry

*K*<br/>
Klíčový typ

*_Hasher*<br/>
Typ objektu hashovací funkce Tento argument je nepovinný a výchozí hodnota je `std::hash<K>`.

*key_equality*<br/>
Typ objektu funkce porovnání rovnosti Tento argument je nepovinný a výchozí hodnota je `std::equal_to<K>`.

*_Allocator_type*<br/>
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navracení zpět paměti pro souběžný vektor. Tento argument je nepovinný a výchozí hodnota je `std::allocator<K>`.

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
|`pointer`|Typ ukazatele na prvek|
|`reference`|Typ odkazu na prvek|
|`size_type`|Typ vzdálenosti bez znaménka mezi dvěma prvky|
|`value_type`|Typ prvku|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[concurrent_unordered_multiset](#ctor)|Přetíženo. Sestaví souběžnou neuspořádanou multisadu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[hash_function –](#hash_function)|Vrátí uložený objekt hashovací funkce.|
|[Vložit](#insert)|Přetíženo. Přidá prvky do `concurrent_unordered_multiset` objektu.|
|[key_eq](#key_eq)|Uložené porovnání rovnosti objektu funkce.|
|[Prohození](#swap)|Zamění obsah dvou `concurrent_unordered_multiset` objekty. Tato metoda není bezpečná pro souběžnost.|
|[unsafe_erase](#unsafe_erase)|Přetíženo. Odebere prvky z `concurrent_unordered_multiset` v určených pozicích. Tato metoda není bezpečná pro souběžnost.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Přetíženo. Přiřadí obsah jiného `concurrent_unordered_multiset` do tohoto objektu. Tato metoda není bezpečná pro souběžnost.|

## <a name="remarks"></a>Poznámky

Podrobné informace o `concurrent_unordered_multiset` najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_multiset`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concurrent_unordered_set.h

**Namespace:** souběžnosti

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

##  <a name="ctor"></a> concurrent_unordered_multiset –

Sestaví souběžnou neuspořádanou multisadu.

```
explicit concurrent_unordered_multiset(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multiset(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_multiset(_Iterator first,
    _Iterator last,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_multiset(
    const concurrent_unordered_multiset& _Uset);

concurrent_unordered_multiset(
    const concurrent_unordered_multiset& _Uset,
    const allocator_type& _Allocator);

concurrent_unordered_multiset(
    concurrent_unordered_multiset&& _Uset);
```

### <a name="parameters"></a>Parametry

*_Iterator*<br/>
Typ vstupního iterátoru.

*_Number_of_buckets*<br/>
Počáteční počet kbelíků pro tento neuspořádanou multisadu.

*_Hasher*<br/>
Funkce hash pro tuto neuspořádanou multisadu.

*key_equality*<br/>
Funkce porovnání rovnosti pro tento neuspořádanou multisadu.

*_Allocator*<br/>
Alokátor pro tento neuspořádanou multisadu.

*první*<br/>
*poslední*<br/>
*_Uset*<br/>
Zdroj `concurrent_unordered_multiset` se mají přesunout prvky z objektu.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt alokátoru `_Allocator` a inicializovat neuspořádanou multisadu.

První konstruktor Určuje prázdnou multimnožinu počáteční a explicitně určuje počet kbelíků, hashovací funkce, funkce rovnosti a alokátoru typu má být použit.

Druhý konstruktor určuje alokátoru pro neuspořádanou multisadu.

Třetí konstruktor určuje hodnoty poskytnuté rozsahem iterátoru [ `_Begin`, `_End`).

Čtvrtý a pátý konstruktor určuje kopii souběžnou neuspořádanou multisadu `_Uset`.

Poslední konstruktor určuje pohyb souběžnou neuspořádanou multisadu `_Uset`.

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

Vrátí uložený objekt hashovací funkce.

```
hasher hash_function() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt hashovací funkce.

##  <a name="insert"></a> Vložit

Přidá prvky do `concurrent_unordered_multiset` objektu.

```
iterator insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
iterator insert(
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
Typ hodnoty vložené.

*value*<br/>
Hodnota má být vložen.

*_Where*<br/>
Výchozí umístění pro vyhledávání pro kurzor.

*první*<br/>
Začátek rozsahu, který chcete vložit.

*poslední*<br/>
Konec rozsahu, který chcete vložit.

### <a name="return-value"></a>Návratová hodnota

Iterátor odkazující na umístění kurzoru.

### <a name="remarks"></a>Poznámky

První členská funkce vloží prvek `value` v řízené sekvenci, pak vrátí iterátor, který určuje vložený prvek.

Druhá členská funkce vrátí vložit ( `value`) s použitím `_Where` jako výchozí bod v řízené sekvenci k vyhledání kurzor.

Třetí členská funkce vloží sekvenci hodnot prvku v rozsahu [ `first`, `last`).

Poslední dva členské funkce se chovají stejně jako první dva, s výjimkou, že `value` se používá ke konstrukci Vložená hodnota.

##  <a name="key_eq"></a> key_eq –

Uložené porovnání rovnosti objektu funkce.

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

##  <a name="operator_eq"></a> operátor =

Přiřadí obsah jiného `concurrent_unordered_multiset` do tohoto objektu. Tato metoda není bezpečná pro souběžnost.

```
concurrent_unordered_multiset& operator= (const concurrent_unordered_multiset& _Uset);

concurrent_unordered_multiset& operator= (concurrent_unordered_multiset&& _Uset);
```

### <a name="parameters"></a>Parametry

*_Uset*<br/>
Zdroj `concurrent_unordered_multiset` objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `concurrent_unordered_multiset` objektu.

### <a name="remarks"></a>Poznámky

Po odstranění jakýchkoli prvků v souběžnou neuspořádanou multisadu `operator=` kopíruje nebo přesouvá obsah `_Uset` do současných neuspořádaná multiset.

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

Zamění obsah dvou `concurrent_unordered_multiset` objekty. Tato metoda není bezpečná pro souběžnost.

```
void swap(concurrent_unordered_multiset& _Uset);
```

### <a name="parameters"></a>Parametry

*_Uset*<br/>
`concurrent_unordered_multiset` Objektu, který chcete Prohodit s.

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

##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count –

Vrátí aktuální počet kbelíků v tomto kontejneru.

```
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální počet kbelíků, v tomto kontejneru.

##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size –

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

Odebere prvky z `concurrent_unordered_multiset` v určených pozicích. Tato metoda není bezpečná pro souběžnost.

```
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator first,
    const_iterator last);

size_type unsafe_erase(
    const key_type& KVal);
```

### <a name="parameters"></a>Parametry

*_Where*<br/>
Pozice iterátoru, který chcete smazat.

*první*<br/>
*poslední*<br/>
*KVal*<br/>
Hodnota klíče vymazat.

### <a name="return-value"></a>Návratová hodnota

První dvě členské funkce vrátí iterátor, který určuje první prvek zbývající za všemi odstraněnými prvky, nebo [end](#end)(), pokud žádný takový prvek neexistuje. Třetí členská funkce vrátí počet prvků, které odebere.

### <a name="remarks"></a>Poznámky

První členská funkce odstraní prvek, na které odkazuje `_Where`. Druhá členská funkce odebere prvky v rozsahu [ `_Begin`, `_End`).

Třetí členská funkce odebere prvky v rozsahu odděleny [equal_range –](#equal_range)(KVal).

##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count –

Vrátí maximální počet kbelíků v tomto kontejneru.

```
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet kbelíků, v tomto kontejneru.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md)

