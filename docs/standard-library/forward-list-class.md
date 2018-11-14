---
title: forward_list – třída
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::forward_list
- forward_list/std::forward_list::allocator_type
- forward_list/std::forward_list::const_iterator
- forward_list/std::forward_list::const_pointer
- forward_list/std::forward_list::const_reference
- forward_list/std::forward_list::difference_type
- forward_list/std::forward_list::iterator
- forward_list/std::forward_list::pointer
- forward_list/std::forward_list::reference
- forward_list/std::forward_list::size_type
- forward_list/std::forward_list::value_type
- forward_list/std::forward_list::assign
- forward_list/std::forward_list::before_begin
- forward_list/std::forward_list::begin
- forward_list/std::forward_list::cbefore_begin
- forward_list/std::forward_list::cbegin
- forward_list/std::forward_list::cend
- forward_list/std::forward_list::clear
- forward_list/std::forward_list::emplace_after
- forward_list/std::forward_list::emplace_front
- forward_list/std::forward_list::empty
- forward_list/std::forward_list::end
- forward_list/std::forward_list::erase_after
- forward_list/std::forward_list::front
- forward_list/std::forward_list::get_allocator
- forward_list/std::forward_list::insert_after
- forward_list/std::forward_list::max_size
- forward_list/std::forward_list::merge
- forward_list/std::forward_list::pop_front
- forward_list/std::forward_list::push_front
- forward_list/std::forward_list::remove
- forward_list/std::forward_list::remove_if
- forward_list/std::forward_list::resize
- forward_list/std::forward_list::reverse
- forward_list/std::forward_list::sort
- forward_list/std::forward_list::splice_after
- forward_list/std::forward_list::swap
- forward_list/std::forward_list::unique
helpviewer_keywords:
- std::forward_list
- std::forward_list::allocator_type
- std::forward_list::const_iterator
- std::forward_list::const_pointer
- std::forward_list::const_reference
- std::forward_list::difference_type
- std::forward_list::iterator
- std::forward_list::pointer
- std::forward_list::reference
- std::forward_list::size_type
- std::forward_list::value_type
- std::forward_list::assign
- std::forward_list::before_begin
- std::forward_list::begin
- std::forward_list::cbefore_begin
- std::forward_list::cbegin
- std::forward_list::cend
- std::forward_list::clear
- std::forward_list::emplace_after
- std::forward_list::emplace_front
- std::forward_list::empty
- std::forward_list::end
- std::forward_list::erase_after
- std::forward_list::front
- std::forward_list::get_allocator
- std::forward_list::insert_after
- std::forward_list::max_size
- std::forward_list::merge
- std::forward_list::pop_front
- std::forward_list::push_front
- std::forward_list::remove
- std::forward_list::remove_if
- std::forward_list::resize
- std::forward_list::reverse
- std::forward_list::sort
- std::forward_list::splice_after
- std::forward_list::swap
- std::forward_list::unique
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
ms.openlocfilehash: 5eaa8eba1904dc0a729fb66b280b8d3fa4bb78f1
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524544"
---
# <a name="forwardlist-class"></a>forward_list – třída

Popisuje objekt, který řídí různé délky sekvence elementů. Sekvence se ukládá jako jednotlivě propojený seznam uzlů, každá obsahuje člen typu `Type`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type,
    class Allocator = allocator<Type>>
class forward_list
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Typ*|Typ dat prvku, který bude uložen do forward_list –.|
|*Allocator –*|Uložený objekt alokátoru, který zapouzdřuje informace o forward_list – přidělování a navracení zpět paměti. Tento parametr je volitelný. Výchozí hodnota je allocator < `Type`>.|

## <a name="remarks"></a>Poznámky

