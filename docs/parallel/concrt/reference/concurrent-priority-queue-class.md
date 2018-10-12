---
title: concurrent_priority_queue – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de97557025929c394039b1a786fe12a7035381e1
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163150"
---
# <a name="concurrentpriorityqueue-class"></a>concurrent_priority_queue – třída

`concurrent_priority_queue` Třída je kontejner, který umožňuje více vláken současně nabízená oznámení a pop položek. Položky jsou otevřené v pořadí podle priority, kde je určen priority funktor zadaný jako argument šablony.

## <a name="syntax"></a>Syntaxe

```
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ prvků, který bude uložen do prioritní fronty.

*_Porovnat*<br/>
Typ objektu funkce, který může porovnat dvě hodnoty prvků jako klíče řazení pro určení jejich relativního pořadí v prioritní fronty. Tento argument je nepovinný a binární predikát `less<T>` je výchozí hodnota.

*_Ax*<br/>
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navracení zpět paměti pro souběžný prioritní fronty. Tento argument je nepovinný a výchozí hodnota je `allocator<T>`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`allocator_type`|Typ, který představuje třídu alokátoru pro souběžné prioritní fronty.|
|`const_reference`|Typ, který představuje konstantní odkaz na element typu uložené v souběžné prioritní fronty.|
|`reference`|Typ, který představuje odkaz na element typu uložené v souběžné prioritní fronty.|
|`size_type`|Typ, který vrátí počet prvků v souběžné prioritní fronty.|
|`value_type`|Typ, který představuje typ dat uložených v souběžné prioritní fronty.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|Přetíženo. Sestaví souběžných prioritní fronty.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Vymazat](#clear)|Vymaže všechny prvky v souběžné prioritu. Tato metoda není bezpečná pro souběžnost.|
|[prázdný](#empty)|Testuje, zda je souběžných prioritní fronty je prázdný v době tato metoda je volána. Tato metoda je bezpečná pro souběžnost.|
|[get_allocator](#get_allocator)|Vrátí kopii objektu Alokátor použitý k vytvoření souběžných prioritní fronty. Tato metoda je bezpečná pro souběžnost.|
|[push](#push)|Přetíženo. Přidá prvek na souběžné prioritní fronty. Tato metoda je bezpečná pro souběžnost.|
|[Velikost](#size)|Vrátí počet prvků v souběžné prioritní fronty. Tato metoda je bezpečná pro souběžnost.|
|[Prohození](#swap)|Zamění obsah dvou souběžných prioritní fronty. Tato metoda není bezpečná pro souběžnost.|
|[try_pop](#try_pop)|Odebere a vrátí nejvyšší prvek prioritu z fronty, pokud fronta je prázdný. Tato metoda je bezpečná pro souběžnost.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Přetíženo. Přiřadí obsah jiného `concurrent_priority_queue` do tohoto objektu. Tato metoda není bezpečná pro souběžnost.|

## <a name="remarks"></a>Poznámky

Podrobné informace o `concurrent_priority_queue` najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`concurrent_priority_queue`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concurrent_priority_queue.h

**Namespace:** souběžnosti

##  <a name="clear"></a> Vymazat

Vymaže všechny prvky v souběžné prioritu. Tato metoda není bezpečná pro souběžnost.

```
void clear();
```

### <a name="remarks"></a>Poznámky

`clear` není bezpečná pro souběžnost. Ujistěte se, že nejsou žádná jiná vlákna jsou volání metod na souběžné prioritní fronty, při volání této metody. `clear` Nelze uvolnit paměť.

##  <a name="ctor"></a> concurrent_priority_queue –

Sestaví souběžných prioritní fronty.

```
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
Počáteční kapacita objektu `concurrent_priority_queue` objektu.

*_Zahájit*<br/>
Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.

*_Ukončit*<br/>
Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.

*_Src*<br/>
Zdroj `concurrent_priority_queue` objektu, který chcete zkopírovat nebo přesunout elementy ze.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt alokátoru `_Al` a inicializovat prioritní fronty.

První konstruktor určuje prázdný počáteční prioritní fronty a volitelně určuje alokátoru.

Druhý konstruktor určuje prioritní fronty s počáteční kapacitu `_Init_capacity` a volitelně určuje alokátoru.

Třetí konstruktor určuje hodnoty poskytnuté rozsahem iterátoru [ `_Begin`, `_End`) a volitelně určuje alokátoru.

Čtvrtý a pátý konstruktor určuje kopii prioritní fronty `_Src`.

Zadejte šestého a sedmý konstruktor přesunutí prioritní fronty `_Src`.

##  <a name="empty"></a> prázdný

Testuje, zda je souběžných prioritní fronty je prázdný v době tato metoda je volána. Tato metoda je bezpečná pro souběžnost.

```
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud v tuto chvíli byla volána funkce, byla prázdná prioritní fronty **false** jinak.

##  <a name="get_allocator"></a> get_allocator

Vrátí kopii objektu Alokátor použitý k vytvoření souběžných prioritní fronty. Tato metoda je bezpečná pro souběžnost.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor použitý k vytvoření kopie `concurrent_priority_queue` objektu.

##  <a name="operator_eq"></a> operátor =

Přiřadí obsah jiného `concurrent_priority_queue` do tohoto objektu. Tato metoda není bezpečná pro souběžnost.

```
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Zdroj `concurrent_priority_queue` objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `concurrent_priority_queue` objektu.

##  <a name="push"></a> nabízených oznámení

Přidá prvek na souběžné prioritní fronty. Tato metoda je bezpečná pro souběžnost.

```
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>Parametry

*_Elem*<br/>
Elementu, který chcete přidat do souběžných prioritní fronty.

##  <a name="size"></a> Velikost

Vrátí počet prvků v souběžné prioritní fronty. Tato metoda je bezpečná pro souběžnost.

```
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků v tomto `concurrent_priority_queue` objektu.

### <a name="remarks"></a>Poznámky

Je zaručeno, že vrácená velikost zahrnout všechny elementy přidané ve volání funkce `push`. Ale to nemusí odrážet výsledky čekající souběžných operací.

##  <a name="swap"></a> Prohození

Zamění obsah dvou souběžných prioritní fronty. Tato metoda není bezpečná pro souběžnost.

```
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>Parametry

*_Fronty*<br/>
`concurrent_priority_queue` Objektu k výměně obsahu s.

##  <a name="try_pop"></a> try_pop –

Odebere a vrátí nejvyšší prvek prioritu z fronty, pokud fronta je prázdný. Tato metoda je bezpečná pro souběžnost.

```
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>Parametry

*_Elem*<br/>
Odkaz na proměnnou, která naplní prvku nejvyšší prioritou, pokud fronta je prázdný.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud hodnotu byl odebrán, **false** jinak.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md)

