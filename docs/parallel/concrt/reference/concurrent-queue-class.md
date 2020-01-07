---
title: concurrent_queue – třída
ms.date: 11/04/2016
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
ms.openlocfilehash: 7f87ead486d635c933ad356f9868c22344601eda
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298616"
---
# <a name="concurrent_queue-class"></a>concurrent_queue – třída

Třída `concurrent_queue` je třída kontejneru sekvence, která umožňuje prvnímu přístupu k jeho prvkům. Umožňuje omezené sady bezpečných operací v rámci souběžnosti, například `push` a `try_pop`. V případě bezpečného zpracování v souběžnosti znamená, že ukazatele nebo iterátory jsou vždy platné. Není zárukou pro inicializaci elementu nebo z konkrétního pořadí procházení.

## <a name="syntax"></a>Syntaxe

```
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ prvků, které mají být uloženy ve frontě.

*_Ax*<br/>
Typ, který představuje uložený objekt přidělování, který zapouzdřuje informace o přidělování a navracení paměti pro tuto souběžnou frontu. Tento argument je nepovinný a výchozí hodnota je `allocator<T>`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|`allocator_type`|Typ, který představuje třídu přidělování pro souběžnou frontu.|
|`const_iterator`|Typ, který představuje iterátor `const` bez vlákna u prvků v souběžné frontě.|
|`const_reference`|Typ, který poskytuje odkaz na `const` element uložený v souběžné frontě pro čtení a provádění `const`ch operací.|
|`difference_type`|Typ, který poskytuje podepsanou vzdálenost mezi dvěma prvky v souběžné frontě.|
|`iterator`|Typ, který představuje iterátor, který není bezpečný pro přístup z více vláken nad prvky v souběžné frontě.|
|`reference`|Typ, který poskytuje odkaz na prvek uložený v souběžné frontě.|
|`size_type`|Typ, který spočítá počet prvků v souběžné frontě.|
|`value_type`|Typ, který představuje datový typ uložený v souběžné frontě.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[concurrent_queue](#ctor)|Přetížené Sestaví souběžnou frontu.|
|[~concurrent_queue Destructor](#dtor)|Odstraní souběžnou frontu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[jejich](#clear)|Vymaže souběžnou frontu a zničí všechny aktuálně zařazené prvky do fronty. Tato metoda není bezpečná pro souběžnost.|
|[empty](#empty)|Testuje, zda je souběžná fronta prázdná v okamžiku volání této metody. Tato metoda je bezpečná pro souběžnost.|
|[get_allocator](#get_allocator)|Vrátí kopii přidělujícího modulu, pomocí které se vytvoří souběžná fronta. Tato metoda je bezpečná pro souběžnost.|
|[push](#push)|Přetížené Zařadí položku do fronty na konec souběžné fronty. Tato metoda je bezpečná pro souběžnost.|
|[try_pop](#try_pop)|Vyřadí položku z fronty, pokud je k dispozici. Tato metoda je bezpečná pro souběžnost.|
|[unsafe_begin](#unsafe_begin)|Přetížené Vrátí iterátor typu `iterator` nebo `const_iterator` na začátek souběžné fronty. Tato metoda není bezpečná pro souběžnost.|
|[unsafe_end](#unsafe_end)|Přetížené Vrátí iterátor typu `iterator` nebo `const_iterator` na konec souběžné fronty. Tato metoda není bezpečná pro souběžnost.|
|[unsafe_size](#unsafe_size)|Vrátí počet položek ve frontě. Tato metoda není bezpečná pro souběžnost.|

## <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`concurrent_queue`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concurrent_queue. h

**Obor názvů:** souběžnost

##  <a name="clear"></a>jejich

Vymaže souběžnou frontu a zničí všechny aktuálně zařazené prvky do fronty. Tato metoda není bezpečná pro souběžnost.

```
void clear();
```

##  <a name="ctor"></a>concurrent_queue

Sestaví souběžnou frontu.

```
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Parametry

*_InputIterator*<br/>
Typ vstupního iterátoru, který určuje rozsah hodnot.

*_Al*<br/>
Třída alokátoru, která se má použít s tímto objektem.

*_OtherQ*<br/>
Zdrojový objekt `concurrent_queue`, ze kterého se mají kopírovat nebo přesunout prvky.

*_Begin*<br/>
Pozice prvního prvku v rozsahu prvků, které mají být zkopírovány.

