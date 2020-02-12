---
title: concurrent_priority_queue – třída
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
ms.openlocfilehash: 1d8651d1391ded2970a00a7429c36f341a438659
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143220"
---
# <a name="concurrent_priority_queue-class"></a>concurrent_priority_queue – třída

Třída `concurrent_priority_queue` je kontejner, který umožňuje více vláknům souběžně vkládat a automaticky otevírané položky. Položky jsou odebrány v pořadí podle priority, kde priorita je určena funktor zadaným jako argument šablony.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ prvků, které mají být uloženy ve frontě priorit.

*_Compare*<br/>
Typ objektu funkce, který může porovnat dvě hodnoty prvků jako klíče řazení pro určení jejich relativního pořadí ve frontě priorit. Tento argument je nepovinný a binární predikát `less<T>` výchozí hodnotu.

*_Ax*<br/>
Typ, který představuje uložený objekt přidělování, který zapouzdřuje informace o přidělování a navracení paměti pro frontu souběžné priority. Tento argument je nepovinný a výchozí hodnota je `allocator<T>`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`allocator_type`|Typ, který představuje třídu přidělování pro frontu souběžné priority.|
|`const_reference`|Typ, který představuje odkaz const na element typu uložený ve frontě s souběžnou prioritou.|
|`reference`|Typ, který představuje odkaz na prvek typu uloženého ve frontě souběžné priority.|
|`size_type`|Typ, který spočítá počet prvků ve frontě souběžné priority.|
|`value_type`|Typ, který představuje datový typ uložený ve frontě s souběžnou prioritou.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|Přetíženo. Vytvoří frontu souběžné priority.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[jejich](#clear)|Vymaže všechny prvky v souběžné prioritě. Tato metoda není bezpečná pro souběžnost.|
|[obsahovat](#empty)|Testuje, zda je fronta souběžné priority v době volání této metody prázdná. Tato metoda je bezpečná pro souběžnost.|
|[get_allocator](#get_allocator)|Vrátí kopii přidělujícího modulu, která se používá k vytvoření fronty souběžné priority. Tato metoda je bezpečná pro souběžnost.|
|[push](#push)|Přetíženo. Přidá prvek do fronty souběžné priority. Tato metoda je bezpečná pro souběžnost.|
|[hodnota](#size)|Vrátí počet prvků ve frontě souběžné priority. Tato metoda je bezpečná pro souběžnost.|
|[adresu](#swap)|Zamění obsah dvou front priorit souběžnosti. Tato metoda není bezpečná pro souběžnost.|
|[try_pop](#try_pop)|Odebere a vrátí prvek nejvyšší priority z fronty, pokud je fronta neprázdná. Tato metoda je bezpečná pro souběžnost.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Přetíženo. Přiřadí obsah jiného objektu `concurrent_priority_queue` k tomuto. Tato metoda není bezpečná pro souběžnost.|

## <a name="remarks"></a>Poznámky

Podrobné informace o třídě `concurrent_priority_queue` naleznete v tématu [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`concurrent_priority_queue`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concurrent_priority_queue. h

**Obor názvů:** souběžnost

## <a name="clear"></a>jejich

Vymaže všechny prvky v souběžné prioritě. Tato metoda není bezpečná pro souběžnost.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

`clear` není bezpečná pro souběžnost. Když zavoláte tuto metodu, musíte zajistit, aby žádná jiná vlákna nevolala metody ve frontě priorit souběžnosti. `clear` nemá volnou paměť.

## <a name="ctor"></a>concurrent_priority_queue

Vytvoří frontu souběžné priority.

```cpp
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```

### <a name="parameters"></a>Parametry

*_InputIterator*<br/>
Typ vstupního iterátoru.

*_Al*<br/>
Třída alokátoru, která se má použít s tímto objektem.

*_Init_capacity*<br/>
Počáteční kapacita objektu `concurrent_priority_queue`.

*_Begin*<br/>
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*_End*<br/>
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

*_Src*<br/>
Zdrojový objekt `concurrent_priority_queue`, ze kterého se mají kopírovat nebo přesunout prvky.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt přidělování `_Al` a inicializují frontu priorit.

První konstruktor určuje prázdnou frontu počáteční priority a volitelně určuje přidělování.

Druhý konstruktor určuje prioritní frontu s počáteční kapacitou `_Init_capacity` a volitelně určuje přidělování.

Třetí konstruktor určuje hodnoty poskytnuté rozsahem iterátoru [`_Begin`, `_End`) a volitelně určuje přidělování.

Čtvrtý a pátý konstruktor určuje kopii `_Src`fronty priorit.

Šest a sedmý konstruktory určují přesun `_Src`fronty priorit.

## <a name="empty"></a>obsahovat

Testuje, zda je fronta souběžné priority v době volání této metody prázdná. Tato metoda je bezpečná pro souběžnost.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla fronta priorit prázdná v okamžiku, kdy byla funkce volána, jinak **false** .

## <a name="get_allocator"></a>get_allocator

Vrátí kopii přidělujícího modulu, která se používá k vytvoření fronty souběžné priority. Tato metoda je bezpečná pro souběžnost.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Kopie přidělování, která se používá k vytvoření objektu `concurrent_priority_queue`.

## <a name="operator_eq"></a>operátor =

Přiřadí obsah jiného objektu `concurrent_priority_queue` k tomuto. Tato metoda není bezpečná pro souběžnost.

```cpp
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Zdrojový objekt `concurrent_priority_queue`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `concurrent_priority_queue`.

## <a name="push"></a>replik

Přidá prvek do fronty souběžné priority. Tato metoda je bezpečná pro souběžnost.

```cpp
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>Parametry

*_Elem*<br/>
Prvek, který má být přidán do fronty souběžné priority.

## <a name="size"></a>hodnota

Vrátí počet prvků ve frontě souběžné priority. Tato metoda je bezpečná pro souběžnost.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v tomto objektu `concurrent_priority_queue`.

### <a name="remarks"></a>Poznámky

Vrácená velikost je zaručena, aby zahrnovala všechny prvky přidané voláním funkce `push`. Nemusí ale odrážet výsledky probíhajících souběžných operací.

## <a name="swap"></a>adresu

Zamění obsah dvou front priorit souběžnosti. Tato metoda není bezpečná pro souběžnost.

```cpp
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>Parametry

*_Queue*<br/>
Objekt `concurrent_priority_queue`, pomocí kterého má prohození obsahu.

## <a name="try_pop"></a>try_pop

Odebere a vrátí prvek nejvyšší priority z fronty, pokud je fronta neprázdná. Tato metoda je bezpečná pro souběžnost.

```cpp
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>Parametry

*_Elem*<br/>
Odkaz na proměnnou, která bude naplněna pomocí elementu s nejvyšší prioritou, pokud je fronta prázdná.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla hodnota vyjmuta, jinak **false** .

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md)
