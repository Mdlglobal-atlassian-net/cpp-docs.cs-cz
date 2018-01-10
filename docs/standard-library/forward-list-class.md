---
title: "forward_list – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 36354e8b6e6e0c456334caed402a700129b32dae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="forwardlist-class"></a>forward_list – třída
Popisuje objekt, který řídí různých délka pořadí elementů. Pořadí je uloženo jako samostatně propojené seznam uzlů, každá obsahuje člen typu `Type`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Type,   
    class Allocator = allocator<Type>>  
class forward_list   
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Type`|Datový typ elementu k uložení do forward_list –.|  
|`Allocator`|Uložené allocator objekt, který zapouzdřuje informace o přidělení forward_list – a zrušení přidělení paměti. Tento parametr je volitelný. Výchozí hodnota je allocator < `Type`>.|  
  
## <a name="remarks"></a>Poznámky  
 A `forward_list` objekt přiděluje a uvolní úložiště pro pořadí jimi řídí prostřednictvím uložené objektu třídy `Allocator` založený na [allocator – třída](../standard-library/allocator-class.md) (obvykle označuje jako `std::allocator)`. Další informace najdete v tématu [Alokátorů](../standard-library/allocators.md). Allocator objekt musí mít stejné externí rozhraní jako objekt třídy šablony `allocator`.  
  
> [!NOTE]
>  Objekt uložené allocator nezkopíruje, když je přiřazen kontejnerového objektu.  
  
 Iterátory, ukazatelů a odkazy na pokud mohou být neplatná elementy jejich řízené sekvenci jsou vymazány prostřednictvím `forward_list`. Vložení a zapletení provést v řízené sekvenci prostřednictvím `forward_list` cokoli iterátory.  
  
 Doplňky řízené sekvenci může provádí volání [forward_list::insert_after](#insert_after), který je pouze členské funkce, která volá konstruktor `Type(const  T&)`. `forward_list`může také volání přesunout konstruktory. Pokud takový výraz vyvolá výjimku, objekt kontejneru vloží žádné nové elementy a znovu vyvolá výjimku. Proto objekt třídy šablony `forward_list` je ponechán v známého stavu, když dojde k takové výjimky.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[forward_list –](#forward_list)|Vytvoří objekt typu `forward_list`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type –](#allocator_type)|Typ, který reprezentuje allocator – třída pro objekt dopředného seznamu.|  
|[const_iterator –](#const_iterator)|Typ, který poskytuje konstantní iterator dopředného seznamu.|  
|[const_pointer –](#const_pointer)|Typ, který poskytuje odkazy `const` prvků dopředného seznamu.|  
|[const_reference –](#const_reference)|Typ, který poskytuje konstantní odkaz na element v seznamu předat dál.|  
|[difference_type –](#difference_type)|Typ se znaménkem, který můžete použít k reprezentování počet elementů dopředného seznamu v rozsahu mezi elementy, na kterou iterátory odkazuje.|  
|[iterator](#iterator)|Typ, který poskytuje iterovat dopředného seznamu.|  
|[ukazatele](#pointer)|Typ, který poskytuje ukazatel na element v seznamu předat dál.|  
|[referenční dokumentace](#reference)|Typ, který obsahuje odkaz na element v seznamu předat dál.|  
|[size_type –](#size_type)|Typ, který reprezentuje nepodepsané vzdálenost mezi dvěma prvky.|  
|[value_type](#value_type)|Typ, který představuje typ elementu, které jsou uloženy v seznamu předat dál.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[přiřazení](#assign)|Vymaže elementy ze seznamu dopředného a zkopíruje novou sadu elementů do cílového seznamu předat dál.|  
|[before_begin –](#before_begin)|Vrátí iterator adresování pozice před prvním elementem v seznam předat dál.|  
|[začít](#begin)|Vrátí iterator adresování prvním elementem v seznam předat dál.|  
|[cbefore_begin –](#cbefore_begin)|Vrátí const iterator adresování pozice před prvním elementem v seznam předat dál.|  
|[cbegin –](#cbegin)|Vrátí const iterator adresování prvním elementem v seznam předat dál.|  
|[cend –](#cend)|Vrátí const iterator, která řeší umístění úspěšné posledním prvkem v seznamu předat dál.|  
|[Vymazat](#clear)|Vymaže všechny prvky dopředného seznamu.|  
|[emplace_after –](#emplace_after)|Přesunutí vytvoří nového elementu po konkrétní pozici.|  
|[emplace_front –](#emplace_front)|Přidá element sestavený na místě na začátek seznamu.|  
|[prázdný](#empty)|Ověřuje, zda dopředného seznam je prázdný.|  
|[end](#end)|Vrátí iterátor, který řeší umístění úspěšné posledním prvkem v seznamu předat dál.|  
|[erase_after –](#erase_after)|Odebere elementy ze seznamu dopředného po konkrétní pozici.|  
|[přední](#front)|Vrátí odkaz na první prvek seznamu předat dál.|  
|[get_allocator –](#get_allocator)|Vrátí kopii allocator objekt použitý k vytvoření seznamu předat dál.|  
|[insert_after –](#insert_after)|Přidá elementy do seznamu dopředného po konkrétní pozici.|  
|[max_size –](#max_size)|Vrátí maximální délku seznam předat dál.|  
|[sloučení](#merge)|Odebere ze seznamu argumentů elementy, vloží je do cílového seznamu dopředného a řadí nové, kombinované sadu elementů ve vzestupném pořadí nebo v některých zadaném pořadí.|  
|[pop_front –](#pop_front)|Odstraní prvek na začátek dopředného seznamu.|  
|[push_front –](#push_front)|Přidá prvek na začátek seznamu předat dál.|  
|[remove](#remove)|Vymaže elementy dopředného seznamu, který odpovídá zadané hodnotě.|  
|[remove_if –](#remove_if)|Vymaže elementy dopředného seznamu, pro kterou je splněné zadaným predikátem.|  
|[Změna velikosti](#resize)|Určuje novou velikost dopředného seznam.|  
|[zpětné](#reverse)|Obrátí pořadí, ve kterém elementy objevují v seznamu předat dál.|  
|[řazení](#sort)|Uspořádá elementy ve vzestupném pořadí nebo k pořadí určeného predikátu.|  
|[splice_after –](#splice_after)|Restitches propojení mezi uzly.|  
|[swap](#swap)|Výměny elementy dva seznamy předat dál.|  
|[jedinečné](#unique)|Odebere přiléhající prvky, které předávají testu zadaný.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#op_eq)|Nahradí prvky dopředného seznamu kopii jiného seznamu předat dál.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<forward_list – >  
  
 **Namespace:** – std  
  
##  <a name="allocator_type"></a>forward_list::allocator_type  
 Typ, který reprezentuje allocator – třída pro objekt dopředného seznamu.  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 `allocator_type`je synonymum pro parametr šablony přidělení.  
  
##  <a name="assign"></a>forward_list::Assign  
 Vymaže elementy ze seznamu dopředného a zkopíruje novou sadu elementů do cílového seznamu předat dál.  
  
```  
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
|`first`|Začátek rozsahu nahrazení.|  
|`last`|Konec rozsahu nahrazení.|  
|`count`|Počet elementů přiřadit.|  
|`val`|Hodnota pro přiřazení každý prvek.|  
|`Type`|Typ hodnoty.|  
|`IList`|Initializer_list ke kopírování.|  
  
