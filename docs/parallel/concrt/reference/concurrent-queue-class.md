---
title: concurrent_queue – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d211d94903e411db5755bd57873b9d3e33ee54fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076486"
---
# <a name="concurrentqueue-class"></a>concurrent_queue – třída
`concurrent_queue` Třída je sekvence kontejner – třída, která umožňuje first-in, FIFO přístup k jeho prvkům. Umožňuje omezenou sadu operace bezpečné na souběžnosti, jako například `push` a `try_pop`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```  
  
#### <a name="parameters"></a>Parametry  
*T*<br/>
Datový typ prvků, které mají být uloženy ve frontě.  
  
*_Ax*<br/>
Typ představující uložený objekt alokátoru, který zapouzdřuje informace o přidělování a navracení zpět paměti pro tuto frontu souběžných. Tento argument je nepovinný a výchozí hodnota je `allocator<T>`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`allocator_type`|Typ, který představuje třídu alokátoru pro souběžná fronta.|  
|`const_iterator`|Typ, který představuje jiných – bezpečné pro vlákna `const` iterátoru přes prvky v souběžná fronta.|  
|`const_reference`|Typ, který poskytuje odkaz na `const` prvek uložený v souběžná fronta pro čtení a provádění `const` operace.|  
|`difference_type`|Typ, který poskytuje podepsaný vzdálenosti mezi dvěma prvky v souběžná fronta.|  
|`iterator`|Typ, která představuje iterátor vláknově bezpečné přes prvky v souběžná fronta.|  
|`reference`|Typ, který poskytuje odkaz na prvek uložený v souběžná fronta.|  
|`size_type`|Typ, který vrátí počet prvků v souběžná fronta.|  
|`value_type`|Typ, který představuje typ dat uložených v souběžná fronta.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[concurrent_queue](#ctor)|Přetíženo. Sestaví souběžná fronta.|  
|[~concurrent_queue Destructor](#dtor)|Zničí souběžná fronta.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Vymazat](#clear)|Vymaže souběžná fronta zničení všechny aktuálně zařazených do fronty elementy. Tato metoda není bezpečná pro souběžnost.|  
|[prázdný](#empty)|Testuje, zda je v tuto chvíli je prázdný souběžná fronta tato metoda je volána. Tato metoda je bezpečná pro souběžnost.|  
|[get_allocator](#get_allocator)|Vrátí kopii objektu Alokátor použitý k vytvoření souběžná fronta. Tato metoda je bezpečná pro souběžnost.|  
|[push](#push)|Přetíženo. Zařadí položku na konci ocáskem souběžná fronta. Tato metoda je bezpečná pro souběžnost.|  
|[try_pop](#try_pop)|Dequeues položky z fronty, pokud je k dispozici. Tato metoda je bezpečná pro souběžnost.|  
|[unsafe_begin](#unsafe_begin)|Přetíženo. Vrátí iterátor typu `iterator` nebo `const_iterator` začátek souběžná fronta. Tato metoda není bezpečná pro souběžnost.|  
|[unsafe_end](#unsafe_end)|Přetíženo. Vrátí iterátor typu `iterator` nebo `const_iterator` konec souběžná fronta. Tato metoda není bezpečná pro souběžnost.|  
|[unsafe_size](#unsafe_size)|Vrátí počet položek ve frontě. Tato metoda není bezpečná pro souběžnost.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `concurrent_queue`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concurrent_queue.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="clear"></a> Vymazat 

 Vymaže souběžná fronta zničení všechny aktuálně zařazených do fronty elementy. Tato metoda není bezpečná pro souběžnost.  
  
```
void clear();
```  
  
##  <a name="ctor"></a> concurrent_queue – 

 Sestaví souběžná fronta.  
  
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
Zdroj `concurrent_queue` objektu, který chcete zkopírovat nebo přesunout elementy ze.  
  
*_Zahájit*<br/>
Pozice prvního prvku v rozsahu prvků, které se mají zkopírovat.  
  
*_Ukončit*<br/>
Pozice prvního prvku mimo rozsah prvků, které se mají zkopírovat.  
  
### <a name="remarks"></a>Poznámky  
 Všechny konstruktory ukládají objekt alokátoru `_Al` a inicializace fronty.  
  
 První konstruktor určí prázdný počáteční fronty a explicitně určuje typ alokátoru, který se má použít.  
  
 Druhý konstruktor určuje kopii souběžná fronta `_OtherQ`.  
  
 Třetí konstruktor určuje pohyb souběžná fronta `_OtherQ`.  
  
 Čtvrtý konstruktor určuje hodnoty poskytnuté rozsahem iterátoru [ `_Begin`, `_End`).  
  
##  <a name="dtor"></a> ~ concurrent_queue – 

 Zničí souběžná fronta.  
  
```
~concurrent_queue();
```  
  
##  <a name="empty"></a> prázdný 

 Testuje, zda je v tuto chvíli je prázdný souběžná fronta tato metoda je volána. Tato metoda je bezpečná pro souběžnost.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud v tuto chvíli jsme se podívali, byla prázdná souběžná fronta `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Zatímco tato metoda je bezpečná pro souběžnost s ohledem na volání metody `push`, `try_pop`, a `empty`, vrácená hodnota může být nesprávný podle času je prozkoumat volajícího vlákna.  
  