*_End*<br/>
Pozice prvního prvku mimo rozsah prvků, které mají být zkopírovány.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt přidělování `_Al` a inicializují frontu.

První konstruktor určuje prázdnou počáteční frontu a explicitně určuje typ přidělujícího objektu, který se má použít.

Druhý konstruktor určuje kopii souběžných `_OtherQ`fronty.

Třetí konstruktor určuje přesun `_OtherQ`souběžné fronty.

Čtvrtý konstruktor určuje hodnoty poskytované rozsahem iterátoru [`_Begin`, `_End`).

##  <a name="dtor"></a>~ concurrent_queue

Odstraní souběžnou frontu.

```
~concurrent_queue();
```

##  <a name="empty"></a>obsahovat

Testuje, zda je souběžná fronta prázdná v okamžiku volání této metody. Tato metoda je bezpečná pro souběžnost.

```
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla souběžná fronta prázdná v okamžiku, kdy se vyhledala, jinak **false** .

### <a name="remarks"></a>Poznámky

Zatímco tato metoda je bezpečná pro souběžnost s ohledem na volání metod `push`, `try_pop`a `empty`, vrácená hodnota může být nesprávná o čas, který je zkontrolován volajícím vláknem.

##  <a name="get_allocator"></a>get_allocator

Vrátí kopii přidělujícího modulu, pomocí které se vytvoří souběžná fronta. Tato metoda je bezpečná pro souběžnost.

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Kopie přidělujícího modulu, pomocí které se vytváří souběžná fronta.

##  <a name="push"></a>replik

Zařadí položku do fronty na konec souběžné fronty. Tato metoda je bezpečná pro souběžnost.

```
void push(const T& _Src);

void push(T&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Položka, která se má přidat do fronty

### <a name="remarks"></a>Poznámky

`push` je bezpečné pro souběžnost s voláním metod `push`, `try_pop`a `empty`.

##  <a name="try_pop"></a>try_pop

Vyřadí položku z fronty, pokud je k dispozici. Tato metoda je bezpečná pro souběžnost.

```
bool try_pop(T& _Dest);
```

### <a name="parameters"></a>Parametry

*_Dest*<br/>
Odkaz na umístění pro uložení položky vyřazení z fronty.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se položka úspěšně zrušila z fronty, jinak **false** .

### <a name="remarks"></a>Poznámky

Pokud byla položka úspěšně odstraněna z fronty, parametr `_Dest` obdrží hodnotu dequeueed, původní hodnota uložená ve frontě je zničena a tato funkce vrátí **hodnotu true**. Pokud nebyla žádná položka k vyřazení z fronty, vrátí tato funkce `false` bez blokování a obsah `_Dest` parametr není definován.

`try_pop` je bezpečné pro souběžnost s voláním metod `push`, `try_pop`a `empty`.

##  <a name="unsafe_begin"></a>unsafe_begin

Vrátí iterátor typu `iterator` nebo `const_iterator` na začátek souběžné fronty. Tato metoda není bezpečná pro souběžnost.

```
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `iterator` nebo `const_iterator` na začátek souběžného objektu Queue.

### <a name="remarks"></a>Poznámky

Iterátory pro třídu `concurrent_queue` jsou primárně určeny pro ladění, jak jsou pomalé a iterace není bezpečná pro souběžnost s ohledem na jiné operace fronty.

##  <a name="unsafe_end"></a>unsafe_end

Vrátí iterátor typu `iterator` nebo `const_iterator` na konec souběžné fronty. Tato metoda není bezpečná pro souběžnost.

```
iterator unsafe_end();

const_iterator unsafe_end() const;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor typu `iterator` nebo `const_iterator` na konec souběžné fronty.

### <a name="remarks"></a>Poznámky

Iterátory pro třídu `concurrent_queue` jsou primárně určeny pro ladění, jak jsou pomalé a iterace není bezpečná pro souběžnost s ohledem na jiné operace fronty.

##  <a name="unsafe_size"></a>unsafe_size

Vrátí počet položek ve frontě. Tato metoda není bezpečná pro souběžnost.

```
size_type unsafe_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost souběžné fronty.

### <a name="remarks"></a>Poznámky

`unsafe_size` není bezpečná pro souběžnost a může poskytovat nesprávné výsledky, pokud jsou volány souběžně s voláním metod `push`, `try_pop`a `empty`.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
