---
title: "concurrent_unordered_set – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::concurrent_unordered_set
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::hash_function
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::insert
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::key_eq
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::swap
- CONCURRENT_UNORDERED_SET/concurrency::concurrent_unordered_set::unsafe_erase
dev_langs: C++
helpviewer_keywords: concurrent_unordered_set class
ms.assetid: c61f9a9a-4fd9-491a-9251-e300737ecf4b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dfbdcac3bd4d16b96b2ce961b102dfa8c2deea6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="concurrentunorderedset-class"></a>concurrent_unordered_set – třída
`concurrent_unordered_set` Třída je concurrency bezpečných kontejner, který určuje posloupnost různých délka elementy typu K. Pořadí je reprezentována způsobem, který umožňuje bezpečné souběžnosti připojit, iterator traversal operace, iterator přístup a přístup k elementu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename K,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>
>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<K>> class concurrent_unordered_set : public details::_Concurrent_hash<details::_Concurrent_unordered_set_traits<K,
    details::_Hash_compare<K,
 _Hasher,
    key_equality>,
 _Allocator_type,
    false>>;
```   
  
#### <a name="parameters"></a>Parametry  
 `K`  
 Klíčový typ  
  
 `_Hasher`  
 Typ objektu hashovací funkce Tento argument je volitelný a výchozí hodnota je `std::hash<K>`.  
  
 `key_equality`  
 Typ objektu funkce porovnání rovnosti Tento argument je volitelný a výchozí hodnota je `std::equal_to<K>`.  
  
 `_Allocator_type`  
 Typ, který představuje uložené allocator objekt, který zapouzdřuje podrobnosti o přidělení a zrušení přidělení paměti pro souběžné neuspořádaný sadu. Tento argument je volitelný a výchozí hodnota je `std::allocator<K>`.  
  
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
|`pointer`|Typ ukazatele na prvek|  
|`reference`|Typ odkazu na prvek|  
|`size_type`|Typ vzdálenosti bez znaménka mezi dvěma prvky|  
|`value_type`|Typ prvku|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[concurrent_unordered_set](#ctor)|Přetíženo. Vytvoří souběžných neuspořádaný sadu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[hash_function –](#hash_function)|Vrátí objekt funkce uložené hodnoty hash.|  
|[Vložení](#insert)|Přetíženo. Přidá elementy na `concurrent_unordered_set` objektu.|  
|[key_eq –](#key_eq)|Vrátí objekt funkce porovnání rovnosti uložené.|  
|[swap](#swap)|Prohození obsahu dvou `concurrent_unordered_set` objekty. Tato metoda není bezpečná souběžnosti.|  
|[unsafe_erase –](#unsafe_erase)|Přetíženo. Odebere elementy z `concurrent_unordered_set` v zadaných pozic. Tato metoda není bezpečná souběžnosti.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operátor =](#operator_eq)|Přetíženo. Přiřadí obsah jiného `concurrent_unordered_set` k tomuto objektu. Tato metoda není bezpečná souběžnosti.|  
  
## <a name="remarks"></a>Poznámky  
 Podrobné informace o `concurrent_unordered_set` třídy najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_set`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concurrent_unordered_set.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="begin"></a>začít 

 Vrátí iterator odkazující na prvním elementem v souběžných kontejneru. Tato metoda je bezpečné souběžnosti.  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor na prvním elementem v souběžných kontejneru.  
  
##  <a name="cbegin"></a>cbegin – 

 Vrátí const iterator odkazující na prvním elementem v souběžných kontejneru. Tato metoda je bezpečné souběžnosti.  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const iterator na prvním elementem v souběžných kontejneru.  
  
##  <a name="cend"></a>cend – 

 Vrátí const iterator odkazující na umístění posledním prvkem v kontejneru souběžných úspěšné. Tato metoda je bezpečné souběžnosti.  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const iterator do umístění posledním prvkem v kontejneru souběžných úspěšné.  
  
##  <a name="clear"></a>Vymazat 

 Vymaže všechny elementy v souběžných kontejneru. Tato funkce není bezpečné souběžnosti.  
  
```
void clear();
```  
  
##  <a name="ctor"></a>concurrent_unordered_set 

 Vytvoří souběžných neuspořádaný sadu.  
  
```
explicit concurrent_unordered_set(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_set(_Iterator first,
    _Iterator last,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset);

concurrent_unordered_set(
    const concurrent_unordered_set& _Uset,
    const allocator_type& _Allocator);

concurrent_unordered_set(
    concurrent_unordered_set&& _Uset);
```  
  