### <a name="remarks"></a>Poznámky  
 Pokud forward_list – celočíselného typu, první členská funkce se chová stejně jako `assign((size_type)First, (Type)Last)`. Jinak první členská funkce nahradí pořadí řízené `*this` s pořadím [ `First, Last)`, která se nesmí překrývat počáteční řízené sekvenci.  
  
 Druhý členská funkce nahrazuje pořadí řízené `*this` s opakování `Count` elementy hodnoty `Val`.  
  
 Třetí členská funkce zkopíruje elementy initializer_list do forward_list –.  
  
##  <a name="before_begin"></a>forward_list::before_begin  
 Vrátí iterator adresování pozice před prvním elementem v seznam předat dál.  
  
```  
const_iterator before_begin() const;
iterator before_begin();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator předat dál, který odkazuje těsně před první prvek pořadí (nebo těsně před koncem prázdnou sekvencí).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="begin"></a>forward_list::begin  
 Vrátí iterator adresování prvním elementem v seznam předat dál.  
  
```  
const_iterator begin() const;
iterator begin();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator předat dál, která odkazuje na první prvek pořadí (nebo jenom přesahuje za konec prázdnou sekvencí).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="cbefore_begin"></a>forward_list::cbefore_begin  
 Vrátí const iterator adresování pozice před prvním elementem v seznam předat dál.  
  
```  
const_iterator cbefore_begin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator předat dál, který odkazuje těsně před první prvek pořadí (nebo těsně před koncem prázdnou sekvencí).  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="cbegin"></a>forward_list::cbegin  
 Vrátí `const` iterator, která řeší prvním elementem v rozsahu.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `const` iterator předat dál přístup, který odkazuje na první prvek rozsahu nebo umístění právě přesahuje za konec prázdného rozsahu (pro prázdného rozsahu, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Poznámky  
 S návratovou hodnotou `cbegin`, nemůže být upravena elementů v rozsahu.  
  
 Můžete použít tuto funkci člen místě `begin()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `begin()` a `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>forward_list::cend  
 Vrátí `const` iterator, která řeší umístění bezprostředně za posledním prvkem v rozsahu.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor pro dopředný přístup, který ukazuje přesně za konec rozsahu.  
  
### <a name="remarks"></a>Poznámky  
 `cend`slouží k ověření, zda iterovat uplynutí konec její rozsah.  
  
 Můžete použít tuto funkci člen místě `end()` – členská funkce zaručit, že je návratovou hodnotu `const_iterator`. Obvykle se používá ve spojení s [automaticky](../cpp/auto-cpp.md) odvození – klíčové slovo, zadejte, jak je znázorněno v následujícím příkladu. V příkladu, vezměte v úvahu `Container` upravitelná (jinou hodnotu než `const`) kontejneru libovolného typu, který podporuje `end()` a `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 Hodnoty vrácené `cend` by neměl být vyhodnoceny odkazy.  
  
##  <a name="clear"></a>forward_list::clear  
 Vymaže všechny prvky dopředného seznamu.  
  
```  
void clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Volá tento – členská funkce`erase_after(before_begin(), end()).`  
  
##  <a name="const_iterator"></a>forward_list::const_iterator  
 Typ, který poskytuje konstantní iterator dopředného seznamu.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 `const_iterator`Popisuje objekt, který může sloužit jako konstantní dopředného iterator pro řízené sekvenci. Je popsán sem jako synonymum typu definované implementací.  
  
##  <a name="const_pointer"></a>forward_list::const_pointer  
 Typ, který poskytuje odkazy `const` prvků dopředného seznamu.  
  
```  
typedef typename Allocator::const_pointer  
    const_pointer; 
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="const_reference"></a>forward_list::const_reference  
 Typ, který poskytuje konstantní odkaz na element v seznamu předat dál.  
  
```  
typedef typename Allocator::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="difference_type"></a>forward_list::difference_type  
 Typ se znaménkem, který můžete použít k reprezentování počet elementů dopředného seznamu v rozsahu mezi elementy, na kterou iterátory odkazuje.  
  
```  
typedef typename Allocator::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 `difference_type`Popisuje objekt, který může představovat rozdíl mezi dvěma prvky v řízené sekvenci adresy.  
  
##  <a name="emplace_after"></a>forward_list::emplace_after  
 Přesunutí vytvoří nového elementu po konkrétní pozici.  
  
```  
template <class T>  
iterator emplace_after(const_iterator Where, Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Where`|Pozice v seznamu cíl předat dál, kde je vytvořený nového elementu.|  
|`val`|Argument konstruktoru.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator, který určuje nově vloženou elementu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen Vloží element s argumenty konstruktoru `val` pouze po elementu, na kterou odkazuje `Where` v řízené sekvenci. Její chování je jinak stejný jako [forward_list::insert_after](#insert_after).  
  
##  <a name="emplace_front"></a>forward_list::emplace_front  
 Přidá element sestavený na místě na začátek seznamu.  
  
```  
template <class Type>  
void emplace_front(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`val`|Prvek přidán na začátek seznamu předat dál.|  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen Vloží element s argumenty konstruktoru `_ val` na konci řízené sekvenci.  
  
 Pokud je vyvolána výjimka, je ponechán kontejneru v nezměněném stavu a je znovu vyvolány výjimku.  
  
##  <a name="empty"></a>forward_list::Empty  
 Ověřuje, zda dopředného seznam je prázdný.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud dopředného seznam je prázdný; v opačném `false`.  
  
##  <a name="end"></a>forward_list::end  
 Vrátí iterátor, který řeší umístění úspěšné posledním prvkem v seznamu předat dál.  
  
```  
const_iterator end() const;
iterator end();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator předat dál, který odkazuje právě přesahuje za konec sekvenci.  
  
##  <a name="erase_after"></a>forward_list::erase_after  
 Odebere elementy ze seznamu dopředného po konkrétní pozici.  
  
```  
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Where`|Pozice v seznamu cíl předat dál, kde vymazáním elementu.|  
|`first`|Začátek rozsahu vymazat.|  
|`last`|Konec rozsahu vymazat.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor, který označí první prvek zbývající nad rámec všechny elementy odebrán, nebo [forward_list::end](#end) Pokud neexistuje žádný takový prvek.  
  
### <a name="remarks"></a>Poznámky  
 Odebere první členská funkce elementu řízené pořadí právě po `Where`.  
  
 Druhý členská funkce odebere elementy řízené sekvenci v rozsahu `( first,  last)` (ani koncový bod je součástí).  
  
 Vymazání `N` elementy příčiny `N` volání destruktoru. [Opakované přidělení](../standard-library/forward-list-class.md) dojde, takže zneplatní iterátory a reference pro vymazaných elementy.  
  
 Členské funkce nikdy vyvolat výjimku.  
  
##  <a name="forward_list"></a>forward_list::forward_list  
 Vytvoří objekt typu `forward_list`.  
  
```  
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
|`Al`|Třída alokátoru, která se má použít s tímto objektem.|  
|`Count`|Počet elementů v seznamu zkonstruovat.|  
|`Val`|Hodnota elementů v seznamu zkonstruovat.|  
|`Right`|Seznam, které má být kopii seznamu vytvořený.|  
|`First`|Pozice první prvek v rozsahu elementy, které se mají zkopírovat.|  
|`Last`|Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.|  
|`IList`|Initializer_list ke kopírování.|  
  
### <a name="remarks"></a>Poznámky  
 Ukládat všechny konstruktory [allocator](../standard-library/allocator-class.md) a inicializace řízené sekvenci. Je objekt allocator argument `Al`, pokud je k dispozici. Konstruktor copy, je ` right.get_allocator()`. Jinak je `Allocator()`.  
  
 První dva konstruktory zadejte prázdný počáteční řízené sekvenci.  
  
 Třetí konstruktor určuje opakování `Count` elementy hodnoty `Type()`.  
  
 Konstruktory čtvrté a páté zadejte opakování `Count` elementy hodnoty `Val`.  
  
 Šesté konstruktor určuje kopii pořadí řízené `Right`. Pokud `InputIterator` je typ celé číslo, zadejte následující dva konstruktory opakování `(size_type)First` elementy hodnoty `(Type)Last`. Jinak, zadejte následující dva konstruktory pořadí `[First, Last)`.  
  
 Konstruktory deváté a desetinu jsou stejné jako šesté, ale s [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) odkaz.  
  
 Poslední konstruktor Určuje počáteční řízené sekvenci objekt třídy `initializer_list<Type>`.  
  
##  <a name="front"></a>forward_list::front  
 Vrátí odkaz na první prvek seznamu předat dál.  
  
```  
reference front();
const_reference front() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na první prvek řízené sekvenci, která musí být neprázdný.  
  
##  <a name="get_allocator"></a>forward_list::get_allocator  
 Vrátí kopii allocator objekt použitý k vytvoření seznamu předat dál.  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Uložených [allocator](../standard-library/allocator-class.md) objektu.  
  
##  <a name="insert_after"></a>forward_list::insert_after  
 Přidá elementy do seznamu dopředného po konkrétní pozici.  
  
```  
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
|`Where`|Pozice v seznamu cíl dopředného vloženy první prvek.|  
|`Count`|Počet elementů k vložení.|  
|`First`|Začátek rozsahu vložení.|  
|`Last`|Konec rozsahu vložení.|  
|`Val`|Element přidán do seznamu předat dál.|  
|`IList`|Initializer_list vložit.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor, který označuje nově vložený element (pouze první a poslední členské funkce).  
  
### <a name="remarks"></a>Poznámky  
 Každý člen funkce vložení – právě po elementu, na kterou odkazuje `Where` v řízené sekvenci – sekvenci, se určeného zbývající operandy.  
  
 První člen funkce vloží element, který má hodnotu `Val` a vrátí iterátor, který označuje nově vloženou elementu.  
  
 Druhý členská funkce vloží opakování `Count` elementy hodnoty `Val`.  
  
 Pokud `InputIterator` je typ integer třetí členská funkce se chová stejně jako `insert(it, (size_type)First, (Type)Last)`. V opačném pořadí vloží `[First, Last)`, která se nesmí překrývat počáteční řízené sekvenci.  
  
 Čtvrtý – členská funkce vloží sekvenci, která je zadána třída objektu `initializer_list<Type>`.  
  
 Poslední členská funkce je stejný jako první, ale s [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) odkaz.  
  
 Vkládání `N` elementy příčiny `N` volá konstruktor. [Opakované přidělení](../standard-library/forward-list-class.md) dojde, ale žádné iterátory nebo odkazy zneplatní.  
  
 Pokud je vyvolána výjimka při vkládání do jednoho nebo více elementů kontejneru vlevo v nezměněném stavu a je znovu vyvolány výjimku.  
  
##  <a name="iterator"></a>forward_list::iterator  
 Typ, který poskytuje iterovat dopředného seznamu.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 `iterator`Popisuje objekt, který může sloužit jako dopředného iterator pro řízené sekvenci. Je popsán sem jako synonymum typu definované implementací.  
  
##  <a name="max_size"></a>forward_list::max_size  
 Vrátí maximální délku seznam předat dál.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka nejdelší pořadí, které můžete řídit objekt.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="merge"></a>forward_list::merge  
 Kombinuje dvě seřazené posloupnosti do jednoho seřazená posloupnost lineární včas. Odebere elementy ze seznamu argumentů a vloží je do této `forward_list`. Dva seznamy by měl být seřazené podle stejný objekt funkce porovnání před voláním `merge`. Kombinovaná seznamu bude seřadit podle s porovnáním objekt funkce.  
  
```  
void merge(forward_list& right);
template <class Predicate>  
void merge(forward_list& right, Predicate comp);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|Předat dál seznam sloučit z.|  
|`comp`|Objekt porovnat funkce, který slouží k seřazení elementy.|  
  
### <a name="remarks"></a>Poznámky  
 `forward_list::merge`Odebere elementy ze `forward_list` `right`a vloží je do této `forward_list`. Obě pořadí musejí být seřazeny ve stejném predikát popsané dole. Kombinovaná pořadí je také seřazené podle funkce objektu porovnat.  
  
 U iterátorů `Pi` a `Pj` určení prvky v pozic `i` a `j`, první členská funkce ukládá pořadí `!(*Pj < *Pi)` vždy, když `i < j`. (Prvky jsou seřazeny v `ascending` pořadí.) Druhý členská funkce ukládá pořadí `! comp(*Pj, *Pi)` vždy, když `i < j`.  
  
 V výsledné řízené sekvenci se vrátit zpět žádné páry elementů v původní řízené sekvenci. Pokud pár elementů v výsledná řídí pořadí porovná rovna ( `!(*Pi < *Pj) && !(*Pj < *Pi)`), element z původní řízené sekvenci se zobrazuje před element z pořadí řízené `right`.  
  
 Pouze, pokud dojde k výjimce `comp` vyvolá výjimku. V takovém případě řízené sekvenci je ponechán v neurčené pořadí a je znovu vyvolány výjimku.  
  
##  <a name="op_eq"></a>forward_list::Operator =  
 Nahradí prvky dopředného seznamu kopii jiného seznamu předat dál.  
  
```  
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|Předat dál seznam kopírovány do seznamu předat dál.|  
|`IList`|Složené závorce uzavřena inicializátoru seznam, který se chová stejně jako posloupnost elementy typu `Type`.|  
  
### <a name="remarks"></a>Poznámky  
 První člen operátor nahradí řízené sekvenci kopii pořadí řízené `right`.  
  
 Druhý člen operátor nahrazuje řízené sekvenci z objektu třídy `initializer_list<Type>`.  
  
 Třetí operátor členů je stejný jako první, ale s [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) odkaz.  
  
##  <a name="pointer"></a>forward_list::Pointer  
 Typ, který poskytuje ukazatel na element v seznamu předat dál.  
  
```  
typedef typename Allocator::pointer pointer;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="pop_front"></a>forward_list::pop_front  
 Odstraní prvek na začátek dopředného seznamu.  
  
```  
void pop_front();
```  
  
### <a name="remarks"></a>Poznámky  
 První prvek seznamu předat dál, musí být neprázdný.  
  
 Členská funkce nikdy vyvolá výjimku.  
  
##  <a name="push_front"></a>forward_list::push_front  
 Přidá prvek na začátek seznamu předat dál.  
  
```  
void push_front(const Type& val);
void push_front(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`val`|Prvek přidán na začátek seznamu předat dál.|  
  
### <a name="remarks"></a>Poznámky  
 Pokud je vyvolána výjimka, je ponechán kontejneru v nezměněném stavu a je znovu vyvolány výjimku.  
  
##  <a name="reference"></a>forward_list::Reference  
 Typ, který obsahuje odkaz na element v seznamu předat dál.  
  
```  
typedef typename Allocator::reference reference;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="remove"></a>forward_list::Remove  
 Vymaže elementy dopředného seznamu, který odpovídá zadané hodnotě.  
  
```  
void remove(const Type& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`val`|Hodnota, která, pokud držené elementu, bude výsledkem tohoto prvku odebrání ze seznamu.|  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce odebere řízené sekvenci všechny elementy, určené, které iterator `P`, pro kterou `*P ==  val`.  
  
 Členská funkce nikdy vyvolá výjimku.  
  
##  <a name="remove_if"></a>forward_list::remove_if  
 Vymaže elementy dopředného seznamu, pro kterou je splněné zadaným predikátem.  
  
```  
template <class Predicate>  
void remove_if(Predicate pred);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`pred`|Unární predikátu. Výsledkem je, pokud splňují elementu, odstranění tohoto prvku ze seznamu.|  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce odebere řízené sekvenci všechny elementy, určené, které iterator `P`, pro kterou ` pred(*P)` hodnotu true.  
  
 Pouze, pokud dojde k výjimce `pred` vyvolá výjimku. V takovém případě řízené sekvenci je ponechán v neurčené stavu a je znovu vyvolány výjimku.  
  
##  <a name="resize"></a>forward_list::Resize  
 Určuje novou velikost dopředného seznam.  
  
```  
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_Newsize`|Počet elementů v seznamu změněnou předat dál.|  
|`val`|Hodnota, která chcete použít pro odsazení.|  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce obě zajistěte, aby byl počet elementů v seznamu od nynějška `_Newsize`. Pokud je třeba provést řízené sekvenci déle, první členská funkce připojí elementy s hodnotou `Type()`, zatímco druhý členská funkce připojí elementy s hodnotou `val`. Chcete-li řízené sekvenci kratší, oba členské funkce efektivně volání `erase_after(begin() + _Newsize - 1, end())`.  
  
##  <a name="reverse"></a>forward_list::Reverse  
 Obrátí pořadí, ve kterém elementy objevují v seznamu předat dál.  
  
```  
void reverse();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="size_type"></a>forward_list::size_type  
 Typ, který reprezentuje nepodepsané vzdálenost mezi dvěma prvky.  
  
```  
typedef typename Allocator::size_type size_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Zadejte celé číslo bez znaménka popisuje objekt, který může představovat délka žádné řízené sekvenci.  
  
##  <a name="sort"></a>forward_list::sort  
 Uspořádá elementy ve vzestupném pořadí nebo k pořadí určeného predikátu.  
  
```  
void sort();
template <class Predicate>  
void sort(Predicate pred);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`pred`|Řazení predikát.|  
  
### <a name="remarks"></a>Poznámky  
 Obě členské funkce řazení elementů v řízené sekvenci predikátu, popsané dole.  
  
 U iterátorů `Pi` a `Pj` určení prvky v pozic `i` a `j`, první členská funkce ukládá pořadí `!(*Pj < *Pi)` vždy, když `i < j`. (Prvky jsou seřazeny v `ascending` pořadí.) Funkce šablony člen ukládá pořadí `! pred(*Pj, *Pi)` vždy, když `i < j`. V výsledné řízené sekvenci se vrátit zpět žádné seřazené páry elementů v původní řízené sekvenci. (Řazení je stabilní.)  
  
 Pouze, pokud dojde k výjimce `pred` vyvolá výjimku. V takovém případě řízené sekvenci je ponechán v neurčené pořadí a je znovu vyvolány výjimku.  
  
##  <a name="splice_after"></a>forward_list::splice_after  
 Odebere elementy z forward_list – zdroj a vloží je do forward_list – cílové.  
  
```  
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
 `Where`  
 Pozice v forward_list – cílové po kterém se má vložit.  
  
 `Source`  
 Zdrojovém forward_list –, které má být vložen do cílového forward_list –.  
  
 `Iter`  
 Element, který má být vložen z forward_list – zdroj.  
  
 `First`  
 První prvek v rozsahu, který má být vložen z forward_list – zdroj.  
  
 `Last`  
 První pozici mimo rozsah, který má být vložen z forward_list – zdroj.  
  
### <a name="remarks"></a>Poznámky  
 První pár členských funkcí vloží pořadí řízené `Source` pouze po elementu v řízené sekvenci, na kterou odkazuje `Where`. Také odebere všechny elementy z `Source`. ( `&Source` nesmí být stejný jako `this`.)  
  
 Odebere element na druhý pár členských funkcí jenom po `Iter` v řízené sekvenci `Source` a vloží ho hned po elementu v řízené sekvenci na kterou odkazuje `Where`. (Pokud `Where == Iter || Where == ++Iter`, žádná změna.)  
  
 Třetí dvojice členské funkce (pohyboval uživatele programu splice) vloží Podoblast sady určené, které `(First, Last)` z pořadí řízené `Source` pouze po elementu v řízené sekvenci, na kterou odkazuje `Where`. Odebere také původní Podoblast sady z pořadí řízené `Source`. (Pokud `&Source == this`, rozsahu `(First, Last)` nesmí obsahovat elementu, na kterou odkazuje `Where`.)  
  
 Pokud ranged uživatele programu splice vloží `N` prvky, a `&Source != this`, objekt třídy [iterator](#iterator) se zvýší `N` časy.  
  
 Žádné iterátory, ukazatele nebo odkazy, které se určit spliced elementy zneplatní.  
  
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
  
##  <a name="swap"></a>forward_list::swap  
 Výměny elementy dva seznamy předat dál.  
  
```  
void swap(forward_list& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|Předat dál seznam poskytuje elementy výměnu.|  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce prohození řízené pořadí mezi `*this` a `right`. Pokud `get_allocator() ==  right.get_allocator()`, učiní tak konstantní včas, vyvolá nedocházelo k výjimkám a ho by způsobila neplatnost žádné odkazy, ukazatele nebo iterátory, které určit elementů ve dvou řízené pořadí. Jinak provede několik element přiřazení a volá konstruktor úměrná počet elementů ve dvou řízené pořadí.  
  
##  <a name="unique"></a>forward_list::Unique  
 Eliminuje všechny kromě první prvek z každé po sobě jdoucích skupiny ekvivalentní elementy.  
  
```  
void unique();
template <class BinaryPredicate>  
void unique(BinaryPredicate comp);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`comp`|Binární predikát použit k porovnání po sobě následujících elementů.|  
  
### <a name="remarks"></a>Poznámky  
 Zachová první den každý jedinečný prvek a odebere zbytek. Elementy musí být seřazeny tak, aby sousedí elementy stejnou hodnotu v seznamu.  
  
 První člen funkce odebere řízené sekvenci každý element, který porovnává rovna jeho předchozí element. U iterátorů `Pi` a `Pj` určení prvky v pozic `i` a `j`, druhý členská funkce odebere každý element, pro kterou `i + 1 == j &&  comp(*Pi, *Pj)`.  
  
 Řízené sekvenci délka `N` (> 0), predikát ` comp(*Pi, *Pj)` vyhodnotí `N - 1` časy.  
  
 Pouze, pokud dojde k výjimce `comp` vyvolá výjimku. V takovém případě řízené sekvenci je ponechán v neurčené stavu a je znovu vyvolány výjimku.  
  
##  <a name="value_type"></a>forward_list::value_type  
 Typ, který představuje typ elementu, které jsou uloženy v seznamu předat dál.  
  
```  
typedef typename Allocator::value_type value_type;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ se jedná o synonymum _ parametr šablony `Ty`.  
  
## <a name="see-also"></a>Viz také  
 [<forward_list>](../standard-library/forward-list.md)