##  <a name="get_allocator"></a> get_allocator 

 Vrátí kopii objektu Alokátor použitý k vytvoření souběžná fronta. Tato metoda je bezpečná pro souběžnost.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie Alokátor použitý k vytvoření souběžná fronta.  
  
##  <a name="push"></a> nabízených oznámení 

 Zařadí položku na konci ocáskem souběžná fronta. Tato metoda je bezpečná pro souběžnost.  
  
```
void push(const T& _Src);

void push(T&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
*_Src*<br/>
Položky, které chcete přidat do fronty.  
  
### <a name="remarks"></a>Poznámky  
 `push` je bezpečné na souběžnosti s ohledem na volání metody `push`, `try_pop`, a `empty`.  
  
##  <a name="try_pop"></a> try_pop – 

 Dequeues položky z fronty, pokud je k dispozici. Tato metoda je bezpečná pro souběžnost.  
  
```
bool try_pop(T& _Dest);
```  
  
### <a name="parameters"></a>Parametry  
*_Dest*<br/>
Odkaz na umístění pro uložení dequeued položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud byla položka úspěšně dequeued `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Pokud byla položka úspěšně dequeued parametr `_Dest` přijímá dequeued hodnotu, původní hodnota uložená ve frontě je zničen, a tato funkce vrací `true`. Pokud se žádné položky k odstranění z fronty, tato funkce vrací `false` bez blokování a obsah `_Dest` parametr nejsou definovány.  
  
 `try_pop` je bezpečné na souběžnosti s ohledem na volání metody `push`, `try_pop`, a `empty`.  
  
##  <a name="unsafe_begin"></a> unsafe_begin – 

 Vrátí iterátor typu `iterator` nebo `const_iterator` začátek souběžná fronta. Tato metoda není bezpečná pro souběžnost.  
  
```
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor typu `iterator` nebo `const_iterator` začátek souběžná fronta objektu.  
  
### <a name="remarks"></a>Poznámky  
 Iterátory pro `concurrent_queue` třídy jsou primárně určeny pro ladění, jako jsou pomalé a iterace není bezpečná pro souběžnost s ohledem na ostatní operace fronty.  
  
##  <a name="unsafe_end"></a> unsafe_end – 

 Vrátí iterátor typu `iterator` nebo `const_iterator` konec souběžná fronta. Tato metoda není bezpečná pro souběžnost.  
  
```
iterator unsafe_end();

const_iterator unsafe_end() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor typu `iterator` nebo `const_iterator` konec souběžná fronta.  
  
### <a name="remarks"></a>Poznámky  
 Iterátory pro `concurrent_queue` třídy jsou primárně určeny pro ladění, jako jsou pomalé a iterace není bezpečná pro souběžnost s ohledem na ostatní operace fronty.  
  
##  <a name="unsafe_size"></a> unsafe_size – 

 Vrátí počet položek ve frontě. Tato metoda není bezpečná pro souběžnost.  
  
```
size_type unsafe_size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost souběžná fronta.  
  
### <a name="remarks"></a>Poznámky  
 `unsafe_size` není bezpečná pro souběžnost a může poskytovat nesprávné výsledky, pokud současně volání metod volá `push`, `try_pop`, a `empty`.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
