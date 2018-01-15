---
title: "concurrent_priority_queue – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords: concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1796351dc594712ef69ec5562f85501b30997104
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="concurrentpriorityqueue-class"></a>concurrent_priority_queue – třída
`concurrent_priority_queue` Třída je kontejner, který umožňuje více vláken současně nabízení a pop položek. Položky jsou odebrány v pořadí podle priority, kde je priorita určena functor, zadaný jako argument šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ prvky, které mají být uloženy ve frontě s prioritou.  
  
 `_Compare`  
 Typ objektu funkce, která můžete porovnat dvě hodnoty element jako klíči řazení určit jejich relativní pořadí ve frontě s prioritou. Tento argument je volitelný a binární predikát `less<T>` je výchozí hodnota.  
  
 `_Ax`  
 Typ, který představuje uložené allocator objekt, který zapouzdřuje podrobnosti o přidělení a zrušení přidělení paměti pro souběžné priority fronty. Tento argument je volitelný a výchozí hodnota je `allocator<T>`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`allocator_type`|Typ, který reprezentuje allocator – třída souběžných priority fronty.|  
|`const_reference`|Typ, který představuje const odkaz na element typu uložené v souběžných priority fronty.|  
|`reference`|Typ, který reprezentuje odkaz na element typu uložené v souběžných priority fronty.|  
|`size_type`|Typ, který udává počet elementů v souběžných priority fronty.|  
|`value_type`|Typ, který představuje datový typ, který je uložený ve frontě souběžných priority.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[concurrent_priority_queue](#ctor)|Přetíženo. Vytvoří souběžných priority fronty.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Vymazat](#clear)|Vymaže všechny elementy ve souběžných prioritu. Tato metoda není bezpečná souběžnosti.|  
|[prázdný](#empty)|Testy, pokud je v době prázdný souběžných priority fronty tato metoda je volána. Tato metoda je bezpečné souběžnosti.|  
|[get_allocator –](#get_allocator)|Vrátí kopii allocator použitý k vytvoření souběžných priority fronty. Tato metoda je bezpečné souběžnosti.|  
|[push](#push)|Přetíženo. Přidá element do souběžných priority fronty. Tato metoda je bezpečné souběžnosti.|  
|[velikost](#size)|Vrátí počet elementů ve frontě souběžných priority. Tato metoda je bezpečné souběžnosti.|  
|[swap](#swap)|Zamění obsah dvou souběžných priority fronty. Tato metoda není bezpečná souběžnosti.|  
|[try_pop –](#try_pop)|Odebere a vrátí nejvyšší prioritou element z fronty, pokud fronty je prázdný. Tato metoda je bezpečné souběžnosti.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operátor =](#operator_eq)|Přetíženo. Přiřadí obsah jiného `concurrent_priority_queue` k tomuto objektu. Tato metoda není bezpečná souběžnosti.|  
  
## <a name="remarks"></a>Poznámky  
 Podrobné informace o `concurrent_priority_queue` třídy najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `concurrent_priority_queue`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concurrent_priority_queue.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="clear"></a>Vymazat 

 Vymaže všechny elementy ve souběžných prioritu. Tato metoda není bezpečná souběžnosti.  
  
```
void clear();
```  
  
### <a name="remarks"></a>Poznámky  
 `clear`není bezpečné souběžnosti. Je nutné zajistit, že jsou nejsou žádná jiná vlákna při volání této metody vyvolání metody ve frontě souběžných s prioritou. `clear`není volné paměti.  
  
##  <a name="ctor"></a>concurrent_priority_queue 

 Vytvoří souběžných priority fronty.  
  
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
 `_InputIterator`  
 Typ vstupu iterator.  
  
 `_Al`  
 Třída alokátoru, která se má použít s tímto objektem.  
  
 `_Init_capacity`  
 Počáteční kapacitu `concurrent_priority_queue` objektu.  
  
 `_Begin`  
 Pozice první prvek v rozsahu elementy, které se mají zkopírovat.  
  
 `_End`  
 Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.  
  
 `_Src`  
 Zdroj `concurrent_priority_queue` objekt, který chcete zkopírovat nebo přesunout elementy z.  
  
### <a name="remarks"></a>Poznámky  
 Všechny konstruktory uložit objekt allocator `_Al` a inicializace priority fronty.  
  
 První konstruktor Určuje frontu prázdný počáteční priority a volitelně specifikuje přidělení.  
  
 Druhý konstruktor určuje prioritu fronty s počáteční kapacita `_Init_capacity` a volitelně specifikuje přidělení.  
  
 Třetí konstruktor určuje poskytl iterator rozsah hodnot [ `_Begin`, `_End`) a volitelně specifikuje přidělení.  
  
 Konstruktory čtvrté a páté zadejte kopii priority fronty `_Src`.  
  
 Konstruktory šesté a sedmého zadejte přesunu priority fronty `_Src`.  
  
##  <a name="empty"></a>prázdný 

 Testy, pokud je v době prázdný souběžných priority fronty tato metoda je volána. Tato metoda je bezpečné souběžnosti.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud se v tuto chvíli byla zavolána funkce, prázdný priority fronty `false` jinak.  
  
##  <a name="get_allocator"></a>get_allocator – 

 Vrátí kopii allocator použitý k vytvoření souběžných priority fronty. Tato metoda je bezpečné souběžnosti.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie allocator použitý k vytvoření `concurrent_priority_queue` objektu.  
  
##  <a name="operator_eq"></a>operátor = 

 Přiřadí obsah jiného `concurrent_priority_queue` k tomuto objektu. Tato metoda není bezpečná souběžnosti.  
  
```
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
 Zdroj `concurrent_priority_queue` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `concurrent_priority_queue` objektu.  
  
##  <a name="push"></a>push 

 Přidá element do souběžných priority fronty. Tato metoda je bezpečné souběžnosti.  
  
```
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```  
  
### <a name="parameters"></a>Parametry  
 `_Elem`  
 Elementu, který chcete přidat do souběžných priority fronty.  
  
##  <a name="size"></a>velikost 

 Vrátí počet elementů ve frontě souběžných priority. Tato metoda je bezpečné souběžnosti.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů v této `concurrent_priority_queue` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Vrácený velikost záruku, že se mají zahrnout všechny elementy přidané ve volání funkce `push`. Je však nemusí odrážet výsledky čekajících souběžných operací.  
  
##  <a name="swap"></a>swap 

 Zamění obsah dvou souběžných priority fronty. Tato metoda není bezpečná souběžnosti.  
  
```
void swap(concurrent_priority_queue& _Queue);
```  
  
### <a name="parameters"></a>Parametry  
 `_Queue`  
 `concurrent_priority_queue` Objekt, který chcete Prohodit obsah s.  
  
##  <a name="try_pop"></a>try_pop – 

 Odebere a vrátí nejvyšší prioritou element z fronty, pokud fronty je prázdný. Tato metoda je bezpečné souběžnosti.  
  
```
bool try_pop(reference _Elem);
```  
  
### <a name="parameters"></a>Parametry  
 `_Elem`  
 Odkaz na proměnnou, který vyplní s nejvyšší prioritou elementu, pokud je fronta není prázdný.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud se hodnota odebrány, `false` jinak.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md)