### <a name="parameters"></a>Parametry  
 `_Iterator`  
 Typ vstupu iterator.  
  
 `_Number_of_buckets`  
 Počáteční počet kbelíků pro tuto neuspořádaný sadu.  
  
 `_Hasher`  
 Funkce hash pro tuto neuspořádaný sadu.  
  
 `key_equality`  
 Funkce porovnání rovnosti pro tuto neuspořádaný sadu.  
  
 `_Allocator`  
 Allocator pro tuto neuspořádaný sadu.  
  
 `first`  
 `last`  
 `_Uset`  
 Zdroj `concurrent_unordered_set` objekt, který chcete zkopírovat nebo přesunout elementy z.  
  
### <a name="remarks"></a>Poznámky  
 Všechny konstruktory uložit objekt allocator `_Allocator` a inicializace neuspořádaný sady.  
  
 První konstruktor určuje prázdný počáteční sadu a explicitně určuje počet intervalů, funkce hash, funkce rovnosti a allocator typ má být použit.  
  
 Druhý konstruktor určuje přidělení pro Neseřazený sadu.  
  
 Třetí konstruktor určuje poskytl iterator rozsah hodnot [ `_Begin`, `_End`).  
  
 Konstruktory čtvrté a páté zadejte kopii sady souběžných neuspořádaný `_Uset`.  
  
 Poslední konstruktor určuje přesunu souběžných neuspořádaný sady `_Uset`.  
  
##  <a name="count"></a>počet 

 Spočítá počet elementů odpovídající zadaného klíče. Tato funkce je bezpečné souběžnosti.  
  
```
size_type count(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Klíč k vyhledání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet opakování, kolikrát se zobrazí klíč v kontejneru.  
  
##  <a name="empty"></a>prázdný 

 Zkouší, zda nejsou přítomny žádné prvky. Tato metoda je bezpečné souběžnosti.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je prázdný, kontejneru souběžných `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Případě souběžných vložení, jestli je prázdný souběžných kontejneru se může změnit ihned po volání této funkce, než je návratovou hodnotu i pro čtení.  
  
##  <a name="end"></a>end 

 Vrátí iterator odkazující na umístění posledním prvkem v kontejneru souběžných úspěšné. Tato metoda je bezpečné souběžnosti.  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor do umístění posledním prvkem v kontejneru souběžných úspěšné.  
  
