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
ms.openlocfilehash: 0e7084f0df15a1adf2124c9c6b8cae63eb12de89
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957037"
---
# <a name="forward_list-class"></a>forward_list – třída

Popisuje objekt, který ovládá proměnlivou délku sekvence prvků. Sekvence je uložena jako samostatně propojený seznam uzlů, z nichž každý obsahuje člena typu `Type`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type,
    class Allocator = allocator<Type>>
class forward_list
```

### <a name="parameters"></a>Parametry

Zadejte * \
Typ dat prvku, který bude uložen v forward_list.

*Dělující*\
Uložený objekt přidělování, který zapouzdřuje informace o přidělování forward_list a navracení paměti. Tento parametr je volitelný. Výchozí hodnota je přidělování <`Type`>.

## <a name="remarks"></a>Poznámky

Objekt přiděluje a uvolňuje úložiště pro sekvenci, kterou ovládá, pomocí uloženého objektu *přidělování* tříd, který je založen na [třídě přidělování](../standard-library/allocator-class.md) (obvykle se `std::allocator)`označuje jako. `forward_list` Další informace najdete v tématu [přidělování](../standard-library/allocators.md). Objekt přidělování musí mít stejné externí rozhraní jako objekt třídy `allocator`šablony.

> [!NOTE]
> Uložený objekt přidělování není zkopírován při přiřazení objektu kontejneru.

Iterátory, ukazatele a odkazy mohou být neplatné, pokud se prvky jejich řízené sekvence vymažou pomocí `forward_list`. Vložení a spojení prováděná na řízené sekvenci prostřednictvím `forward_list` neověřuje iterátory.

K sestavování řízené sekvence může dojít voláním [forward_list:: insert_after](#insert_after), což je jediná členská funkce, která volá konstruktor `Type(const  T&)`. `forward_list`mohou také volat konstruktory Move. Pokud takový výraz vyvolá výjimku, objekt kontejneru vloží žádné nové prvky a znovu vyvolá výjimku. Proto objekt třídy `forward_list` šablony je ponechán ve známém stavu, když dojde k takovým výjimkám.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[forward_list](#forward_list)|Vytvoří objekt typu `forward_list`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Typ, který představuje třídu přidělování pro objekt dopředný seznam.|
|[const_iterator](#const_iterator)|Typ, který poskytuje konstantní iterátor pro seznam pro dopředek.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na prvek **const** v seznamu pro dopředný seznam.|
|[const_reference](#const_reference)|Typ, který poskytuje konstantní odkaz na prvek v seznamu pro dopředný seznam.|
|[difference_type](#difference_type)|Typ se znaménkem typu Integer, který lze použít k reprezentaci počtu prvků v dopředných seznamech v rozsahu mezi prvky, na které odkazují iterátory.|
|[iterator](#iterator)|Typ, který poskytuje iterátor pro seznam pro dopředek.|
|[pointer](#pointer)|Typ, který poskytuje ukazatel na prvek v seznamu pro dopředný seznam.|
|[Referenční dokumentace](#reference)|Typ, který poskytuje odkaz na prvek v seznamu pro dopředný seznam.|
|[size_type](#size_type)|Typ, který představuje vzdálenost bez znaménka mezi dvěma prvky.|
|[value_type](#value_type)|Typ, který představuje typ elementu uložený v seznamu pro dopředný seznam.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[assign](#assign)|Vymaže prvky ze seznamu před a zkopíruje novou sadu prvků do cílového seznamu pro seznam.|
|[before_begin](#before_begin)|Vrátí iterátor adresující pozici před prvním prvkem v seznamu pro dopředný seznam.|
|[ifunctiondiscovery](#begin)|Vrátí iterátor adresující první prvek v seznamu pro dopředný seznam.|
|[cbefore_begin](#cbefore_begin)|Vrátí konstantní iterátor adresující pozici před prvním prvkem v seznamu pro dopředný seznam.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek v seznamu pro dopředný seznam.|
|[cend](#cend)|Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v seznamu pro dopředný seznam.|
|[jejich](#clear)|Smaže všechny prvky seznamu dopředných.|
|[emplace_after](#emplace_after)|Přesune konstrukce nový prvek po zadané pozici.|
|[emplace_front](#emplace_front)|Přidá prvek konstruovaný na začátek seznamu.|
|[empty](#empty)|Testuje, zda je seznam předaných je prázdný.|
|[účelu](#end)|Vrátí iterátor, který adresuje umístění následující po posledním prvku v seznamu pro dopředný seznam.|
|[erase_after](#erase_after)|Odebere prvky ze seznamu předek po zadané pozici.|
|[dopředu](#front)|Vrátí odkaz na první prvek v seznamu pro dopředné.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu přidělování, která se používá k vytvoření seznamu pro seznam.|
|[insert_after](#insert_after)|Přidá prvky do seznamu předek po zadané pozici.|
|[max_size](#max_size)|Vrátí maximální délku seznamu předávaných nahoru.|
|[sloučení](#merge)|Odebere prvky ze seznamu argumentů, vloží je do cílového seznamu pro odeslání a seřadí nové kombinované sady elementů ve vzestupném pořadí nebo v některém jiném určeném pořadí.|
|[pop_front](#pop_front)|Odstraní prvek na začátku dopředný seznam.|
|[push_front](#push_front)|Přidá prvek na začátek seznamu pro dopředný seznam.|
|[remove](#remove)|Vymaže prvky v seznamu dopředných položek, které odpovídají zadané hodnotě.|
|[remove_if](#remove_if)|Vymaže prvky ze seznamu dopředných, pro který je splněn zadaný predikát.|
|[velikost](#resize)|Určuje novou velikost seznamu dopředných.|
|[zpět](#reverse)|Obrátí pořadí, ve kterém se prvky vyskytují v seznamu dopředného vyhledávání.|
|[druhu](#sort)|Uspořádá elementy ve vzestupném pořadí nebo s objednávkou určenou predikátem.|
|[splice_after](#splice_after)|Znovu spojí propojení mezi uzly.|
|[swap](#swap)|Vyměňuje prvky dvou seznamů pro přeposílání.|
|[unique](#unique)|Odebere sousední prvky, které přejdou na zadaný test.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_eq)|Nahradí prvky seznamu pro dopředek kopií jiného seznamu pro příjem.|

## <a name="allocator_type"></a>allocator_type

Typ, který představuje třídu přidělování pro objekt dopředný seznam.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type`je synonymem pro přidělování parametrů šablony.

