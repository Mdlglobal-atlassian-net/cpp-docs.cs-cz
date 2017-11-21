---
title: "concurrent_vector – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords: concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8dc17ee63caf62ddeea4a134d61f8fbd47e0061c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="concurrentvector-class"></a>concurrent_vector – třída
`concurrent_vector` Třídy je třída kontejneru pořadí, která umožňuje náhodný přístup k libovolného elementu. Umožňuje bezpečné souběžnosti připojit, iterator traversal operace, iterator přístup a přístup k elementu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
 private details::_Concurrent_vector_base_v4;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ elementů v vektoru.  
  
 `_Ax`  
 Typ, který představuje uložené allocator objekt, který zapouzdřuje informace o přidělení a zrušení přidělení paměti pro souběžné vektoru. Tento argument je volitelný a výchozí hodnota je `allocator<T>`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`allocator_type`|Typ, který reprezentuje allocator – třída pro souběžné vektoru.|  
|`const_iterator`|Typ, který poskytuje iterator náhodný přístup, který může číst `const` element v souběžných vektoru.|  
|`const_pointer`|Typ, který poskytuje odkazy `const` element v souběžných vektoru.|  
|`const_reference`|Typ, který obsahuje odkaz na `const` element uložené v souběžných vektor pro čtení a provádění `const` operace.|  
|`const_reverse_iterator`|Typ, který poskytuje iterator náhodný přístup, který může číst všechny `const` element v souběžných vektoru.|  
|`difference_type`|Typ, který poskytuje podepsaný vzdálenost mezi dvěma prvky v souběžných vektoru.|  
|`iterator`|Typ, který poskytuje iterator náhodný přístup, který může číst libovolný element v souběžných vektoru. Změna elementu s použitím iteraci není bezpečné souběžnosti.|  
|`pointer`|Typ, který poskytuje ukazatel na prvek v souběžných vektoru.|  
|`reference`|Typ, který obsahuje odkaz na element uložené v souběžných vektoru.|  
|`reverse_iterator`|Typ, který poskytuje iterator náhodný přístup, který může číst libovolný element v invertovaných souběžných vektoru. Změna elementu s použitím iteraci není bezpečné souběžnosti.|  
|`size_type`|Typ, který udává počet elementů v souběžných vektoru.|  
|`value_type`|Typ, který představuje typ data uložená v souběžných vektoru.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[concurrent_vector](#ctor)|Přetíženo. Vytvoří souběžných vektoru.|  
|[~ concurrent_vector – destruktor](#dtor)|Vymaže všechny elementy a zničí tento souběžných vektoru.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[přiřazení](#assign)|Přetíženo. Vymaže elementy souběžných vektoru a přiřadí ji buď `_N` zkopíruje z `_Item`, nebo hodnoty zadané ve iterator rozsah [ `_Begin`, `_End`). Tato metoda není bezpečná souběžnosti.|  
|[v](#at)|Přetíženo. Poskytuje přístup k elementu u daného indexu v souběžných vektoru. Tato metoda je souběžnosti bezpečných pro operace čtení a také během růstu vektoru, tak dlouho, dokud zajistíte, že hodnota `_Index` je menší než velikost souběžných vektoru.|  
|[zpět](#back)|Přetíženo. Vrátí a odkaz, nebo `const` odkazovat na poslední prvek v souběžných vektoru. Pokud souběžných vektoru je prázdná, není definován návratovou hodnotu. Tato metoda je bezpečné souběžnosti.|  
|[začít](#begin)|Přetíženo. Vrátí iterovat typu `iterator` nebo `const_iterator` na začátek souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[kapacita](#capacity)|Vrátí maximální velikost, do kterého můžete dosáhnout souběžných vektoru bez nutnosti přidělení více paměti. Tato metoda je bezpečné souběžnosti.|  
|[cbegin –](#cbegin)|Vrátí iterovat typu `const_iterator` na začátek souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[cend –](#cend)|Vrátí iterovat typu `const_iterator` na konec souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[Vymazat](#clear)|Vymaže všechny elementy ve souběžných vektoru. Tato metoda není bezpečná souběžnosti.|  
|[crbegin –](#crbegin)|Vrátí iterovat typu `const_reverse_iterator` na začátek souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[crend –](#crend)|Vrátí iterovat typu `const_reverse_iterator` na konec souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[prázdný](#empty)|Testy, pokud je v době prázdný souběžných vektoru tato metoda je volána. Tato metoda je bezpečné souběžnosti.|  
|[end](#end)|Přetíženo. Vrátí iterovat typu `iterator` nebo `const_iterator` na konec souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[přední](#front)|Přetíženo. Vrátí a odkaz, nebo `const` odkaz na prvním elementem v souběžných vektoru. Pokud souběžných vektoru je prázdná, není definován návratovou hodnotu. Tato metoda je bezpečné souběžnosti.|  
|[get_allocator –](#get_allocator)|Vrátí kopii allocator použitý k vytvoření souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[grow_by –](#grow_by)|Přetíženo. Zvětšování tento souběžných vektoru podle `_Delta` elementy. Tato metoda je bezpečné souběžnosti.|  
|[grow_to_at_least –](#grow_to_at_least)|Zvětšování tento souběžných vektoru, dokud má nejméně `_N` elementy. Tato metoda je bezpečné souběžnosti.|  
|[max_size –](#max_size)|Vrátí maximální počet prvky, které mohou být uloženy souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[push_back –](#push_back)|Přetíženo. Daná položka připojí na konec souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[rbegin –](#rbegin)|Přetíženo. Vrátí iterovat typu `reverse_iterator` nebo `const_reverse_iterator` na začátek souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[rend –](#rend)|Přetíženo. Vrátí iterovat typu `reverse_iterator` nebo `const_reverse_iterator` na konec souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[Rezervovat](#reserve)|Přiděluje dostatek místa pro souběžné vektoru dosáhnout velikost `_N` bez nutnosti později přidělení více paměti. Tato metoda není bezpečná souběžnosti.|  
|[Změna velikosti](#resize)|Přetíženo. Změní velikost souběžných vektoru na požadovanou velikost, odstranění nebo přidávání elementů podle potřeby. Tato metoda není bezpečná souběžnosti.|  
|[shrink_to_fit –](#shrink_to_fit)|Zkomprimuje interního vyjádření souběžných vektoru zmenšíte fragmentace a optimalizovat využití paměti. Tato metoda není bezpečná souběžnosti.|  
|[velikost](#size)|Vrátí počet prvků v souběžných vektoru. Tato metoda je bezpečné souběžnosti.|  
|[swap](#swap)|Zamění obsah dvou souběžných vektory. Tato metoda není bezpečná souběžnosti.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[[] – operátor](#operator_at)|Přetíženo. Poskytuje přístup k elementu u daného indexu v souběžných vektoru. Tato metoda je souběžnosti bezpečných pro operace čtení a také během růstu vektoru, tak dlouho, dokud zajistíte, že hodnota `_Index` je menší než velikost souběžných vektoru.|  
|[operátor =](#operator_eq)|Přetíženo. Přiřadí obsah jiného `concurrent_vector` k tomuto objektu. Tato metoda není bezpečná souběžnosti.|  
  
## <a name="remarks"></a>Poznámky  
 Podrobné informace o `concurrent_vector` třídy najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_Concurrent_vector_base_v4`  
  
 `_Allocator_base`  
  
 `concurrent_vector`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concurrent_vector.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="assign"></a>přiřazení 

 Vymaže elementy souběžných vektoru a přiřadí ji buď `_N` zkopíruje z `_Item`, nebo hodnoty zadané ve iterator rozsah [ `_Begin`, `_End`). Tato metoda není bezpečná souběžnosti.  
  
```
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```  
  
### <a name="parameters"></a>Parametry  
 `_InputIterator`  
 Typ zadaný iterator.  
  
 `_N`  
 Počet položek, které chcete zkopírovat do souběžných vektoru.  
  
 `_Item`  
 Odkaz na hodnotu použitou k vyplnění souběžných vektoru.  
  
 `_Begin`  
 Iterátor na první prvek zdrojový rozsah.  
  
 `_End`  
 Iterátor na jednu za posledním elementem zdrojový rozsah.  
  
### <a name="remarks"></a>Poznámky  
 `assign`není bezpečné souběžnosti. Je nutné zajistit, že jsou nejsou žádná jiná vlákna při volání této metody vyvolání metody na souběžných vektoru.  
  
##  <a name="at"></a>v 

 Poskytuje přístup k elementu u daného indexu v souběžných vektoru. Tato metoda je souběžnosti bezpečných pro operace čtení a také během růstu vektoru, tak dlouho, dokud zajistíte, že hodnota `_Index` je menší než velikost souběžných vektoru.  
  
```
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index elementu, který chcete načíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na položku na daném indexu.  
  
### <a name="remarks"></a>Poznámky  
 Verze funkce `at` , vrátí jinou hodnotu než `const` odkaz nelze použít současně zapsat do elementu z různých vláknech. Objekt různých synchronizace slouží k synchronizaci souběžných pro čtení a operací zápisu na stejný datový prvek.  
  
 Vyvolá metoda `out_of_range` Pokud `_Index` je větší než nebo rovna velikosti souběžných vektoru a `range_error` Pokud index je poškozený část vektoru. Podrobnosti o jak vektor porušený se může stát, najdete v části [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
##  <a name="back"></a>zpět 

 Vrátí a odkaz, nebo `const` odkazovat na poslední prvek v souběžných vektoru. Pokud souběžných vektoru je prázdná, není definován návratovou hodnotu. Tato metoda je bezpečné souběžnosti.  
  
```
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A odkaz nebo `const` odkazovat na poslední prvek v souběžných vektoru.  
  
##  <a name="begin"></a>začít 

 Vrátí iterovat typu `iterator` nebo `const_iterator` na začátek souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace typu `iterator` nebo `const_iterator` na začátek souběžných vektoru.  
  
##  <a name="capacity"></a>kapacita 

 Vrátí maximální velikost, do kterého můžete dosáhnout souběžných vektoru bez nutnosti přidělení více paměti. Tato metoda je bezpečné souběžnosti.  
  
```
size_type capacity() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální velikost, ke kterému můžou růst souběžných vektoru bez nutnosti přidělení více paměti.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od standardní knihovna C++ `vector`, `concurrent_vector` objekt nepřesouvá stávající elementy, pokud se přiděluje víc paměti.  
  
##  <a name="cbegin"></a>cbegin – 

 Vrátí iterovat typu `const_iterator` na začátek souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace typu `const_iterator` na začátek souběžných vektoru.  
  
##  <a name="cend"></a>cend – 

 Vrátí iterovat typu `const_iterator` na konec souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace typu `const_iterator` na konec souběžných vektoru.  
  
##  <a name="clear"></a>Vymazat 

 Vymaže všechny elementy ve souběžných vektoru. Tato metoda není bezpečná souběžnosti.  
  
```
void clear();
```  
  
### <a name="remarks"></a>Poznámky  
 `clear`není bezpečné souběžnosti. Je nutné zajistit, že jsou nejsou žádná jiná vlákna při volání této metody vyvolání metody na souběžných vektoru. `clear`Interní pole neuvolní. Chcete-li uvolnit interní pole, zavolejte funkci `shrink_to_fit` po `clear`.  
  
##  <a name="ctor"></a>concurrent_vector 

 Vytvoří souběžných vektoru.  
  
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
 `M`  
 Typ přidělení vektoru zdroje.  
  
 `_InputIterator`  
 Typ vstupu iterator.  
  
 `_Al`  
 Třída alokátoru, která se má použít s tímto objektem.  
  
 `_Vector`  
 Zdroj `concurrent_vector` objekt, který chcete zkopírovat nebo přesunout elementy z.  
  
 `_N`  
 Počáteční kapacitu `concurrent_vector` objektu.  
  
 `_Item`  
 Hodnota elementů v konstruovaný objekt.  
  
 `_Begin`  
 Pozice první prvek v rozsahu elementy, které se mají zkopírovat.  
  
 `_End`  
 Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.  
  
### <a name="remarks"></a>Poznámky  
 Všechny konstruktory uložit objekt allocator `_Al` a inicializace vektoru.  
  
 První konstruktor zadejte je prázdný počáteční vektor a explicitně určuje typ přidělení. k použití.  
  
 Zadejte konstruktory druhý a třetí kopii souběžných vektoru `_Vector`.  
  
 Čtvrtý konstruktor určuje přesunu souběžných vektoru `_Vector`.  
  
 V páté konstruktoru určuje opakování určeného čísla ( `_N`) elementů výchozí hodnota pro třídu `T`.  
  
 Šesté konstruktor určuje opakování ( `_N`) elementy hodnoty `_Item`.  
  
 Poslední konstruktor určuje poskytl iterator rozsah hodnot [ `_Begin`, `_End`).  
  
##  <a name="dtor"></a>~ concurrent_vector 

 Vymaže všechny elementy a zničí tento souběžných vektoru.  
  
```
~concurrent_vector();
```  
  
##  <a name="crbegin"></a>crbegin – 

 Vrátí iterovat typu `const_reverse_iterator` na začátek souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace typu `const_reverse_iterator` na začátek souběžných vektoru.  
  
##  <a name="crend"></a>crend – 

 Vrátí iterovat typu `const_reverse_iterator` na konec souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace typu `const_reverse_iterator` na konec souběžných vektoru.  
  
##  <a name="empty"></a>prázdný 

 Testy, pokud je v době prázdný souběžných vektoru tato metoda je volána. Tato metoda je bezpečné souběžnosti.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud v tuto chvíli funkce byla zavolána, byla prázdná vektoru `false` jinak.  
  
##  <a name="end"></a>end 

 Vrátí iterovat typu `iterator` nebo `const_iterator` na konec souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace typu `iterator` nebo `const_iterator` na konec souběžných vektoru.  
  
##  <a name="front"></a>přední 

 Vrátí a odkaz, nebo `const` odkaz na prvním elementem v souběžných vektoru. Pokud souběžných vektoru je prázdná, není definován návratovou hodnotu. Tato metoda je bezpečné souběžnosti.  
  
```
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A odkaz nebo `const` odkaz na prvním elementem v souběžných vektoru.  
  
##  <a name="get_allocator"></a>get_allocator – 

 Vrátí kopii allocator použitý k vytvoření souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie allocator použitý k vytvoření `concurrent_vector` objektu.  
  
##  <a name="grow_by"></a>grow_by – 

 Zvětšování tento souběžných vektoru podle `_Delta` elementy. Tato metoda je bezpečné souběžnosti.  
  
```
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```  
  
### <a name="parameters"></a>Parametry  
 `_Delta`  
 Počet elementů má být připojen k objektu.  
  
 `_Item`  
 Hodnota k inicializaci nové elementy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Připojí se iterator první položku.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `_Item` nezadáte, nové prvky jsou výchozí zkonstruovat.  
  
##  <a name="grow_to_at_least"></a>grow_to_at_least – 

 Zvětšování tento souběžných vektoru, dokud má nejméně `_N` elementy. Tato metoda je bezpečné souběžnosti.  
  
```
iterator grow_to_at_least(size_type _N);
```  
  
### <a name="parameters"></a>Parametry  
 `_N`  
 Nové minimální velikost `concurrent_vector` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor, který odkazuje na začátek pořadí připojením, nebo element v indexu `_N` Pokud byly připojeny žádné elementy.  
  
##  <a name="max_size"></a>max_size – 

 Vrátí maximální počet prvky, které mohou být uloženy souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální počet elementů `concurrent_vector` objekt mohou být uloženy.  
  
##  <a name="operator_eq"></a>operátor = 

 Přiřadí obsah jiného `concurrent_vector` k tomuto objektu. Tato metoda není bezpečná souběžnosti.  
  
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
 `M`  
 Typ přidělení vektoru zdroje.  
  
 `_Vector`  
 Zdroj `concurrent_vector` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `concurrent_vector` objektu.  
  
##  <a name="operator_at"></a>[] – operátor 

 Poskytuje přístup k elementu u daného indexu v souběžných vektoru. Tato metoda je souběžnosti bezpečných pro operace čtení a také během růstu vektoru, tak dlouho, dokud zajistíte, že hodnota `_Index` je menší než velikost souběžných vektoru.  
  
```
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index elementu, který chcete načíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na položku na daném indexu.  
  
### <a name="remarks"></a>Poznámky  
 Verze `operator []` , vrátí jinou hodnotu než `const` odkaz nelze použít současně zapsat do elementu z různých vláknech. Objekt různých synchronizace slouží k synchronizaci souběžných pro čtení a operací zápisu na stejný datový prvek.  
  
 Žádné hranice kontrola se provádí zajistit, aby `_Index` je platný index v souběžných vektoru.  
  
##  <a name="push_back"></a>push_back – 

 Daná položka připojí na konec souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```  
  
### <a name="parameters"></a>Parametry  
 `_Item`  
 Hodnota, který bude přidán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Připojí se iterator k položce.  
  
##  <a name="rbegin"></a>rbegin – 

 Vrátí iterovat typu `reverse_iterator` nebo `const_reverse_iterator` na začátek souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace typu `reverse_iterator` nebo `const_reverse_iterator` na začátek souběžných vektoru.  
  
##  <a name="rend"></a>rend – 

 Vrátí iterovat typu `reverse_iterator` nebo `const_reverse_iterator` na konec souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
reverse_iterator rend();

const_reverse_iterator rend() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace typu `reverse_iterator` nebo `const_reverse_iterator` na konec souběžných vektoru.  
  
##  <a name="reserve"></a>Rezervovat 

 Přiděluje dostatek místa pro souběžné vektoru dosáhnout velikost `_N` bez nutnosti později přidělení více paměti. Tato metoda není bezpečná souběžnosti.  
  
```
void reserve(size_type _N);
```  
  
### <a name="parameters"></a>Parametry  
 `_N`  
 Počet elementů rezervovat místo pro.  
  
### <a name="remarks"></a>Poznámky  
 `reserve`není bezpečné souběžnosti. Je nutné zajistit, že jsou nejsou žádná jiná vlákna při volání této metody vyvolání metody na souběžných vektoru. Počet souběžných vektoru po vrátí metoda může být větší než požadovaný rezervace.  
  
##  <a name="resize"></a>Změna velikosti 

 Změní velikost souběžných vektoru na požadovanou velikost, odstranění nebo přidávání elementů podle potřeby. Tato metoda není bezpečná souběžnosti.  
  
```
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```  
  
### <a name="parameters"></a>Parametry  
 `_N`  
 Novou velikost concurrent_vector.  
  
 `val`  
 Hodnota nové elementy přidané do vektoru, pokud nová velikost je větší než původní velikost. Pokud hodnota je vynechán, nové objekty přiřazené výchozí hodnota pro jejich typu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je velikost kontejneru menší než požadovaná velikost, prvky jsou přidány do vektoru, dokud nedosáhne požadované velikosti. Pokud velikost kontejneru je větší než požadovaná velikost, jsou nejbližší na konec objektu kontejneru elementů odstranit, dokud kontejneru dosáhne velikosti `_N`. Pokud je přítomen velikost kontejneru stejná jako požadovaná velikost, nebyla provedena žádná akce.  
  
 `resize`není souběžnosti bezpečné. Je nutné zajistit, že jsou nejsou žádná jiná vlákna při volání této metody vyvolání metody na souběžných vektoru.  
  
##  <a name="shrink_to_fit"></a>shrink_to_fit – 

 Zkomprimuje interního vyjádření souběžných vektoru zmenšíte fragmentace a optimalizovat využití paměti. Tato metoda není bezpečná souběžnosti.  
  
```
void shrink_to_fit();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda bude interně znovu přidělit paměť přesunutí elementy kolem, zneplatnění všechny iterátory. `shrink_to_fit`není bezpečné souběžnosti. Je nutné zajistit, že jsou nejsou žádná jiná vlákna vyvolání metody na souběžných vektoru při volání této funkce.  
  
##  <a name="size"></a>velikost 

 Vrátí počet prvků v souběžných vektoru. Tato metoda je bezpečné souběžnosti.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů v této `concurrent_vector` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Vrácený velikost záruku, že se mají zahrnout všechny elementy připojí ve volání funkce `push_back`, nebo růst operace, které byly dokončeny před volání této metody. Však může také obsahovat elementy, které jsou přiděleny, ale stále ve vytváření podle souběžných volání metod růstu.  
  
##  <a name="swap"></a>swap 

 Zamění obsah dvou souběžných vektory. Tato metoda není bezpečná souběžnosti.  
  
```
void swap(concurrent_vector& _Vector);
```  
  
### <a name="parameters"></a>Parametry  
 `_Vector`  
 `concurrent_vector` Objekt, který chcete Prohodit obsah s.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md)