##  <a name="equal_range"></a>equal_range – 

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
 A [pár](http://msdn.microsoft.com/en-us/32e72d66-3020-4cb9-92c3-f7a5fa7998ff) kde první prvek je iterátor na začátku a druhý prvkem je iterátor na konec rozsahu.  
  
### <a name="remarks"></a>Poznámky  
 Je možné pro souběžných vloží způsobí další klíče má být vložen po begin iterator a před end iterator.  
  
##  <a name="find"></a>Najít 

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
  
##  <a name="get_allocator"></a>get_allocator – 

 Vrací objekt allocator uložené pro tento souběžných kontejner. Tato metoda je bezpečné souběžnosti.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt allocator uložené pro tento souběžných kontejner.  
  
##  <a name="hash_function"></a>hash_function – 

 Vrátí objekt funkce uložené hodnoty hash.  
  
```
hasher hash_function() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt funkce uložené hodnoty hash.  
  
##  <a name="insert"></a>Vložení 

 Přidá elementy na `concurrent_unordered_set` objektu.  
  
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
 Typ hodnoty vložit do sady.  
  
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
  
##  <a name="key_eq"></a>key_eq – 

 Vrátí objekt funkce porovnání rovnosti uložené.  
  
```
key_equal key_eq() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt funkce porovnání rovnosti uložené.  
  
##  <a name="load_factor"></a>load_factor – 

 Vypočítá a vrátí aktuální zatížení Multi-Factor kontejneru. Koeficient zatížení je počet elementů v kontejneru rozdělené podle počtu kbelíků.  
  
```
float load_factor() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Koeficient zatížení kontejneru.  
  
##  <a name="max_load_factor"></a>max_load_factor – 

 Získá nebo nastaví maximální zatížení faktor kontejneru. Maximální zatížení faktor je největší počet prvků, než může být v žádné sady než kontejneru zvětšování jeho interní tabulku.  
  
```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```  
  
### <a name="parameters"></a>Parametry  
 `_Newmax`  
  
### <a name="return-value"></a>Návratová hodnota  
 První člen funkce vrátí Multi-Factor uložené maximální zatížení. Druhý členská funkce nevrací hodnotu, ale vyvolá [out_of_range](../../../standard-library/out-of-range-class.md) výjimka, pokud zadaná zatížení faktor je neplatný...  
  
##  <a name="max_size"></a>max_size – 

 Vrátí maximální velikost souběžných kontejneru, určit pomocí přidělujícího modulu. Tato metoda je bezpečné souběžnosti.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální počet prvků, které lze vložit do tohoto souběžných kontejneru.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota horní mez může být ve skutečnosti vyšší, než co kontejneru ve skutečnosti pojme.  
  
##  <a name="operator_eq"></a>operátor = 

 Přiřadí obsah jiného `concurrent_unordered_set` k tomuto objektu. Tato metoda není bezpečná souběžnosti.  
  
```
concurrent_unordered_set& operator= (const concurrent_unordered_set& _Uset);

concurrent_unordered_set& operator= (concurrent_unordered_set&& _Uset);
```  
  
### <a name="parameters"></a>Parametry  
 `_Uset`  
 Zdroj `concurrent_unordered_set` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `concurrent_unordered_set` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Po vymazání existující elementy v sadě souběžných neuspořádaný `operator=` buď kopíruje nebo přesouvá obsah `_Uset` do souběžných neuspořádané sady.  
  
##  <a name="rehash"></a>rehash – 

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
  
##  <a name="size"></a>velikost 

 Vrátí počet prvků v tomto souběžných kontejneru. Tato metoda je bezpečné souběžnosti.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v kontejneru.  
  
### <a name="remarks"></a>Poznámky  
 Případě souběžných vložení může změnit počet elementů v kontejneru souběžných ihned po volání této funkce, než je návratovou hodnotu i pro čtení.  
  
##  <a name="swap"></a>swap 

 Prohození obsahu dvou `concurrent_unordered_set` objekty. Tato metoda není bezpečná souběžnosti.  
  
```
void swap(concurrent_unordered_set& _Uset);
```  
  
### <a name="parameters"></a>Parametry  
 `_Uset`  
 `concurrent_unordered_set` Objekt, který chcete Prohodit s.  
  
##  <a name="unsafe_begin"></a>unsafe_begin – 

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
  
##  <a name="unsafe_bucket"></a>unsafe_bucket – 

 Vrátí index sady, který konkrétního klíče mapy v tomto kontejneru.  
  
```
size_type unsafe_bucket(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parametry  
 `KVal`  
 Klíč elementu, který se hledají.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index sady pro klíč v tomto kontejneru.  
  
##  <a name="unsafe_bucket_count"></a>unsafe_bucket_count – 

 Vrátí aktuální počet intervalů, v tomto kontejneru.  
  
```
size_type unsafe_bucket_count() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální počet intervalů, v tomto kontejneru.  
  
##  <a name="unsafe_bucket_size"></a>unsafe_bucket_size – 

 Vrátí počet položek v konkrétní sady tohoto kontejneru.  
  
```
size_type unsafe_bucket_size(size_type _Bucket);
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 V bloku k vyhledání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální počet intervalů, v tomto kontejneru.  
  
##  <a name="unsafe_cbegin"></a>unsafe_cbegin – 

 Vrátí první prvek v tomto kontejneru pro konkrétní sady iterace.  
  
```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 Bucket index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace odkazující na začátku bloku.  
  
##  <a name="unsafe_cend"></a>unsafe_cend 

 Vrátí iterator do umístění úspěšné posledním prvkem v konkrétní sady.  
  
```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Bucket`  
 Bucket index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace odkazující na začátku bloku.  
  
##  <a name="unsafe_end"></a>unsafe_end – 

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
  
##  <a name="unsafe_erase"></a>unsafe_erase – 

 Odebere elementy z `concurrent_unordered_set` v zadaných pozic. Tato metoda není bezpečná souběžnosti.  
  
```
iterator unsafe_erase(
    const_iterator _Where);

size_type unsafe_erase(
    const key_type& KVal);

iterator unsafe_erase(
    const_iterator first,
    const_iterator last);
```  
  
### <a name="parameters"></a>Parametry  
 `_Where`  
 Iterator pozice vymazat z.  
  
 `KVal`  
 Hodnota klíče vymazat.  
  
 `first`  
 `last`  
  
### <a name="return-value"></a>Návratová hodnota  
 První dva členské funkce vrátí iterátor, který označí první prvek zbývající nad rámec všechny elementy odebrán, nebo [end](#end)(), pokud neexistuje žádný takový prvek. Třetí členská funkce vrátí počet prvků, které se odeberou.  
  
### <a name="remarks"></a>Poznámky  
 Odebere první členská funkce elementu, na kterou odkazuje `_Where`. Druhý členská funkce odebere elementy v rozsahu [ `_Begin`, `_End`).  
  
 Třetí členská funkce odebere elementy v rozsahu oddělená [equal_range –](#equal_range)(KVal).  
  
##  <a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count – 

 Vrátí maximální počet intervalů, v tomto kontejneru.  
  
```
size_type unsafe_max_bucket_count() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální počet intervalů, v tomto kontejneru.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md)