## <a name="assign"></a>řadit

Vymaže prvky ze seznamu před a zkopíruje novou sadu prvků do cílového seznamu pro seznam.

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

*první*\
Začátek rozsahu nahrazení.

*posledního*\
Konec rozsahu nahrazení.

*výpočtu*\
Počet prvků, které se mají přiřadit.

*počítává*\
Hodnota, kterou chcete přiřadit každému elementu.

*Textový*\
Typ hodnoty.

*IList*\
Initializer_list, který se má zkopírovat

### <a name="remarks"></a>Poznámky

Pokud je forward_list typu Integer, První členská funkce se chová stejně jako `assign((size_type)First, (Type)Last)`. V opačném případě první členská funkce nahradí sekvenci `*this` řízenou sekvencí `First, Last)`[, která nesmí překrývat počáteční řízenou sekvenci.

Druhá členská funkce nahradí sekvenci řízenou `*this` `Count` opakováním prvků hodnoty `Val`.

Třetí členská funkce zkopíruje prvky initializer_list do forward_list.

## <a name="before_begin"></a>before_begin

Vrátí iterátor adresující pozici před prvním prvkem v seznamu pro dopředný seznam.

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který ukazuje těsně před první prvek sekvence (nebo těsně před koncem prázdné sekvence).

### <a name="remarks"></a>Poznámky

## <a name="begin"></a>ifunctiondiscovery

Vrátí iterátor adresující první prvek v seznamu pro dopředný seznam.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který odkazuje na první prvek sekvence (nebo těsně za konec prázdné sekvence).

### <a name="remarks"></a>Poznámky

## <a name="cbefore_begin"></a>cbefore_begin

Vrátí konstantní iterátor adresující pozici před prvním prvkem v seznamu pro dopředný seznam.

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který ukazuje těsně před první prvek sekvence (nebo těsně před koncem prázdné sekvence).

### <a name="remarks"></a>Poznámky

## <a name="cbegin"></a>cbegin

Vrátí **konstantní** iterátor, který adresuje první prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro dopředný přístup const, který odkazuje na první prvek rozsahu nebo umístění hned za konec prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

V případě návratové hodnoty `cbegin`nelze prvky v rozsahu upravovat.

Tuto členskou funkci můžete použít místo `begin()` členské funkce k zajištění, že návratová hodnota je. `const_iterator` Obvykle se používá ve spojení s klíčovým slovem srážky typu [auto](../cpp/auto-cpp.md) , jak je znázorněno v následujícím příkladu. `Container` V příkladu zvažte, že se jedná o upravitelný kontejner (nekonstantní) jakýkoli druh, kterýpodporuje `begin()` a. `cbegin()`

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

Vrátí **konstantní** iterátor, který adresuje umístění hned za poslední prvek v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro dopředný přístup, který ukazuje přesně za konec rozsahu.

### <a name="remarks"></a>Poznámky

`cend`slouží k otestování, zda iterátor prošl na konci rozsahu.

Tuto členskou funkci můžete použít místo `end()` členské funkce k zajištění, že návratová hodnota je. `const_iterator` Obvykle se používá ve spojení s klíčovým slovem srážky typu [auto](../cpp/auto-cpp.md) , jak je znázorněno v následujícím příkladu. `Container` V příkladu zvažte, že se jedná o upravitelný kontejner (nekonstantní) jakýkoli druh, kterýpodporuje `end()` a. `cend()`

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Hodnota vrácená `cend` by neměla být zpětně odkazovaná.

## <a name="clear"></a>jejich

Smaže všechny prvky seznamu dopředných.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce volá`erase_after(before_begin(), end()).`

## <a name="const_iterator"></a>const_iterator

Typ, který poskytuje konstantní iterátor pro seznam pro dopředek.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

`const_iterator`popisuje objekt, který může sloužit jako konstanta dopředný iterátor pro řízenou sekvenci. Je zde popsána jako synonymum pro implementaci definovaný typ.

## <a name="const_pointer"></a>const_pointer

Typ, který poskytuje ukazatel na prvek **const** v seznamu pro dopředný seznam.

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>Poznámky

## <a name="const_reference"></a>const_reference

Typ, který poskytuje konstantní odkaz na prvek v seznamu pro dopředný seznam.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

## <a name="difference_type"></a>difference_type

Typ se znaménkem typu Integer, který lze použít k reprezentaci počtu prvků v dopředných seznamech v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type`popisuje objekt, který může představovat rozdíl mezi adresami všech dvou prvků v řízené sekvenci.

## <a name="emplace_after"></a>emplace_after

Přesune konstrukce nový prvek po zadané pozici.

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>Parametry

*,* \
Pozice v seznamu cíle předek, kde je vytvořen nový prvek.

*počítává*\
Argument konstruktoru.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který označuje nově vložený element.

### <a name="remarks"></a>Poznámky

Tato členská funkce vloží element s argumenty konstruktoru *Val* hned za element, na který ukazuje, *kde* v řízené sekvenci. Jeho chování je jinak stejné jako [forward_list:: insert_after](#insert_after).

## <a name="emplace_front"></a>emplace_front

Přidá prvek konstruovaný na začátek seznamu.

```cpp
template <class Type>
    void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Prvek přidaný na začátek seznamu pro dopředný seznam.

### <a name="remarks"></a>Poznámky

Tato členská funkce vloží prvek s argumenty `_ val` konstruktoru na konci řízené sekvence.

Pokud je vyvolána výjimka, kontejner zůstane beze změny a výjimka je znovu vyvolána.

## <a name="empty"></a>obsahovat

Testuje, zda je seznam předaných je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam předek prázdný; v opačném případě **false**.

## <a name="end"></a>účelu

Vrátí iterátor, který adresuje umístění následující po posledním prvku v seznamu pro dopředný seznam.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který ukazuje hned za konec sekvence.

## <a name="erase_after"></a>erase_after

Odebere prvky ze seznamu předek po zadané pozici.

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>Parametry

*,* \
Pozice v seznamu cíle předek, kde je prvek smazán.

*první*\
Začátek rozsahu, který chcete vymazat.

*posledního*\
Konec rozsahu, který se má vymazat

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek zbývající za odebranými prvky, nebo [forward_list:: end](#end) , pokud žádný takový prvek neexistuje.

### <a name="remarks"></a>Poznámky

První členská funkce odstraní prvek kontrolované sekvence hned za *WHERE*.

Druhá členská funkce odstraní prvky kontrolované sekvence v rozsahu `( first,  last)` (ani není zahrnut koncový bod).

Mazání prvků způsobuje `N` volání destruktoru. `N` [](../standard-library/forward-list-class.md) Dojde k přerozdělení, takže iterátory a odkazy se stanou pro vymazané prvky neplatné.

Členské funkce nikdy nevyvolají výjimku.

## <a name="forward_list"></a>forward_list

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

*VŠ*\
Třída alokátoru, která se má použít s tímto objektem.

*Výpočtu*\
Počet prvků v seznamu sestavených.

*Počítává*\
Hodnota prvků v seznamu sestavena.

*Kliknutím*\
Seznam, ze kterého se má sestavený seznam kopírovat

*První*\
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*Posledního*\
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

*IList*\
Initializer_list, který se má zkopírovat

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají [přidělování](../standard-library/allocator-class.md) a inicializují řízenou sekvenci. Objekt přidělování je argument *Al*, pokud je k dispozici. Pro kopírovací konstruktor je ` right.get_allocator()`to. V opačném případě `Allocator()`je to.

První dva konstruktory určují prázdnou počáteční sekvenci řízenou.

Třetí konstruktor určuje opakování počtu prvků hodnoty. `Type()`

Čtvrtý a pátý konstruktor určuje opakování počtu prvků Value *Val*.

Šestý konstruktor určuje kopii sekvence řízenou *vpravo*. Pokud `InputIterator` je celočíselný typ, další dva konstruktory určují `(size_type)First` opakování prvků hodnoty `(Type)Last`. V opačném případě následující dva konstruktory určují sekvenci `[First, Last)`.

Deváté a desáté konstruktory jsou stejné jako šest, ale s odkazem [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) .

Poslední konstruktor určuje počáteční řízenou sekvenci s objektem třídy `initializer_list<Type>`.

## <a name="front"></a>dopředu

Vrátí odkaz na první prvek v seznamu pro dopředné.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na první prvek řízené sekvence, který nesmí být prázdný.

## <a name="get_allocator"></a>get_allocator

Vrátí kopii objektu přidělování, která se používá k vytvoření seznamu pro seznam.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt [přidělování](../standard-library/allocator-class.md) .

## <a name="insert_after"></a>insert_after

Přidá prvky do seznamu předek po zadané pozici.

```cpp
iterator insert_after(const_iterator Where, const Type& Val);
void insert_after(const_iterator Where, size_type Count, const Type& Val);
void insert_after(const iterator Where, initializer_list<Type> IList);
iterator insert_after(const_iterator Where, Type&& Val);
template <class InputIterator>
    void insert_after(const_iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

*,* \
Pozice v seznamu cílové dopřed, kde je vložen první prvek.

*Výpočtu*\
Počet prvků, které mají být vloženy.

*První*\
Začátek rozsahu vložení

*Posledního*\
Konec rozsahu vložení

*Počítává*\
Prvek přidaný do seznamu pro dopředné.

*IList*\
Initializer_list, který se má vložit

### <a name="return-value"></a>Návratová hodnota

Iterátor, který označuje nově vložený element (pouze první a poslední členská funkce).

### <a name="remarks"></a>Poznámky

Každá z členských funkcí vkládá – hned za element, na který ukazuje, *kde* v kontrolované sekvenci – sekvence, která je určena zbývajícími operandy.

První členská funkce vloží prvek, který má hodnotu *Val* a vrátí iterátor, který určí nově vložený element.

Druhá členská funkce vloží opakování počtu prvků Value *Val*.

Pokud `InputIterator` je celočíselný typ, třetí členská funkce se chová stejně jako `insert(it, (size_type)First, (Type)Last)`. V opačném případě vloží sekvenci `[First, Last)`, která nesmí překrývat počáteční řízenou sekvenci.

Čtvrtá členská funkce vloží sekvenci, která je určena objektem třídy `initializer_list<Type>`.

Poslední členská funkce je stejná jako první, ale s odkazem [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) .

Vložení `N` prvků způsobí `N` volání konstruktoru. [](../standard-library/forward-list-class.md) Dojde k přerozdělení, ale žádné iterátory nebo odkazy se stanou neplatnými.

Pokud je vyvolána výjimka během vkládání jednoho nebo více prvků, kontejner zůstane nezměněn a výjimka je znovu vyvolána.

## <a name="iterator"></a>iterátor

Typ, který poskytuje iterátor pro seznam pro dopředek.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

`iterator`popisuje objekt, který může sloužit jako dopředný iterátor pro řízenou sekvenci. Je zde popsána jako synonymum pro implementaci definovaný typ.

## <a name="max_size"></a>max_size

Vrátí maximální délku seznamu předávaných nahoru.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka nejdelší sekvence, kterou může objekt ovládat.

### <a name="remarks"></a>Poznámky

## <a name="merge"></a>sloučení

Kombinuje dvě seřazené sekvence do jedné seřazené sekvence v lineárním čase. Odebere prvky ze seznamu argumentů a vloží je do tohoto `forward_list`seznamu. Tyto dva seznamy by měly být seřazené podle stejného objektu Compare Function před voláním `merge`. Kombinovaný seznam bude seřazen podle objektu funkce Compare.

```cpp
void merge(forward_list& right);
template <class Predicate>
    void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Seznam pro přeposílání, ze kterého se mají sloučit

*zajištění*\
Objekt funkce Compare, který se používá k řazení prvků.

### <a name="remarks"></a>Poznámky

`forward_list::merge`Odebere prvky z `forward_list` `right`a vloží je do tohoto `forward_list`. Obě sekvence musí být seřazeny stejným predikátem, popsaným níže. Kombinované pořadí je také řazeno pomocí objektu Compare Function.

Pro `Pi` iterátory a `!(*Pj < *Pi)` `j` `i` `Pj` určení prvků na pozicích a první členská funkce ukládá pořadí pokaždé `i < j`. (Elementy jsou seřazeny podle `ascending` pořadí.) Druhá členská funkce ukládá pořadí `! comp(*Pj, *Pi)` pokaždé. `i < j`

V výsledné řízené sekvenci nejsou vráceny žádné páry prvků v původní řízené sekvenci. Pokud dvojice prvků ve výsledné kontrolované sekvenci porovná EQUAL ( `!(*Pi < *Pj) && !(*Pj < *Pi)`), prvek z původní kontrolované sekvence se zobrazí před prvkem řízeným pomocí. `right`

Výjimka je vyvolána pouze v `comp` případě, že vyvolá výjimku. V takovém případě je řízená sekvence ponechána v nespecifikovaném pořadí a výjimka je znovu vyvolána.

## <a name="op_eq"></a>operátor =

Nahradí prvky seznamu pro dopředek kopií jiného seznamu pro příjem.

```cpp
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Seznam pro dopředné kopírování do seznamu pro příjem

*IList*\
Seznam inicializátorů uzavřený ve složených závorkách, který se chová stejně jako sekvence prvků typu `Type`.

### <a name="remarks"></a>Poznámky

První operátor členu nahradí řízenou sekvenci kopií řízené sekvence napravo.

Druhý členský operátor nahradí řízená sekvence z objektu třídy `initializer_list<Type>`.

Třetí členský operátor je stejný jako první, ale s odkazem [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) .

## <a name="pointer"></a>ukazatele

Typ, který poskytuje ukazatel na prvek v seznamu pro dopředný seznam.

```cpp
typedef typename Allocator::pointer pointer;
```

## <a name="pop_front"></a>pop_front

Odstraní prvek na začátku dopředný seznam.

```cpp
void pop_front();
```

### <a name="remarks"></a>Poznámky

První prvek seznamu pro dopředný seznam nesmí být prázdný.

Členská funkce nikdy nevyvolává výjimku.

## <a name="push_front"></a>push_front

Přidá prvek na začátek seznamu pro dopředný seznam.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Prvek přidaný na začátek seznamu pro dopředný seznam.

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, kontejner zůstane beze změny a výjimka je znovu vyvolána.

## <a name="reference"></a>odkaz

Typ, který poskytuje odkaz na prvek v seznamu pro dopředný seznam.

```cpp
typedef typename Allocator::reference reference;
```

## <a name="remove"></a>odebrány

Vymaže prvky v seznamu dopředných položek, které odpovídají zadané hodnotě.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parametry

*počítává*\
Hodnota, která, pokud je držena prvkem, bude mít za následek odebrání tohoto elementu ze seznamu.

### <a name="remarks"></a>Poznámky

Členská funkce se odebere ze kontrolované sekvence všechny prvky určené iterátorem `P`, pro který. `*P ==  val`

Členská funkce nikdy nevyvolává výjimku.

## <a name="remove_if"></a>remove_if

Vymaže prvky ze seznamu dopředných, pro který je splněn zadaný predikát.

```cpp
template <class Predicate>
    void remove_if(Predicate pred);
```

### <a name="parameters"></a>Parametry

*čekání*\
Unární predikát, který je-li splněn prvkem, vede k odstranění tohoto prvku ze seznamu.

### <a name="remarks"></a>Poznámky

Členská funkce se odebere ze kontrolované sekvence všechny prvky určené iterátorem `P`, pro který ` pred(*P)` má hodnotu true.

K výjimce dojde pouze v případě, že *před* vyvolá výjimku. V takovém případě je řízená sekvence ponechána v nespecifikovaném stavu a výjimka je znovu vyvolána.

## <a name="resize"></a>velikost

Určuje novou velikost seznamu dopředných.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>Parametry

*_Newsize*\
Počet prvků v seznamu pro dopředné velikosti

*počítává*\
Hodnota, která má být použita pro odsazení.

### <a name="remarks"></a>Poznámky

Členské funkce zajišťují, aby počet prvků v seznamu byl po *_Newsize*. Pokud musí být řízená sekvence delší, První členská funkce připojí prvky s hodnotou `Type()`, zatímco druhá členská funkce přidá prvky s hodnotou *Val*. Aby se řízená sekvence zkrátila kratší, obě členské funkce si `erase_after(begin() + _Newsize - 1, end())`budou efektivně volat.

## <a name="reverse"></a>zpět

Obrátí pořadí, ve kterém se prvky vyskytují v seznamu dopředného vyhledávání.

```cpp
void reverse();
```

## <a name="size_type"></a>size_type

Typ, který představuje vzdálenost bez znaménka mezi dvěma prvky.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ unsigned integer popisuje objekt, který může představovat délku kontrolované sekvence.

## <a name="sort"></a>druhu

Uspořádá elementy ve vzestupném pořadí nebo s objednávkou určenou predikátem.

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>Parametry

*čekání*\
Predikát řazení.

### <a name="remarks"></a>Poznámky

Oba členské funkce sestavují elementy v řízené sekvenci pomocí predikátu, který je popsán níže.

Pro `Pi` iterátory a `!(*Pj < *Pi)` `j` `i` `Pj` určení prvků na pozicích a první členská funkce ukládá pořadí pokaždé `i < j`. (Elementy jsou seřazeny podle `ascending` pořadí.) Funkce šablony člena ukládá pořadí `! pred(*Pj, *Pi)` vždy, když je to. `i < j` V výsledné řízené sekvenci jsou vráceny žádné seřazené páry prvků v původní řízené sekvenci. (Řazení je stabilní.)

K výjimce dojde pouze v případě, že *před* vyvolá výjimku. V takovém případě je řízená sekvence ponechána v nespecifikovaném pořadí a výjimka je znovu vyvolána.

## <a name="splice_after"></a>splice_after

Odstraní prvky ze zdrojového forward_list a vloží je do cílového forward_list.

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

*,* \
Pozice v cílovém forward_list, po které se má vložit

*Zdrojová*\
Zdrojový forward_list, který má být vložen do cílového forward_list.

*ITER*\
Prvek, který má být vložen ze zdrojového forward_list.

*První*\
První prvek v rozsahu, který má být vložen ze zdrojového forward_list.

*Posledního*\
První pozice mimo rozsah, který má být vložen ze zdrojového forward_listu.

### <a name="remarks"></a>Poznámky

První pár členských funkcí vloží sekvenci řízenou *zdrojem* hned za prvkem v řízené sekvenci, na kterou ukazuje, *kde*. Také odebere všechny prvky ze *zdroje*. (`&Source` nesmí se rovnat.)

Druhá dvojice členských funkcí odstraní element přímo po Iterě v sekvenci řízené *zdrojem* a vloží jej hned za prvek v řízené sekvenci, na který ukazuje, *kde*. (Pokud `Where == Iter || Where == ++Iter`nedojde k žádné změně.)

Třetí pár členských funkcí (spojování s rozsahem) vloží dílčí rozsah určený `(First, Last)` z sekvence řízené *zdrojem* hned za prvkem v řízené sekvenci, na který ukazuje, *kde*. Také odstraní původní dílčí rozsah z sekvence řízené *zdrojem*. (Pokud `&Source == this`, nesmí rozsah `(First, Last)` zahrnovat element, na který ukazuje, *kde*.)

`N` Pokud je přidaný rozsah přidaných prvků, a `&Source != this`, je objekt [iterátoru](#iterator) `N` třídy zvýšen krát.

Žádné iterátory, ukazatele nebo odkazy, které určují přizpůsobitelné prvky, se stanou neplatnými.

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

## <a name="swap"></a>adresu

Vyměňuje prvky dvou seznamů pro přeposílání.

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Seznam pro předávání, který poskytuje prvky, které mají být vyměněny.

### <a name="remarks"></a>Poznámky

Členská funkce přemění kontrolované sekvence mezi `*this` a *vpravo*. Pokud `get_allocator() ==  right.get_allocator()`je to v konstantním čase, nevyvolává žádné výjimky a neověřuje žádné odkazy, ukazatele nebo iterátory, které určují elementy ve dvou řízených sekvencích. V opačném případě provede několik přiřazení prvků a volání konstruktoru v poměru k počtu prvků ve dvou řízených sekvencích.

## <a name="unique"></a>tabulka

Eliminuje všechny kromě prvního prvku ze všech po sobě jdoucích skupin stejných prvků.

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

*zajištění*\
Binární predikát, který slouží k porovnání po sobě jdoucích prvků.

### <a name="remarks"></a>Poznámky

Zachová první z každého jedinečného prvku a odstraní zbytek. Elementy musí být seřazeny tak, aby prvky stejné hodnoty byly sousedící v seznamu.

První členská funkce se odebere ze kontrolované sekvence každý prvek, který porovnává stejnou hodnotu jako předchozí prvek. `Pi` Pro iterátory `i + 1 == j &&  comp(*Pi, *Pj)`a `Pj` určení prvků na pozicích `i` a `j`druhá členská funkce odebere všechny prvky, pro které.

V případě řízené sekvence délky `N` (> 0) je predikát ` comp(*Pi, *Pj)` vyhodnocen jako `N - 1` časy.

Výjimka je vyvolána pouze v `comp` případě, že vyvolá výjimku. V takovém případě je řízená sekvence ponechána v nespecifikovaném stavu a výjimka je znovu vyvolána.

## <a name="value_type"></a>value_type

Typ, který představuje typ elementu uložený v seznamu pro dopředný seznam.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony _ `Ty`.
