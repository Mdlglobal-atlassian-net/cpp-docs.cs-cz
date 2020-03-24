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
ms.openlocfilehash: 55c870263fdf6bd96cf8a137308adb329866c9e5
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150664"
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

\ *přidělování*
Uložený objekt přidělování, který zapouzdřuje podrobnosti o forward_list přidělování a navracení paměti. Tento parametr je volitelný. Výchozí hodnota je přidělování <`Type`>.

## <a name="remarks"></a>Poznámky

Objekt `forward_list` přiděluje a uvolňuje úložiště pro sekvenci, kterou ovládá, pomocí uloženého objektu *přidělování* tříd, který je založen na [třídě přidělování](../standard-library/allocator-class.md) (obvykle se označuje jako `std::allocator)`. Další informace najdete v tématu [přidělování](../standard-library/allocators.md). Objekt přidělování musí mít stejné externí rozhraní jako objekt typu `allocator`.

> [!NOTE]
> Uložený objekt přidělování není zkopírován při přiřazení objektu kontejneru.

Iterátory, ukazatele a odkazy mohou být neplatné, pokud jsou prvky své řízené sekvence vymazány prostřednictvím `forward_list`. Vložení a spojení prováděná na řízené sekvenci prostřednictvím `forward_list` neprovádí neplatnost iterátorů.

K sestavování řízené sekvence může dojít voláním [forward_list:: insert_after](#insert_after), což je jediná členská funkce, která volá `Type(const  T&)`konstruktoru. `forward_list` mohou také volat konstruktory Move. Pokud takový výraz vyvolá výjimku, objekt kontejneru vloží žádné nové prvky a znovu vyvolá výjimku. Proto objekt typu `forward_list` je ponechán ve známém stavu, když dojde k takovým výjimkám.

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
|[iterátor](#iterator)|Typ, který poskytuje iterátor pro seznam pro dopředek.|
|[ukazatele](#pointer)|Typ, který poskytuje ukazatel na prvek v seznamu pro dopředný seznam.|
|[odkaz](#reference)|Typ, který poskytuje odkaz na prvek v seznamu pro dopředný seznam.|
|[size_type](#size_type)|Typ, který představuje vzdálenost bez znaménka mezi dvěma prvky.|
|[value_type](#value_type)|Typ, který představuje typ elementu uložený v seznamu pro dopředný seznam.|

### <a name="functions"></a>Functions

|||
|-|-|
|[řadit](#assign)|Vymaže prvky ze seznamu před a zkopíruje novou sadu prvků do cílového seznamu pro seznam.|
|[before_begin](#before_begin)|Vrátí iterátor adresující pozici před prvním prvkem v seznamu pro dopředný seznam.|
|[ifunctiondiscovery](#begin)|Vrátí iterátor adresující první prvek v seznamu pro dopředný seznam.|
|[cbefore_begin](#cbefore_begin)|Vrátí konstantní iterátor adresující pozici před prvním prvkem v seznamu pro dopředný seznam.|
|[cbegin](#cbegin)|Vrátí konstantní iterátor adresující první prvek v seznamu pro dopředný seznam.|
|[cend](#cend)|Vrátí konstantní iterátor, který adresuje umístění následující po posledním prvku v seznamu pro dopředný seznam.|
|[jejich](#clear)|Smaže všechny prvky seznamu dopředných.|
|[emplace_after](#emplace_after)|Přesune konstrukce nový prvek po zadané pozici.|
|[emplace_front](#emplace_front)|Přidá prvek konstruovaný na začátek seznamu.|
|[obsahovat](#empty)|Testuje, zda je seznam předaných je prázdný.|
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
|[adresu](#swap)|Vyměňuje prvky dvou seznamů pro přeposílání.|
|[unique](#unique)|Odebere sousední prvky, které přejdou na zadaný test.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_eq)|Nahradí prvky seznamu pro dopředek kopií jiného seznamu pro příjem.|

## <a name="allocator_type"></a><a name="allocator_type"></a>allocator_type

Typ, který představuje třídu přidělování pro objekt dopředný seznam.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

`allocator_type` je synonymum pro přidělování parametrů šablony.

## <a name="assign"></a><a name="assign"></a>řadit

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

*poslední*\
Konec rozsahu nahrazení.

*počet*\
Počet prvků, které se mají přiřadit.

\ *Val*
Hodnota, kterou chcete přiřadit každému elementu.

*Zadejte*\
Typ hodnoty

\ *IList*
Initializer_list ke zkopírování.

### <a name="remarks"></a>Poznámky

Pokud forward_list je celočíselný typ, První členská funkce se chová stejně jako `assign((size_type)First, (Type)Last)`. V opačném případě první členská funkce nahradí sekvenci řízenou `*this` sekvencí [`First, Last)`, která nesmí překrývat počáteční řízenou sekvenci.

Druhá členská funkce nahradí sekvenci řízenou `*this` s opakováním `Count` prvků `Val`hodnoty.

Třetí členská funkce zkopíruje prvky initializer_list do forward_list.

## <a name="before_begin"></a><a name="before_begin"></a>before_begin

Vrátí iterátor adresující pozici před prvním prvkem v seznamu pro dopředný seznam.

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který ukazuje těsně před první prvek sekvence (nebo těsně před koncem prázdné sekvence).

### <a name="remarks"></a>Poznámky

## <a name="begin"></a><a name="begin"></a>ifunctiondiscovery

Vrátí iterátor adresující první prvek v seznamu pro dopředný seznam.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který odkazuje na první prvek sekvence (nebo těsně za konec prázdné sekvence).

### <a name="remarks"></a>Poznámky

## <a name="cbefore_begin"></a><a name="cbefore_begin"></a>cbefore_begin

Vrátí konstantní iterátor adresující pozici před prvním prvkem v seznamu pro dopředný seznam.

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který ukazuje těsně před první prvek sekvence (nebo těsně před koncem prázdné sekvence).

### <a name="remarks"></a>Poznámky

## <a name="cbegin"></a><a name="cbegin"></a>cbegin

Vrátí **konstantní** iterátor, který adresuje první prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro dopředný přístup **const** , který odkazuje na první prvek rozsahu nebo umístění hned za konec prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

### <a name="remarks"></a>Poznámky

S návratovou hodnotou `cbegin`nelze upravovat elementy v rozsahu.

Tuto členskou funkci lze použít místo `begin()` členské funkce pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s klíčovým slovem srážky typu [auto](../cpp/auto-cpp.md) , jak je znázorněno v následujícím příkladu. V příkladu zvažte `Container` jako upravitelný kontejner ( **nekonstantní**) libovolného druhu, který podporuje `begin()` a `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a>cend

Vrátí **konstantní** iterátor, který adresuje umístění hned za poslední prvek v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor pro dopředný přístup, který ukazuje přesně za konec rozsahu.

### <a name="remarks"></a>Poznámky

`cend` slouží k otestování, zda iterátor prošl na konci rozsahu.

Tuto členskou funkci lze použít místo `end()` členské funkce pro zajištění, že návratová hodnota je `const_iterator`. Obvykle se používá ve spojení s klíčovým slovem srážky typu [auto](../cpp/auto-cpp.md) , jak je znázorněno v následujícím příkladu. V příkladu zvažte `Container` jako upravitelný kontejner ( **nekonstantní**) libovolného druhu, který podporuje `end()` a `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Hodnota vrácená `cend` by neměla být zpětně odkazovaná.

## <a name="clear"></a><a name="clear"></a>jejich

Smaže všechny prvky seznamu dopředných.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce volá `erase_after(before_begin(), end()).`.

## <a name="const_iterator"></a><a name="const_iterator"></a>const_iterator

Typ, který poskytuje konstantní iterátor pro seznam pro dopředek.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

`const_iterator` popisuje objekt, který může sloužit jako konstantní dopředný iterátor pro řízenou sekvenci. Je zde popsána jako synonymum pro implementaci definovaný typ.

## <a name="const_pointer"></a><a name="const_pointer"></a>const_pointer

Typ, který poskytuje ukazatel na prvek **const** v seznamu pro dopředný seznam.

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>Poznámky

## <a name="const_reference"></a><a name="const_reference"></a>const_reference

Typ, který poskytuje konstantní odkaz na prvek v seznamu pro dopředný seznam.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

## <a name="difference_type"></a><a name="difference_type"></a>difference_type

Typ se znaménkem typu Integer, který lze použít k reprezentaci počtu prvků v dopředných seznamech v rozsahu mezi prvky, na které odkazují iterátory.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

`difference_type` popisuje objekt, který může představovat rozdíl mezi adresami všech dvou prvků v řízené sekvenci.

## <a name="emplace_after"></a><a name="emplace_after"></a>emplace_after

Přesune konstrukce nový prvek po zadané pozici.

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>Parametry

*Kde*\
Pozice v seznamu cíle předek, kde je vytvořen nový prvek.

\ *Val*
Argument konstruktoru.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který označuje nově vložený element.

### <a name="remarks"></a>Poznámky

Tato členská funkce vloží element s argumenty konstruktoru *Val* hned za element, na který ukazuje, *kde* v řízené sekvenci. Jeho chování je jinak stejné jako [forward_list:: insert_after](#insert_after).

## <a name="emplace_front"></a><a name="emplace_front"></a>emplace_front

Přidá prvek konstruovaný na začátek seznamu.

```cpp
template <class Type>
    void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

\ *Val*
Prvek přidaný na začátek seznamu pro dopředný seznam.

### <a name="remarks"></a>Poznámky

Tato členská funkce vloží element s argumenty konstruktoru `_ val` na konci řízené sekvence.

Pokud je vyvolána výjimka, kontejner zůstane beze změny a výjimka je znovu vyvolána.

## <a name="empty"></a><a name="empty"></a>obsahovat

Testuje, zda je seznam předaných je prázdný.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam předek prázdný; v opačném případě **false**.

## <a name="end"></a><a name="end"></a>účelu

Vrátí iterátor, který adresuje umístění následující po posledním prvku v seznamu pro dopředný seznam.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který ukazuje hned za konec sekvence.

## <a name="erase_after"></a><a name="erase_after"></a>erase_after

Odebere prvky ze seznamu předek po zadané pozici.

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>Parametry

*Kde*\
Pozice v seznamu cíle předek, kde je prvek smazán.

*první*\
Začátek rozsahu, který chcete vymazat.

*poslední*\
Konec rozsahu, který se má vymazat

### <a name="return-value"></a>Návratová hodnota

Iterátor, který určuje první prvek zbývající za odebranými prvky, nebo [forward_list:: end](#end) , pokud žádný takový prvek neexistuje.

### <a name="remarks"></a>Poznámky

První členská funkce odstraní prvek kontrolované sekvence hned za *WHERE*.

Druhá členská funkce odstraní prvky řízené sekvence v rozsahu `( first,  last)` (ani není součástí koncového bodu).

Mazání `N` prvků způsobuje volání destruktoru `N`. Dojde k [přerozdělení](../standard-library/forward-list-class.md) , takže iterátory a odkazy se stanou pro vymazané prvky neplatné.

Členské funkce nikdy nevyvolají výjimku.

## <a name="forward_list"></a><a name="forward_list"></a>forward_list

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

*Al*\
Třída alokátoru, která se má použít s tímto objektem.

*Počet*\
Počet prvků v seznamu sestavených.

\ *Val*
Hodnota prvků v seznamu sestavena.

*Pravé*\
Seznam, ze kterého se má sestavený seznam kopírovat

*První*\
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*Poslední*\
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

\ *IList*
Initializer_list ke zkopírování.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají [přidělování](../standard-library/allocator-class.md) a inicializují řízenou sekvenci. Objekt přidělování je argument *Al*, pokud je k dispozici. Pro kopírovací konstruktor je `right.get_allocator()`. V opačném případě je `Allocator()`.

První dva konstruktory určují prázdnou počáteční sekvenci řízenou.

Třetí konstruktor určuje opakování *počtu prvků `Type()`* hodnoty.

Čtvrtý a pátý konstruktor určuje opakování *počtu prvků Value* *Val*.

Šestý konstruktor určuje kopii sekvence řízenou *vpravo*. Pokud `InputIterator` je celočíselný typ, další dva konstruktory určují opakování `(size_type)First` prvků `(Type)Last`hodnoty. V opačném případě následující dva konstruktory určují `[First, Last)`sekvence.

Deváté a desáté konstruktory jsou stejné jako šest, ale s odkazem [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) .

Poslední konstruktor určuje počáteční řízenou sekvenci s objektem třídy `initializer_list<Type>`.

## <a name="front"></a><a name="front"></a>dopředu

Vrátí odkaz na první prvek v seznamu pro dopředné.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na první prvek řízené sekvence, který nesmí být prázdný.

## <a name="get_allocator"></a><a name="get_allocator"></a>get_allocator

Vrátí kopii objektu přidělování, která se používá k vytvoření seznamu pro seznam.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt [přidělování](../standard-library/allocator-class.md) .

## <a name="insert_after"></a><a name="insert_after"></a>insert_after

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

*Kde*\
Pozice v seznamu cílové dopřed, kde je vložen první prvek.

*Počet*\
Počet prvků, které mají být vloženy.

*První*\
Začátek rozsahu vložení

*Poslední*\
Konec rozsahu vložení

\ *Val*
Prvek přidaný do seznamu pro dopředné.

\ *IList*
Initializer_list pro vložení.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který označuje nově vložený element (pouze první a poslední členská funkce).

### <a name="remarks"></a>Poznámky

Každá z členských funkcí vkládá – hned za element, na který ukazuje, *kde* v kontrolované sekvenci – sekvence, která je určena zbývajícími operandy.

První členská funkce vloží prvek, který má hodnotu *Val* a vrátí iterátor, který určí nově vložený element.

Druhá členská funkce vloží opakování *počtu prvků Value* *Val*.

Pokud `InputIterator` je celočíselný typ, třetí členská funkce se chová stejně jako `insert(it, (size_type)First, (Type)Last)`. V opačném případě vloží `[First, Last)`sekvence, která nesmí překrývat počáteční řízenou sekvenci.

Čtvrtá členská funkce vloží sekvenci, která je určena objektem třídy `initializer_list<Type>`.

Poslední členská funkce je stejná jako první, ale s odkazem [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) .

Vložení prvků `N` způsobí volání konstruktoru `N`. Dojde k [přerozdělení](../standard-library/forward-list-class.md) , ale žádné iterátory nebo odkazy se stanou neplatnými.

Pokud je vyvolána výjimka během vkládání jednoho nebo více prvků, kontejner zůstane nezměněn a výjimka je znovu vyvolána.

## <a name="iterator"></a><a name="iterator"></a>iterátor

Typ, který poskytuje iterátor pro seznam pro dopředek.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

`iterator` popisuje objekt, který může sloužit jako dopředný iterátor pro řízenou sekvenci. Je zde popsána jako synonymum pro implementaci definovaný typ.

## <a name="max_size"></a><a name="max_size"></a>max_size

Vrátí maximální délku seznamu předávaných nahoru.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka nejdelší sekvence, kterou může objekt ovládat.

### <a name="remarks"></a>Poznámky

## <a name="merge"></a><a name="merge"></a>sloučení

Kombinuje dvě seřazené sekvence do jedné seřazené sekvence v lineárním čase. Odebere prvky ze seznamu argumentů a vloží je do tohoto `forward_list`. Tyto dva seznamy by měly být seřazené podle stejného objektu Compare Function před voláním `merge`. Kombinovaný seznam bude seřazen podle objektu funkce Compare.

```cpp
void merge(forward_list& right);
template <class Predicate>
    void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>Parametry

*pravé*\
Seznam pro přeposílání, ze kterého se mají sloučit

\ *comp*
Objekt funkce Compare, který se používá k řazení prvků.

### <a name="remarks"></a>Poznámky

`forward_list::merge` odstraní prvky z `right``forward_list` a vloží je do tohoto `forward_list`. Obě sekvence musí být seřazeny stejným predikátem, popsaným níže. Kombinované pořadí je také řazeno pomocí objektu Compare Function.

Pro iterátory `Pi` a `Pj` určení prvků na pozicích `i` a `j`první členská funkce ukládá pořadí `!(*Pj < *Pi)` vždy, když `i < j`. (Prvky jsou seřazené v pořadí `ascending`.) Druhá členská funkce ukládá pořadí `! comp(*Pj, *Pi)` vždy, když `i < j`.

V výsledné řízené sekvenci nejsou vráceny žádné páry prvků v původní řízené sekvenci. Pokud dvojice prvků v výsledné kontrolované sekvenci porovná EQUAL (`!(*Pi < *Pj) && !(*Pj < *Pi)`), zobrazí se prvek z původní kontrolované sekvence před prvkem řízeným pomocí `right`.

Výjimka je vyvolána pouze v případě, že `comp` vyvolá výjimku. V takovém případě je řízená sekvence ponechána v nespecifikovaném pořadí a výjimka je znovu vyvolána.

## <a name="operator"></a><a name="op_eq"></a>operátor =

Nahradí prvky seznamu pro dopředek kopií jiného seznamu pro příjem.

```cpp
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Seznam pro dopředné kopírování do seznamu pro příjem

\ *IList*
Seznam inicializátorů uzavřený ve složených závorkách, který se chová stejně jako sekvence prvků typu `Type`.

### <a name="remarks"></a>Poznámky

První operátor členu nahradí řízenou sekvenci kopií řízené sekvence *napravo*.

Druhý členský operátor nahradí řízená sekvence z objektu třídy `initializer_list<Type>`.

Třetí členský operátor je stejný jako první, ale s odkazem [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) .

## <a name="pointer"></a><a name="pointer"></a>ukazatele

Typ, který poskytuje ukazatel na prvek v seznamu pro dopředný seznam.

```cpp
typedef typename Allocator::pointer pointer;
```

## <a name="pop_front"></a><a name="pop_front"></a>pop_front

Odstraní prvek na začátku dopředný seznam.

```cpp
void pop_front();
```

### <a name="remarks"></a>Poznámky

První prvek seznamu pro dopředný seznam nesmí být prázdný.

Členská funkce nikdy nevyvolává výjimku.

## <a name="push_front"></a><a name="push_front"></a>push_front

Přidá prvek na začátek seznamu pro dopředný seznam.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

\ *Val*
Prvek přidaný na začátek seznamu pro dopředný seznam.

### <a name="remarks"></a>Poznámky

Pokud je vyvolána výjimka, kontejner zůstane beze změny a výjimka je znovu vyvolána.

## <a name="reference"></a><a name="reference"></a>odkaz

Typ, který poskytuje odkaz na prvek v seznamu pro dopředný seznam.

```cpp
typedef typename Allocator::reference reference;
```

## <a name="remove"></a><a name="remove"></a>odebrány

Vymaže prvky v seznamu dopředných položek, které odpovídají zadané hodnotě.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parametry

\ *Val*
Hodnota, která, pokud je držena prvkem, bude mít za následek odebrání tohoto elementu ze seznamu.

### <a name="remarks"></a>Poznámky

Členská funkce odebere z řízených sekvencí všechny prvky určené `P`iterátoru, pro které `*P ==  val`.

Členská funkce nikdy nevyvolává výjimku.

## <a name="remove_if"></a><a name="remove_if"></a>remove_if

Vymaže prvky ze seznamu dopředných, pro který je splněn zadaný predikát.

```cpp
template <class Predicate>
    void remove_if(Predicate pred);
```

### <a name="parameters"></a>Parametry

*před*\
Unární predikát, který je-li splněn prvkem, vede k odstranění tohoto prvku ze seznamu.

### <a name="remarks"></a>Poznámky

Členská funkce se odebere z řízených sekvencí všechny prvky určené `P`iterátoru, pro které `pred(*P)` má hodnotu true.

K výjimce dojde pouze v případě, že *před* vyvolá výjimku. V takovém případě je řízená sekvence ponechána v nespecifikovaném stavu a výjimka je znovu vyvolána.

## <a name="resize"></a><a name="resize"></a>velikost

Určuje novou velikost seznamu dopředných.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>Parametry

*_Newsize*\
Počet prvků v seznamu pro dopředné velikosti

\ *Val*
Hodnota, která má být použita pro odsazení.

### <a name="remarks"></a>Poznámky

Členské funkce zajistí, že počet prvků v seznamu je po *_Newsize*. Je-li nutné řídit sekvenci déle, První členská funkce připojí prvky s hodnotou `Type()`, zatímco druhá členská funkce připojí prvky s hodnotou *Val*. Chcete-li nastavit kratší sekvenci, oba členské funkce efektivně volají `erase_after(begin() + _Newsize - 1, end())`.

## <a name="reverse"></a><a name="reverse"></a>zpět

Obrátí pořadí, ve kterém se prvky vyskytují v seznamu dopředného vyhledávání.

```cpp
void reverse();
```

## <a name="size_type"></a><a name="size_type"></a>size_type

Typ, který představuje vzdálenost bez znaménka mezi dvěma prvky.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ unsigned integer popisuje objekt, který může představovat délku kontrolované sekvence.

## <a name="sort"></a><a name="sort"></a>druhu

Uspořádá elementy ve vzestupném pořadí nebo s objednávkou určenou predikátem.

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>Parametry

*před*\
Predikát řazení.

### <a name="remarks"></a>Poznámky

Oba členské funkce sestavují elementy v řízené sekvenci pomocí predikátu, který je popsán níže.

Pro iterátory `Pi` a `Pj` určení prvků na pozicích `i` a `j`první členská funkce ukládá pořadí `!(*Pj < *Pi)` vždy, když `i < j`. (Prvky jsou seřazené v pořadí `ascending`.) Funkce šablony člena ukládá pořadí `! pred(*Pj, *Pi)` vždy, když `i < j`. V výsledné řízené sekvenci jsou vráceny žádné seřazené páry prvků v původní řízené sekvenci. (Řazení je stabilní.)

K výjimce dojde pouze v případě, že *před* vyvolá výjimku. V takovém případě je řízená sekvence ponechána v nespecifikovaném pořadí a výjimka je znovu vyvolána.

## <a name="splice_after"></a><a name="splice_after"></a>splice_after

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

*Kde*\
Pozice v cíli forward_list, po které se má vložit.

\ *zdroje*
Zdrojový forward_list, který má být vložen do cílového forward_list.

\ *ITER*
Prvek, který má být vložen ze zdrojového forward_list.

*První*\
První prvek v rozsahu, který má být vložen ze zdrojového forward_list.

*Poslední*\
První pozice mimo rozsah, který má být vložen ze zdrojového forward_list.

### <a name="remarks"></a>Poznámky

První pár členských funkcí vloží sekvenci řízenou *zdrojem* hned za prvkem v řízené sekvenci, na kterou ukazuje, *kde*. Také odebere všechny prvky ze *zdroje*. ( **`&Source` se nesmí rovnat.** )

Druhá dvojice členských funkcí odstraní element přímo po *iterě* v sekvenci řízené *zdrojem* a vloží jej hned za prvek v řízené sekvenci, na který ukazuje, *kde*. (Pokud `Where == Iter || Where == ++Iter`, nedojde k žádné změně.)

Třetí pár členských funkcí (spojování s rozsahem) vloží dílčí rozsah určený `(First, Last)` z sekvence řízené *zdrojem* hned za prvkem v řízené sekvenci, na který ukazuje, *kde*. Také odstraní původní dílčí rozsah z sekvence řízené *zdrojem*. (Pokud `&Source == this`, rozsah `(First, Last)` nesmí obsahovat element, na který odkazuje, *kde*.)

Pokud se v rámci rozsahu spojování vloží `N` prvky a `&Source != this`, je objekt [iterátoru](#iterator) třídy zvýšený `N` časy.

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

## <a name="swap"></a><a name="swap"></a>adresu

Vyměňuje prvky dvou seznamů pro přeposílání.

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Seznam pro předávání, který poskytuje prvky, které mají být vyměněny.

### <a name="remarks"></a>Poznámky

Členská funkce přemění kontrolované sekvence mezi `*this` a *pravou*. Pokud je `get_allocator() ==  right.get_allocator()`, tak v konstantním čase nevyvolává žádné výjimky a neověřuje žádné odkazy, ukazatele nebo iterátory, které určují elementy ve dvou řízených sekvencích. V opačném případě provede několik přiřazení prvků a volání konstruktoru v poměru k počtu prvků ve dvou řízených sekvencích.

## <a name="unique"></a><a name="unique"></a>tabulka

Eliminuje všechny kromě prvního prvku ze všech po sobě jdoucích skupin stejných prvků.

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

\ *comp*
Binární predikát, který slouží k porovnání po sobě jdoucích prvků.

### <a name="remarks"></a>Poznámky

Zachová první z každého jedinečného prvku a odstraní zbytek. Elementy musí být seřazeny tak, aby prvky stejné hodnoty byly sousedící v seznamu.

První členská funkce se odebere ze kontrolované sekvence každý prvek, který porovnává stejnou hodnotu jako předchozí prvek. Pro iterátory `Pi` a `Pj` určení prvků na pozicích `i` a `j`, druhá členská funkce odebere všechny prvky, pro které `i + 1 == j &&  comp(*Pi, *Pj)`.

Pro řízenou sekvenci Length `N` (> 0) je predikát `comp(*Pi, *Pj)` vyhodnocen `N - 1` časů.

Výjimka je vyvolána pouze v případě, že `comp` vyvolá výjimku. V takovém případě je řízená sekvence ponechána v nespecifikovaném stavu a výjimka je znovu vyvolána.

## <a name="value_type"></a><a name="value_type"></a>value_type

Typ, který představuje typ elementu uložený v seznamu pro dopředný seznam.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Type`.