A `forward_list` objekt přiděluje a uvolňuje úložiště pro sekvenci řídí, prostřednictvím uloženého objektu třídy *alokátoru* , který je založen na [Allocator – třída](../standard-library/allocator-class.md) (obvykle označuje jako `std::allocator)`. Další informace najdete v tématu [Alokátorů](../standard-library/allocators.md). Objekt alokátoru musí mít stejné externí rozhraní jako objekt třídy šablony `allocator`.

> [!NOTE]
> Uložený objekt alokátoru není zkopírován při přiřazení objektu kontejneru.

Iterátory, ukazatele a reference může být neplatný při jejich řízenou sekvenci prvků měrných prostřednictvím `forward_list`. Vložení a zapletení prováděny v řízené sekvenci prostřednictvím `forward_list` nečiní iterátory.

Doplňky řízené sekvence může dojít k voláním [forward_list::insert_after](#insert_after), což je pouze členskou funkci, která volá konstruktor `Type(const  T&)`. `forward_list` může také volání konstruktorů přesunutí. Pokud takový výraz vyvolá výjimku, kontejneru objekt vloží žádné nové prvky a vyvolá výjimku znovu. Proto objekt třídy šablony `forward_list` zbývá do známého stavu, když dojde k takové výjimky.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[forward_list –](#forward_list)|Vytvoří objekt typu `forward_list`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje třídu alokátoru pro objekt dopředu seznamu.|
|[const_iterator](#const_iterator)|Typ, který poskytuje konstantní iterátor pro dopředný seznamu.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na **const** prvek v seznamu vpřed.|
|[const_reference](#const_reference)|Typ, který poskytuje konstantní odkaz na prvek v seznamu vpřed.|
|[difference_type](#difference_type)|Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků seznam dopředu v rozsahu mezi prvky, na které odkazují iterátory.|
|[iterátor](#iterator)|Typ, který poskytuje iterátor pro dopředný seznamu.|
|[Ukazatel](#pointer)|Typ, který poskytuje ukazatel na prvek v seznamu vpřed.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek v seznamu vpřed.|
|[size_type](#size_type)|Typ, který představuje vzdálenosti bez znaménka mezi dvěma prvky.|
|[value_type](#value_type)|Typ, který představuje typ prvků uložených v dopředné seznamu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[přiřazení](#assign)|Odstraní prvky ze seznamu dopředné a zkopíruje novou sadu prvků do cílového seznamu vpřed.|
|[before_begin –](#before_begin)|Vrátí iterátor adresující umístění před první prvek v dopředné seznamu.|
|[začít](#begin)|Vrátí iterátor adresující první prvek v dopředné seznamu.|
|[cbefore_begin](#cbefore_begin)|Vrátí konstantní iterátor adresující umístění před první prvek v dopředné seznamu.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek v dopředné seznamu.|
|[cend](#cend)|Vrátí konstantní iterátor adresující umístění následující po posledním prvku v dopředné seznamu.|
|[Vymazat](#clear)|Vymaže všechny prvky dopředné seznamu.|
|[emplace_after –](#emplace_after)|Přesunutí vytvoří nový prvek po do zadané pozice.|
|[emplace_front –](#emplace_front)|Přidá prvek vytvořený v místě na začátek seznamu.|
|[prázdný](#empty)|Ověřuje, zda přesměrování seznam je prázdný.|
|[ukončení](#end)|Vrátí iterátor adresující umístění následující po posledním prvku v dopředné seznamu.|
|[erase_after](#erase_after)|Odebere prvky ze seznamu přesměrování po do zadané pozice.|
|[Přední](#front)|Vrátí odkaz na první prvek v dopředné seznamu.|
|[get_allocator](#get_allocator)|Vrátí kopii přidělování objektu používanou k vytvoření seznamu vpřed.|
|[insert_after](#insert_after)|Přidá prvky do seznamu přesměrování po do zadané pozice.|
|[max_size](#max_size)|Vrátí maximální délku dopředné seznamu.|
|[sloučení](#merge)|Odebere prvky ze seznamu argumentů, vloží do cílového seznamu dopředné a řadí nové, kombinované sadu elementů ve vzestupném pořadí nebo v jiných určeném pořadí.|
|[pop_front](#pop_front)|Odstraní prvek na začátku seznamu vpřed.|
|[push_front](#push_front)|Přidá prvek na začátku seznamu vpřed.|
|[remove](#remove)|Odstraní prvky v dopředné seznamu, který odpovídá zadané hodnotě.|
|[remove_if](#remove_if)|Odstraní prvky z seznam vpřed, pro kterou zadaný predikát uspokojen.|
|[Změna velikosti](#resize)|Určuje novou velikost seznamu vpřed.|
|[reverzní](#reverse)|Obrátí pořadí, ve kterém se prvky objevují v dopředné seznamu.|
|[Řazení](#sort)|Uspořádá prvky ve vzestupném pořadí nebo pořadí určeném predikátem.|
|[splice_after](#splice_after)|Restitches propojení mezi uzly.|
|[Prohození](#swap)|Vymění prvky dvou seznamů vpřed.|
|[unique](#unique)|Odebere sousedící prvky, které předávají zadaný testovací.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Nahradí prvky seznamu dopředné kopii jiného seznamu vpřed.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<forward_list – >

**Namespace:** std

## <a name="allocator_type"></a>  forward_list::allocator_type

Typ, který představuje třídu alokátoru pro objekt dopředu seznamu.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro parametr šablony alokátoru.

## <a name="assign"></a>  forward_list::Assign

Odstraní prvky ze seznamu dopředné a zkopíruje novou sadu prvků do cílového seznamu vpřed.

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign(
    initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*první*|Začátek rozsahu nahrazení.|
|*poslední*|Konec rozsahu nahrazení.|
|*Počet*|Počet prvků, které mají přiřadit.|
|*Val*|Hodnota pro přiřazení jednotlivých prvků.|
|*Typ*|Typ hodnoty.|
|* IList.|Objekt initializer_list ke kopírování.|

### <a name="remarks"></a>Poznámky

Pokud forward_list – je celočíselný typ, první členská funkce se chová stejně jako `assign((size_type)First, (Type)Last)`. V opačném případě první členská funkce nahrazuje sekvence řízenou parametrem `*this` s pořadím [ `First, Last)`, která se nesmí překrývat počáteční řízené sekvence.

Druhá členská funkce se nahradí sekvence řízenou parametrem `*this` s opakování `Count` prvků hodnoty `Val`.

Třetí členská funkce zkopíruje do forward_list – prvků objekt initializer_list.

## <a name="before_begin"></a>  forward_list::before_begin

Vrátí iterátor adresující umístění před první prvek v dopředné seznamu.

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který odkazuje těsně před první prvek pořadí (nebo pouze do konce prázdná sekvence).

### <a name="remarks"></a>Poznámky

## <a name="begin"></a>  forward_list::begin

Vrátí iterátor adresující první prvek v dopředné seznamu.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který ukazuje na první prvek v pořadí (nebo hned za konec prázdná sekvence).

### <a name="remarks"></a>Poznámky

## <a name="cbefore_begin"></a>  forward_list::cbefore_begin

Vrátí konstantní iterátor adresující umístění před první prvek v dopředné seznamu.

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který odkazuje těsně před první prvek pořadí (nebo pouze do konce prázdná sekvence).

### <a name="remarks"></a>Poznámky

## <a name="cbegin"></a>  forward_list::cbegin

Vrátí **const** iterátor adresující první prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

A **const** iterátor pro dopředný přístup, který ukazuje na první prvek rozsahu nebo na umístění hned za koncem prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`, nejde upravit prvky v rozsahu.

Můžete použít tuto členskou funkci místo `begin()` členskou funkci pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) zadejte klíčovým slovem odvození, jak je znázorněno v následujícím příkladu. V tomto příkladu zvažte `Container` jako upravitelný (jinou hodnotu než **const**) kontejner jakéhokoli druhu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  forward_list::cend

Vrátí **const** iterátor adresující umístění hned za posledním prvkem v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro dopředný přístup, který ukazuje přesně za konec rozsahu.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, zda iterátor prošel konec rozsahu.

Můžete použít tuto členskou funkci místo `end()` členskou funkci pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) zadejte klíčovým slovem odvození, jak je znázorněno v následujícím příkladu. V tomto příkladu zvažte `Container` jako upravitelný (jinou hodnotu než **const**) kontejner jakéhokoli druhu, který podporuje `end()` a `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Hodnota vrácená `cend` by neměla být dereferencována.

## <a name="clear"></a>  forward_list::clear

Vymaže všechny prvky dopředné seznamu.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce volání `erase_after(before_begin(), end()).`

## <a name="const_iterator"></a>  forward_list::const_iterator

Typ, který poskytuje konstantní iterátor pro dopředný seznamu.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

`const_iterator` Popisuje objekt, který může sloužit jako konstantní dopředného iterátoru řízené sekvence. Je popsán jako synonymum pro implementací definovaný typ. zde.

## <a name="const_pointer"></a>  forward_list::const_pointer

Typ, který poskytuje ukazatel na **const** prvek v seznamu vpřed.

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>Poznámky

## <a name="const_reference"></a>  forward_list::const_reference

Typ, který poskytuje konstantní odkaz na prvek v seznamu vpřed.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

## <a name="difference_type"></a>  forward_list::difference_type

Celočíselný typ se znaménkem, který slouží k vyjádření počtu prvků seznam dopředu v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` Popisuje objekt, který může představovat rozdíl mezi adresami dva prvky řízené sekvence.

## <a name="emplace_after"></a>  forward_list::emplace_after

Přesunutí vytvoří nový prvek po do zadané pozice.

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*kde*|Pozice v dopředné seznamu cílů, kde je vytvořen nový prvek.|
|*Val*|Argument konstruktoru.|

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje nově vložený prvek.

### <a name="remarks"></a>Poznámky

Tato členská funkce vloží prvek s argumenty konstruktoru *val* bezprostředně po elementu, na které odkazuje *kde* v řízené sekvenci. Její chování je jinak stejné jako [forward_list::insert_after](#insert_after).

## <a name="emplace_front"></a>  forward_list::emplace_front

Přidá prvek vytvořený v místě na začátek seznamu.

```cpp
template <class Type>
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Val*|Element přidá na začátek seznamu vpřed.|

### <a name="remarks"></a>Poznámky

Tato členská funkce vloží prvek s argumenty konstruktoru `_ val` na konci řízené sekvence.

Pokud je vyvolána výjimka, kontejner zůstane beze změny a je znovu vyvolána výjimka.

## <a name="empty"></a>  forward_list::Empty

Ověřuje, zda přesměrování seznam je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud dopředné seznam je prázdný; v opačném případě **false**.

## <a name="end"></a>  forward_list::end

Vrátí iterátor adresující umístění následující po posledním prvku v dopředné seznamu.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který ukazuje přesně za konec sekvence.

## <a name="erase_after"></a>  forward_list::erase_after

Odebere prvky ze seznamu přesměrování po do zadané pozice.

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*kde*|Pozice v cílovém seznamu vpřed ve kterém se vymažou elementu.|
|*první*|Začátek rozsahu, který chcete vymazat.|
|*poslední*|Konec rozsahu, který chcete vymazat.|

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek zbývající za všemi odstraněnými prvky, nebo [forward_list::end](#end) Pokud žádný takový prvek neexistuje.

### <a name="remarks"></a>Poznámky

První členská funkce odebere elementu řízené sekvenci hned za *kde*.

Druhá členská funkce odebere prvky řízené sekvence v rozsahu `( first,  last)` (ani koncový bod je součástí).

Mazání `N` způsobí, že prvky `N` volání destruktoru. [Realokace](../standard-library/forward-list-class.md) tak iterátory a odkazy zneplatní mazání prvků.

Členské funkce nikdy nevyvolají výjimku.

## <a name="forward_list"></a>  forward_list::forward_list

Vytvoří objekt typu `forward_list`.

```cpp
forward_list();
explicit forward_list(const Allocator& Al);
explicit forward_list(size_type Count);
forward_list(size_type Count, const Type& Val);
forward_list(size_type Count, const Type& Val, const Allocator& Al);
forward_list(const forward_list& Right);
forward_list(const forward_list& Right, const Allocator& Al);
forward_list(forward_list&& Right);
forward_list(forward_list&& Right, const Allocator& Al);
forward_list(initializer_list<Type> IList, const Alloc& Al);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Al*|Třída alokátoru, která se má použít s tímto objektem.|
|*Počet*|Počet prvků v sestaveném seznamu.|
|*Val*|Hodnota prvků ve vytvořeném seznamu.|
|*doprava*|Seznam, jehož vyrobený seznam je kopií.|
|*první*|Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.|
|*poslední*|Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.|
|*IList*|Objekt initializer_list ke kopírování.|

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají [alokátoru](../standard-library/allocator-class.md) a inicializovat řízené sekvence. Objekt alokátoru je argument *Al*, pokud jsou k dispozici. Pro konstruktor kopie je ` right.get_allocator()`. V opačném případě je `Allocator()`.

První dva konstruktory určují prázdný počáteční řízené sekvence.

Třetí konstruktor určuje opakování *počet* prvků hodnoty `Type()`.

Čtvrtý a pátý konstruktor určuje opakování *počet* prvků hodnoty *Val*.

Šestý konstruktor určuje kopii sekvence řízenou parametrem *vpravo*. Pokud `InputIterator` je celočíselný typ, následující dva konstruktory určují opakování `(size_type)First` prvků hodnoty `(Type)Last`. V opačném případě zadejte následující dva konstruktory pořadí `[First, Last)`.

Devátý a desátý konstruktor jsou stejné jako šestý, ale s [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) odkaz.

Poslední konstruktor Určuje počáteční řízené sekvence s objektem třídy `initializer_list<Type>`.

## <a name="front"></a>  forward_list::front

Vrátí odkaz na první prvek v dopředné seznamu.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na první prvek řízené sekvence, která musí být neprázdný.

## <a name="get_allocator"></a>  forward_list::get_allocator

Vrátí kopii přidělování objektu používanou k vytvoření seznamu vpřed.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený [alokátoru](../standard-library/allocator-class.md) objektu.

## <a name="insert_after"></a>  forward_list::insert_after

Přidá prvky do seznamu přesměrování po do zadané pozice.

```cpp
iterator insert_after(const_iterator Where, const Type& Val);
void insert_after(const_iterator Where, size_type Count, const Type& Val);
void insert_after(const iterator Where, initializer_list<Type> IList);
iterator insert_after(const_iterator Where, Type&& Val);
template <class InputIterator>
void insert_after(const_iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*kde*|Pozice v cílovém seznamu dopředné vloženy první prvek.|
|*Počet*|Počet elementů k vložení.|
|*první*|Začátek rozsahu vložení.|
|*poslední*|Konec rozsahu vložení.|
|*Val*|Prvek přidán do seznamu vpřed.|
|*IList*|Objekt initializer_list pro vložení.|

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje nově vložený prvek (pouze první a poslední členské funkce).

### <a name="remarks"></a>Poznámky

Každý člen funkce vloží – pouze po elementu, na které odkazuje *kde* v řízené sekvenci – sekvenci, která "určené zbývající operandy.

První členská funkce vloží prvek, který má hodnotu *Val* a vrátí iterátor, který určuje nově vložený prvek.

Druhá členská funkce vloží opakování *počet* prvků hodnoty *Val*.

Pokud `InputIterator` je celočíselný typ, třetí členská funkce se chová stejně jako `insert(it, (size_type)First, (Type)Last)`. V opačném případě vloží sekvenci `[First, Last)`, která se nesmí překrývat počáteční řízené sekvence.

Čtvrtá členská funkce vloží sekvenci, která je určená objekt třídy `initializer_list<Type>`.

Poslední členská funkce je stejná jako první, ale s [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) odkaz.

Vkládání `N` způsobí, že prvky `N` volá konstruktor. [Realokace](../standard-library/forward-list-class.md) dojde, ale žádné iterátory nebo odkazy zneplatní.

Pokud dojde k výjimce při vložení jedné nebo víc elementů kontejneru je beze změny doleva a je znovu vyvolána výjimka.

## <a name="iterator"></a>  forward_list::iterator

Typ, který poskytuje iterátor pro dopředný seznamu.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

`iterator` Popisuje objekt, který může sloužit jako dopředného iterátoru řízené sekvence. Je popsán jako synonymum pro implementací definovaný typ. zde.

## <a name="max_size"></a>  forward_list::max_size

Vrátí maximální délku dopředné seznamu.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Délky nejdelší sekvenci, která můžete řídit objektu.

### <a name="remarks"></a>Poznámky

## <a name="merge"></a>  forward_list::merge

Kombinuje dvě seřazená sekvence do jednoho seřazeného sekvence v lineárním čase. Odstraní prvky ze seznamu argumentů a vloží je do této `forward_list`. Dva seznamy mají být řazeny podle stejného objektu funkce porovnání před voláním `merge`. Kombinovaný seznam budou seřazeny podle, která porovná objekt funkce.

```cpp
void merge(forward_list& right);
template <class Predicate>
void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|Dopředné seznamu sloučit z.|
|*Kompozice*|Objekt funkce porovnání, která slouží k seřazení prvků.|

### <a name="remarks"></a>Poznámky

`forward_list::merge` Odebere prvky z `forward_list` `right`a vloží je do této `forward_list`. Obě sekvence musí provést řazení podle stejné predikát je popsáno níže. Kombinované pořadí je také seřazené podle tohoto objektu funkce porovnání.

U iterátorů `Pi` a `Pj` označující prvky v místech `i` a `j`, první členská funkce ukládá pořadí `!(*Pj < *Pi)` pokaždé, když `i < j`. (Prvky jsou seřazeny v `ascending` pořadí.) Druhá členská funkce ukládá pořadí `! comp(*Pj, *Pi)` pokaždé, když `i < j`.

Žádná dvojice prvků v řízené sekvenci původní obrácené ve výsledné řízené sekvence. Pokud dvojici prvků ve výsledné řízené sekvence porovná rovná ( `!(*Pi < *Pj) && !(*Pj < *Pi)`), prvek z původní řízené sekvence se zobrazí před elementem ze sekvence řízenou parametrem `right`.

Pouze tehdy, pokud dojde k výjimce `comp` vyvolá výjimku. V takovém případě řízené sekvence zůstane v nespecifikovaném pořadí a je znovu vyvolána výjimka.

## <a name="op_eq"></a>  forward_list::Operator =

Nahradí prvky seznamu dopředné kopii jiného seznamu vpřed.

```cpp
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|Dopředné seznamu kopírovaná do seznamu vpřed.|
|*IList*|Seznam inicializátorů v závorkách, který se chová stejně jako posloupnost elementy typu `Type`.|

### <a name="remarks"></a>Poznámky

První členský operátor nahradí kopii sekvence řízenou parametrem řízené sekvence *správné*.

Druhý operátor člena nahradí řízenou sekvenci z objektu třídy `initializer_list<Type>`.

Třetí členský operátor je stejný jako první, ale s [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) odkaz.

## <a name="pointer"></a>  forward_list::Pointer

Typ, který poskytuje ukazatel na prvek v seznamu vpřed.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Poznámky

## <a name="pop_front"></a>  forward_list::pop_front

Odstraní prvek na začátku seznamu vpřed.

```cpp
void pop_front();
```

### <a name="remarks"></a>Poznámky

První prvek seznamu přesměrování musí být neprázdný.

Členská funkce nikdy nevyvolá výjimku.

## <a name="push_front"></a>  forward_list::push_front

Přidá prvek na začátku seznamu vpřed.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Val*|Element přidá na začátek seznamu vpřed.|

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, kontejner zůstane beze změny a je znovu vyvolána výjimka.

## <a name="reference"></a>  forward_list::Reference

Typ, který poskytuje odkaz na prvek v seznamu vpřed.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="remarks"></a>Poznámky

## <a name="remove"></a>  forward_list::Remove

Odstraní prvky v dopředné seznamu, který odpovídá zadané hodnotě.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Val*|Hodnota, která pokud je uložena prvkem, způsobí odebrání tohoto prvku ze seznamu.|

### <a name="remarks"></a>Poznámky

Členská funkce odebere z řízené sekvence všechny prvky určené iterátorem `P`, pro kterou `*P ==  val`.

Členská funkce nikdy nevyvolá výjimku.

## <a name="remove_if"></a>  forward_list::remove_if

Odstraní prvky z seznam vpřed, pro kterou zadaný predikát uspokojen.

```cpp
template <class Predicate>
void remove_if(Predicate pred);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Před*|Unární predikát, který pokud uspokojen prvkem, má za následek odstranění tohoto prvku ze seznamu.|

### <a name="remarks"></a>Poznámky

Členská funkce odebere z řízené sekvence všechny prvky určené iterátorem `P`, pro kterou ` pred(*P)` má hodnotu true.

Pouze tehdy, pokud dojde k výjimce *před* vyvolá výjimku. V takovém případě řízené sekvence zůstane ve stavu Nespecifikovaná a je znovu vyvolána výjimka.

## <a name="resize"></a>  forward_list::Resize

Určuje novou velikost seznamu vpřed.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Newsize*|Počet prvků v seznamu změněnou vpřed.|
|*Val*|Hodnota pro odsazení.|

### <a name="remarks"></a>Poznámky

Členské funkce obou zajistěte, aby byl počet prvků v seznamu od nynějška *_Newsize*. Pokud je třeba provést řízené sekvence delší, první členská funkce přidá prvky s hodnotou `Type()`, zatímco druhá členská funkce přidá prvky s hodnotou *val*. Chcete-li řízené sekvence kratší, efektivně i členské funkce volají `erase_after(begin() + _Newsize - 1, end())`.

## <a name="reverse"></a>  forward_list::Reverse

Obrátí pořadí, ve kterém se prvky objevují v dopředné seznamu.

```cpp
void reverse();
```

### <a name="remarks"></a>Poznámky

## <a name="size_type"></a>  forward_list::size_type

Typ, který představuje vzdálenosti bez znaménka mezi dvěma prvky.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ celé číslo bez znaménka, který popisuje objekt, který může představovat délka jakékoli řízené sekvence.

## <a name="sort"></a>  forward_list::sort

Uspořádá prvky ve vzestupném pořadí nebo pořadí určeném predikátem.

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Před*|Predikát pořadí.|

### <a name="remarks"></a>Poznámky

Obě funkce člena seřazení prvků v řízené sekvenci predikátem, je popsáno níže.

U iterátorů `Pi` a `Pj` označující prvky v místech `i` a `j`, první členská funkce ukládá pořadí `!(*Pj < *Pi)` pokaždé, když `i < j`. (Prvky jsou seřazeny v `ascending` pořadí.) Členská funkce šablony, ukládá pořadí `! pred(*Pj, *Pi)` pokaždé, když `i < j`. Žádné seřazený dvojice prvků v řízené sekvenci původní obrácené ve výsledné řízené sekvence. (Je stabilní řazení.)

Pouze tehdy, pokud dojde k výjimce *před* vyvolá výjimku. V takovém případě řízené sekvence zůstane v nespecifikovaném pořadí a je znovu vyvolána výjimka.

## <a name="splice_after"></a>  forward_list::splice_after

Odebere prvky z forward_list – zdroj a vloží je do forward_list – cíl.

```cpp
// insert the entire source forward_list
void splice_after(const_iterator Where, forward_list& Source);
void splice_after(const_iterator Where, forward_list&& Source);

// insert one element of the source forward_list
void splice_after(const_iterator Where, forward_list& Source, const_iterator Iter);
void splice_after(const_iterator Where, forward_list&& Source, const_iterator Iter);

// insert a range of elements from the source forward_list
void splice_after(
    const_iterator Where,
    forward_list& Source,
    const_iterator First,
    const_iterator Last);

void splice_after(
    const_iterator Where,
    forward_list&& Source,
    const_iterator First,
    const_iterator Last);
```

### <a name="parameters"></a>Parametry

*kde*<br/>
Pozice v cílovém forward_list – po kterém se má vložit.

*Zdroj*<br/>
Zdroj forward_list –, který má být vložen do forward_list – cíl.

*ITER*<br/>
Element, který má být vložen z forward_list – zdroj.

*první*<br/>
První prvek v rozsahu, který má být vložen z forward_list – zdroj.

*poslední*<br/>
První pozice mimo rozsah, který má být vložen z forward_list – zdroj.

### <a name="remarks"></a>Poznámky

První pár členských funkcí vloží sekvenci řízené *zdroj* bezprostředně po elementu v řízené sekvenci ukazuje *kde*. Zároveň se tím odebere všechny prvky z *zdroj*. (`&Source` nesmí být stejný jako **to**.)

Druhý pár členské funkce odstraní prvek hned za *Iter* v sekvenci řízené *zdroj* a vloží ho hned po elementu v řízené sekvenci ukazuje *Kde*. (Pokud `Where == Iter || Where == ++Iter`, nedošlo k žádné změně.)

Třetí pár členských funkcí (rozsahové spojení) vloží určený dílčí sadu `(First, Last)` ze sekvence řízenou parametrem *zdroj* bezprostředně po elementu v řízené sekvenci ukazuje *kde*. Zároveň se tím odebere původní dílčí sadu ze sekvence řízenou parametrem *zdroj*. (Pokud `&Source == this`, rozsahu `(First, Last)` nesmí obsahovat prvek, na které odkazuje *kde*.)

Pokud ranged spojení se vloží `N` elementy, a `&Source != this`, objekt třídy [iterátoru](#iterator) se zvýší `N` časy.

Žádné iterátory, ukazatele nebo odkazy, které určují prvky spojeného stanou neplatnými.

### <a name="example"></a>Příklad

```cpp
// forward_list_splice_after.cpp
// compile with: /EHsc /W4
#include <forward_list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    forward_list<int> c1{ 10, 11 };
    forward_list<int> c2{ 20, 21, 22 };
    forward_list<int> c3{ 30, 31 };
    forward_list<int> c4{ 40, 41, 42, 43 };

    forward_list<int>::iterator where_iter;
    forward_list<int>::iterator first_iter;
    forward_list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice_after(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice_after(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    c2.splice_after(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = (10) (11)c2 = (20) (21) (22)c3 = (30) (31)c4 = (40) (41) (42) (43)After splicing c1 into c2:c1 =c2 = (20) (21) (10) (11) (22)After splicing the first element of c3 into c2:c3 = (30)c2 = (20) (21) (31) (10) (11) (22)After splicing a range of c4 into c2:c4 = (40) (41)c2 = (20) (21) (42) (43) (31) (10) (11) (22)
```

## <a name="swap"></a>  forward_list::swap

Vymění prvky dvou seznamů vpřed.

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|Dopředné seznam poskytující prvky mají vyměnit.|

### <a name="remarks"></a>Poznámky

Členská funkce Zamění řízené sekvence mezi `*this` a *správné*. Pokud `get_allocator() ==  right.get_allocator()`, provádí se v konstantním času, nevyvolává žádné výjimky a zneplatní žádné odkazy, ukazatele nebo iterátory, které určují prvky v dané dvě řízené sekvence. V opačném případě provede několik element přiřazení a volání konstruktoru je přímo úměrný počtu prvků v dané dvě řízené sekvence.

## <a name="unique"></a>  forward_list::Unique

Vyloučí všechny kromě první prvek z každé skupiny po sobě jdoucích stejných prvků.

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Kompozice*|Binární predikát, který používá k porovnání po sobě jdoucí prvky.|

### <a name="remarks"></a>Poznámky

Udržuje prvního dne každého prvku jedinečný a zbytek odebere. Elementy musí být řada seřazena tak, aby elementy stejné hodnoty vedle sebe v seznamu.

První členská funkce odebere z řízené sekvence každý element, který při porovnání rovna jeho předchozí prvek. U iterátorů `Pi` a `Pj` označující prvky v místech `i` a `j`, druhá členská funkce odebere každý prvek, pro kterou `i + 1 == j &&  comp(*Pi, *Pj)`.

Pro sekvenci řízené délky `N` (> 0), predikát ` comp(*Pi, *Pj)` vyhodnocena `N - 1` časy.

Pouze tehdy, pokud dojde k výjimce `comp` vyvolá výjimku. V takovém případě řízené sekvence zůstane ve stavu Nespecifikovaná a je znovu vyvolána výjimka.

## <a name="value_type"></a>  forward_list::value_type

Typ, který představuje typ prvků uložených v dopředné seznamu.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr _ šablony `Ty`.

## <a name="see-also"></a>Viz také:

[<forward_list>](../standard-library/forward-list.md)<br/>
