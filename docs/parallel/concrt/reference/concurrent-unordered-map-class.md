---
title: concurrent_unordered_map – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 932cfe232b07a9020af450ad33bb34101827ac79
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="concurrentunorderedmap-class"></a>concurrent_unordered_map – třída
`concurrent_unordered_map` Třída je bezpečné souběžnosti kontejner, který určuje posloupnost různých délka elementy typu `std::pair<const K, _Element_type>`. Pořadí je reprezentována způsobem, který umožňuje bezpečné souběžnosti připojit, iterator traversal operace, iterator přístup a přístup k elementu.  
  
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
 `K`  
 Klíčový typ  
  
 `_Element_type`  
 Mapovaný typ  
  
 `_Hasher`  
 Typ objektu hashovací funkce Tento argument je volitelný a výchozí hodnota je `std::hash<K>`.  
  
 `key_equality`  
 Typ objektu funkce porovnání rovnosti Tento argument je volitelný a výchozí hodnota je `std::equal_to<K>`.  
  
 `_Allocator_type`  
 Typ, který představuje uložené allocator objekt, který zapouzdřuje podrobnosti o přidělení a zrušení přidělení paměti pro souběžné neuspořádaný mapy. Tento argument je volitelný a výchozí hodnota je `std::allocator<std::pair<K`, `_Element_type>>`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
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
|[concurrent_unordered_map](#ctor)|Přetíženo. Vytvoří souběžných neuspořádaný mapy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[at](#at)|Přetíženo. Vyhledá v elementu `concurrent_unordered_map` se zadanou hodnotou klíče... Tato metoda je bezpečné souběžnosti.|  
|[hash_function –](#hash_function)|Získá uložený objekt hashovací funkce.|  
|[Vložení](#insert)|Přetíženo. Přidá elementy na `concurrent_unordered_map` objektu.|  
|[key_eq](#key_eq)|Získá objekt funkce porovnání rovnosti uložené.|  
|[Swap](#swap)|Prohození obsahu dvou `concurrent_unordered_map` objekty. Tato metoda není bezpečná souběžnosti.|  
|[unsafe_erase](#unsafe_erase)|Přetíženo. Odebere elementy z `concurrent_unordered_map` v zadaných pozic. Tato metoda není bezpečná souběžnosti.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[[] – operátor](#operator_at)|Přetíženo. Vyhledá nebo vloží prvek se zadaným klíčem. Tato metoda je bezpečné souběžnosti.|  
|[operátor =](#operator_eq)|Přetíženo. Přiřadí obsah jiného `concurrent_unordered_map` k tomuto objektu. Tato metoda není bezpečná souběžnosti.|  
  
## <a name="remarks"></a>Poznámky  
 Podrobné informace o `concurrent_unordered_map` třídy najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_map`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concurrent_unordered_map.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="at"></a> v 

 Vyhledá v elementu `concurrent_unordered_map` se zadanou hodnotou klíče... Tato metoda je bezpečné souběžnosti.  
  
```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Hodnota klíče najít.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na hodnotu dat nalezen prvek.  
  
### <a name="remarks"></a>Poznámky  
 Pokud není nalezena hodnota klíče argument, funkce vyvolá objekt třídy `out_of_range`.  
  
##  <a name="begin"></a> Začátek 

 Vrátí iterator odkazující na prvním elementem v souběžných kontejneru. Tato metoda je bezpečné souběžnosti.  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor na prvním elementem v souběžných kontejneru.  
  
##  <a name="cbegin"></a> cbegin – 

 Vrátí const iterator odkazující na prvním elementem v souběžných kontejneru. Tato metoda je bezpečné souběžnosti.  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const iterator na prvním elementem v souběžných kontejneru.  
  
##  <a name="cend"></a> cend – 

 Vrátí const iterator odkazující na umístění posledním prvkem v kontejneru souběžných úspěšné. Tato metoda je bezpečné souběžnosti.  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const iterator do umístění posledním prvkem v kontejneru souběžných úspěšné.  
  
##  <a name="clear"></a> Zrušte zaškrtnutí 

 Vymaže všechny elementy v souběžných kontejneru. Tato funkce není bezpečné souběžnosti.  
  
```
void clear();
```  
  
##  <a name="ctor"></a> concurrent_unordered_map 

 Vytvoří souběžných neuspořádaný mapy.  
  
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
 `_Iterator`  
 Typ vstupu iterator.  
  
 `_Number_of_buckets`  
 Počáteční počet kbelíků pro tuto mapu Neseřazený.  
  
 `_Hasher`  
 Funkce hash pro tuto mapu Neseřazený.  
  
 `key_equality`  
 Funkce porovnání rovnosti pro tuto mapu Neseřazený.  
  
 `_Allocator`  
 Allocator pro tuto mapu Neseřazený.  
  
 `_Begin`  
 Pozice první prvek v rozsahu elementy, které se mají zkopírovat.  
  
 `_End`  
 Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.  
  
 `_Umap`  
 Zdroj `concurrent_unordered_map` objekt, který chcete zkopírovat nebo přesunout elementy z.  
  
### <a name="remarks"></a>Poznámky  
 Všechny konstruktory uložit objekt allocator `_Allocator` a inicializace neuspořádaný mapy.  
  
 První konstruktor Určuje počáteční mapování prázdný a explicitně určuje počet intervalů, funkce hash, funkce rovnosti a allocator typ má být použit.  
  
 Druhý konstruktor určuje přidělení neuspořádaný mapy.  
  
 Třetí konstruktor určuje poskytl iterator rozsah hodnot [ `_Begin`, `_End`).  
  
 Konstruktory čtvrté a páté zadejte kopii souběžných neuspořádaný mapy `_Umap`.  
  
 Poslední konstruktor určuje přesunu souběžných neuspořádaný mapy `_Umap`.  
  
##  <a name="count"></a> Počet 

 Spočítá počet elementů odpovídající zadaného klíče. Tato funkce je bezpečné souběžnosti.  
  
```
size_type count(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Klíč k vyhledání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet opakování, kolikrát se zobrazí klíč v kontejneru.  
  
##  <a name="empty"></a> prázdný 

 Zkouší, zda nejsou přítomny žádné prvky. Tato metoda je bezpečné souběžnosti.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je prázdný, kontejneru souběžných `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Případě souběžných vložení, jestli je prázdný souběžných kontejneru se může změnit ihned po volání této funkce, než je návratovou hodnotu i pro čtení.  
  
##  <a name="end"></a> End 

 Vrátí iterator odkazující na umístění posledním prvkem v kontejneru souběžných úspěšné. Tato metoda je bezpečné souběžnosti.  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor do umístění posledním prvkem v kontejneru souběžných úspěšné.  
  
##  <a name="equal_range"></a> equal_range – 

 Vyhledá rozsah, který odpovídá zadaným klíčem. Tato funkce je bezpečné souběžnosti.  
  
```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Hodnota klíče pro vyhledávání.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [pár](http://msdn.microsoft.com/en-us/c5a37023-d939-4eb2-ae24-ce8e0cd4505d) kde první prvek je iterátor na začátku a druhý prvkem je iterátor na konec rozsahu.  
  
### <a name="remarks"></a>Poznámky  
 Je možné pro souběžných vloží způsobí další klíče má být vložen po begin iterator a před end iterator.  
  
##  <a name="find"></a> Najít 

 Vyhledá prvek, který odpovídá zadanému klíči. Tato funkce je bezpečné souběžnosti.  
  
```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Hodnota klíče pro vyhledávání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor odkazující na umístění první prvek, který odpovídá klíči poskytovaném nebo iteraci `end()` Pokud neexistuje žádný takový prvek.  
  
##  <a name="get_allocator"></a> get_allocator – 

 Vrací objekt allocator uložené pro tento souběžných kontejner. Tato metoda je bezpečné souběžnosti.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt allocator uložené pro tento souběžných kontejner.  
  
##  <a name="hash_function"></a> hash_function – 

 Získá uložený objekt hashovací funkce.  
  
```
hasher hash_function() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt funkce uložené hodnoty hash.  
  
##  <a name="insert"></a> Vložení 

 Přidá elementy na `concurrent_unordered_map` objektu.  
  
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
 `_Iterator`  
 Typ iterator použít pro vložení.  
  
 `V`  
 Typ hodnoty vložena do mapy.  
  
 `value`  
 Hodnota, která má být vložen.  
  
 `_Where`  
 Výchozí umístění pro vyhledávání pro bod vložení.  
  
 `first`  
 Začátek rozsahu k vložení.  
  
 `last`  
 Konec rozsahu k vložení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pár, který obsahuje iterovat a logickou hodnotu. Najdete v části poznámky další podrobnosti.  
  
### <a name="remarks"></a>Poznámky  
 První člen funkce určuje, zda element X existuje v pořadí, jehož klíč má ekvivalentní řazení do u `value`. Pokud ne, vytvoří takový prvek X a inicializuje její `value`. Funkce pak určuje iteraci `where` , označí X. Pokud došlo vložení, funkce vrátí hodnotu `std::pair(where, true)`. Funkce `std::pair(where, false)`.  
  
 Druhý členská funkce vrátí vložení ( `value`) pomocí `_Where` jako výchozí bod v řízené sekvenci k vyhledání kurzor.  
  
 Třetí členská funkce vloží pořadí hodnot element z rozsahu [ `first`, `last`).  
  
 Poslední dva členské funkce chovají stejně jako první dvě, vyjma toho, že `value` se používá pro konstrukci zadaná hodnota.  
  
##  <a name="key_eq"></a> key_eq – 

 Získá objekt funkce porovnání rovnosti uložené.  
  
```
key_equal key_eq() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt funkce porovnání rovnosti uložené.  
  
##  <a name="load_factor"></a> load_factor – 

 Vypočítá a vrátí aktuální zatížení Multi-Factor kontejneru. Koeficient zatížení je počet elementů v kontejneru rozdělené podle počtu kbelíků.  
  
```
float load_factor() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Koeficient zatížení kontejneru.  
  
##  <a name="max_load_factor"></a> max_load_factor – 

 Získá nebo nastaví maximální zatížení faktor kontejneru. Maximální zatížení faktor je největší počet prvků, než může být v žádné sady než kontejneru zvětšování jeho interní tabulku.  
  
```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```  
  
### <a name="parameters"></a>Parametry  
 `_Newmax`  
  
### <a name="return-value"></a>Návratová hodnota  
 První člen funkce vrátí Multi-Factor uložené maximální zatížení. Druhý členská funkce nevrací hodnotu, ale vyvolá [out_of_range](../../../standard-library/out-of-range-class.md) výjimka, pokud zadaná zatížení faktor je neplatný...  
  
##  <a name="max_size"></a> max_size – 

 Vrátí maximální velikost souběžných kontejneru, určit pomocí přidělujícího modulu. Tato metoda je bezpečné souběžnosti.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální počet prvků, které lze vložit do tohoto souběžných kontejneru.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota horní mez může být ve skutečnosti vyšší, než co kontejneru ve skutečnosti pojme.  
  
##  <a name="operator_at"></a> [] – operátor 

 Vyhledá nebo vloží prvek se zadaným klíčem. Tato metoda je bezpečné souběžnosti.  
  
```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Hodnota klíče na  
  
 najít, nebo vložit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na hodnotu data najde nebo vložené elementu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud není nalezena hodnota klíče argumentu, je vložen spolu s výchozí hodnotou datového typu.  
  
 `operator[]` slouží k vložení elementy do mapy `m` pomocí `m[key] = DataValue;`, kde `DataValue` je hodnota `mapped_type` elementu s hodnotou klíče `key`.  
  
 Při použití `operator[]` Pokud chcete vložit elementy, vrácený odkaz neindikuje, zda je vložení Změna existující element nebo vytvořením nové. Členské funkce `find` a [vložit](#insert) slouží k určení, zda element se zadaným klíčem již nachází před vložení.  
  
##  <a name="operator_eq"></a> operátor = 

 Přiřadí obsah jiného `concurrent_unordered_map` k tomuto objektu. Tato metoda není bezpečná souběžnosti.  
  
```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```  
  
### <a name="parameters"></a>Parametry  
 `_Umap`  
 Zdroj `concurrent_unordered_map` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `concurrent_unordered_map` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Po vymazání existující prvky souběžných vektoru, `operator=` buď kopíruje nebo přesouvá obsah `_Umap` do souběžných vektoru.  
  
##  <a name="rehash"></a> rehash – 

 Znovu vytvoří hashovací tabulku.  
  
```
void rehash(size_type _Buckets);
```  
  
### <a name="parameters"></a>Parametry  
 `_Buckets`  
 Požadovaný počet intervalů.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce mění počet intervalů nejméně `_Buckets` a znovu sestaví zatřiďovací tabulce podle potřeby. Počet intervalů, musí být násobkem 2. Pokud není mocninou 2, bude další největší exponentem 2 zaokrouhlit.  
  
 Vyvolá [out_of_range](../../../standard-library/out-of-range-class.md) výjimka, pokud počet intervalů, je neplatný (0 nebo větší než maximální počet kbelíků).  
  
##  <a name="size"></a> Velikost 

 Vrátí počet prvků v tomto souběžných kontejneru. Tato metoda je bezpečné souběžnosti.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v kontejneru.  
  
### <a name="remarks"></a>Poznámky  
 Případě souběžných vložení může změnit počet elementů v kontejneru souběžných ihned po volání této funkce, než je návratovou hodnotu i pro čtení.  
  
##  <a name="swap"></a> Swap 

 Prohození obsahu dvou `concurrent_unordered_map` objekty. Tato metoda není bezpečná souběžnosti.  
  
```
void swap(concurrent_unordered_map& _Umap);
```  
  
### <a name="parameters"></a>Parametry  
 `_Umap`  
 `concurrent_unordered_map` Objekt, který chcete Prohodit s.  
  
##  <a name="unsafe_begin"></a> unsafe_begin – 

 Vrátí první prvek v tomto kontejneru pro konkrétní sady iterace.  
  
```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 Bucket index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace odkazující na začátku bloku.  
  
##  <a name="unsafe_bucket"></a> unsafe_bucket – 

 Vrátí index sady, který konkrétního klíče mapy v tomto kontejneru.  
  
```
size_type unsafe_bucket(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Klíč elementu, který se hledají.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index sady pro klíč v tomto kontejneru.  
  
##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count – 

 Vrátí aktuální počet intervalů, v tomto kontejneru.  
  
```
size_type unsafe_bucket_count() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální počet intervalů, v tomto kontejneru.  
  
##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size – 

 Vrátí počet položek v konkrétní sady tohoto kontejneru.  
  
```
size_type unsafe_bucket_size(size_type _Bucket);
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 V bloku k vyhledání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální počet intervalů, v tomto kontejneru.  
  
##  <a name="unsafe_cbegin"></a> unsafe_cbegin – 

 Vrátí první prvek v tomto kontejneru pro konkrétní sady iterace.  
  
```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 Bucket index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace odkazující na začátku bloku.  
  
##  <a name="unsafe_cend"></a> unsafe_cend 

 Vrátí iterator do umístění úspěšné posledním prvkem v konkrétní sady.  
  
```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 Bucket index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace odkazující na začátku bloku.  
  
##  <a name="unsafe_end"></a> unsafe_end – 

 Vrátí iterovat posledním prvkem v tomto kontejneru pro konkrétní sady.  
  
```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 Bucket index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace odkazující na konci bloku.  
  
##  <a name="unsafe_erase"></a> unsafe_erase – 

 Odebere elementy z `concurrent_unordered_map` v zadaných pozic. Tato metoda není bezpečná souběžnosti.  
  
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
 `_Where`  
 Iterator pozice vymazat z.  
  
 `_Begin`  
 Pozice první prvek v rozsahu elementy, aby bylo možné vymazat.  
  
 `_End`  
 Pozice první prvek mimo rozsah elementy, aby bylo možné vymazat.  
  
 `KVal`  
 Hodnota klíče vymazat.  
  
### <a name="return-value"></a>Návratová hodnota  
 První dva členské funkce vrátí iterátor, který označí první prvek zbývající nad rámec všechny elementy odebrán, nebo `concurrent_unordered_map::end`(), pokud neexistuje žádný takový prvek. Třetí členská funkce vrátí počet prvků, které se odeberou.  
  
### <a name="remarks"></a>Poznámky  
 Odebere první členská funkce elementu řízené sekvenci, na kterou odkazuje `_Where`. Druhý členská funkce odebere elementy v rozsahu [ `_Begin`, `_End`).  
  
 Třetí členská funkce odebere elementy v rozsahu oddělená `concurrent_unordered_map::equal_range`(KVal).  
  
##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count – 

 Vrátí maximální počet intervalů, v tomto kontejneru.  
  
```
size_type unsafe_max_bucket_count() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální počet intervalů, v tomto kontejneru.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md)



