---
title: "concurrent_queue – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords: concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9cb1f1618f140ad9183d50d8aaacc8e9cc59c75d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="concurrentqueue-class"></a>concurrent_queue – třída
`concurrent_queue` Třída je pořadí kontejneru třídu, která umožňuje first in, první ven přístup k jeho elementy. Umožňuje omezenou sadu souběžnosti bezpečných operace, jako například `push` a `try_pop`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ prvky, které mají být uloženy ve frontě.  
  
 `_Ax`  
 Typ, který představuje uložené allocator objekt, který zapouzdřuje informace o přidělení a zrušení přidělení paměti pro tuto frontu souběžných. Tento argument je volitelný a výchozí hodnota je `allocator<T>`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`allocator_type`|Typ, který reprezentuje allocator – třída souběžných fronty.|  
|`const_iterator`|Typ, který reprezentuje bez bezpečného přístupu `const` iterator přes elementů v souběžných fronty.|  
|`const_reference`|Typ, který obsahuje odkaz na `const` element uložené v souběžných fronty pro čtení a provádění `const` operace.|  
|`difference_type`|Typ, který poskytuje podepsaný vzdálenost mezi dvěma prvky v souběžných fronty.|  
|`iterator`|Typ, který reprezentuje není bezpečná pro přístup z více vláken iterator přes elementů v souběžných fronty.|  
|`reference`|Typ, který obsahuje odkaz na element uložené v souběžných fronty.|  
|`size_type`|Typ, který udává počet elementů v souběžných fronty.|  
|`value_type`|Typ, který představuje typ dat uložených v souběžných frontě.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[concurrent_queue](#ctor)|Přetíženo. Vytvoří souběžných fronty.|  
|[~ concurrent_queue – destruktor](#dtor)|Zničí souběžných fronty.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Vymazat](#clear)|Vymaže souběžných fronty zničení všechny aktuálně zařazených do fronty elementy. Tato metoda není bezpečná souběžnosti.|  
|[prázdný](#empty)|Testy, pokud v tuto chvíli je souběžných fronta prázdná tato metoda je volána. Tato metoda je bezpečné souběžnosti.|  
|[get_allocator –](#get_allocator)|Vrátí kopii allocator použitý k vytvoření souběžných fronty. Tato metoda je bezpečné souběžnosti.|  
|[push](#push)|Přetíženo. Enqueues položku na konci tail souběžných fronty. Tato metoda je bezpečné souběžnosti.|  
|[try_pop –](#try_pop)|Pokud je k dispozici, dequeues položky z fronty. Tato metoda je bezpečné souběžnosti.|  
|[unsafe_begin –](#unsafe_begin)|Přetíženo. Vrátí iterovat typu `iterator` nebo `const_iterator` na začátek souběžných fronty. Tato metoda není bezpečná souběžnosti.|  
|[unsafe_end –](#unsafe_end)|Přetíženo. Vrátí iterovat typu `iterator` nebo `const_iterator` na konec souběžných fronty. Tato metoda není bezpečná souběžnosti.|  
|[unsafe_size –](#unsafe_size)|Vrátí počet položek ve frontě. Tato metoda není bezpečná souběžnosti.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `concurrent_queue`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concurrent_queue.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="clear"></a>Vymazat 

 Vymaže souběžných fronty zničení všechny aktuálně zařazených do fronty elementy. Tato metoda není bezpečná souběžnosti.  
  
```
void clear();
```  
  
##  <a name="ctor"></a>concurrent_queue 

 Vytvoří souběžných fronty.  
  
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
 `_InputIterator`  
 Typ vstupu iterator, který určuje rozsah hodnot.  
  
 `_Al`  
 Třída alokátoru, která se má použít s tímto objektem.  
  
 `_OtherQ`  
 Zdroj `concurrent_queue` objekt, který chcete zkopírovat nebo přesunout elementy z.  
  
 `_Begin`  
 Pozice první prvek v rozsahu elementy, které se mají zkopírovat.  
  
 `_End`  
 Pozice první prvek mimo rozsah elementy, které se mají zkopírovat.  
  
### <a name="remarks"></a>Poznámky  
 Všechny konstruktory uložit objekt allocator `_Al` a inicializace fronty.  
  
 První konstruktor určuje prázdné frontě počáteční a explicitně určuje typ allocator má být použit.  
  
 Druhý konstruktor určuje kopii souběžných fronty `_OtherQ`.  
  
 Třetí konstruktor určuje přesunu souběžných fronty `_OtherQ`.  
  
 Čtvrtý konstruktor určuje poskytl iterator rozsah hodnot [ `_Begin`, `_End`).  
  
##  <a name="dtor"></a>~ concurrent_queue 

 Zničí souběžných fronty.  
  
```
~concurrent_queue();
```  
  
##  <a name="empty"></a>prázdný 

 Testy, pokud v tuto chvíli je souběžných fronta prázdná tato metoda je volána. Tato metoda je bezpečné souběžnosti.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud v tuto chvíli jsme hledá, byla prázdná souběžných fronty `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Když tato metoda je souběžnosti bezpečných s ohledem na volání metod `push`, `try_pop`, a `empty`, hodnota vrácená můžou být nesprávné doby se prozkoumá volající vlákno.  
  
##  <a name="get_allocator"></a>get_allocator – 

 Vrátí kopii allocator použitý k vytvoření souběžných fronty. Tato metoda je bezpečné souběžnosti.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie allocator použitý k vytvoření souběžných fronty.  
  
##  <a name="push"></a>push 

 Enqueues položku na konci tail souběžných fronty. Tato metoda je bezpečné souběžnosti.  
  
```
void push(const T& _Src);

void push(T&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
 Položka, která má být přidán do fronty.  
  
### <a name="remarks"></a>Poznámky  
 `push`je bezpečné souběžnosti s ohledem na volání metod `push`, `try_pop`, a `empty`.  
  
##  <a name="try_pop"></a>try_pop – 

 Pokud je k dispozici, dequeues položky z fronty. Tato metoda je bezpečné souběžnosti.  
  
```
bool try_pop(T& _Dest);
```  
  
### <a name="parameters"></a>Parametry  
 `_Dest`  
 Odkaz na umístění pro uložení dequeued položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud byla položka úspěšně dequeued `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Pokud byla položka úspěšně dequeued parametr `_Dest` obdrží dequeued hodnota zničena původní hodnotu do fronty, a vrátí tato funkce `true`. Pokud se žádná položka vyřazení z fronty, funkce vrátí hodnotu `false` bez blokování a obsah `_Dest` parametr nejsou definovány.  
  
 `try_pop`je bezpečné souběžnosti s ohledem na volání metod `push`, `try_pop`, a `empty`.  
  
##  <a name="unsafe_begin"></a>unsafe_begin – 

 Vrátí iterovat typu `iterator` nebo `const_iterator` na začátek souběžných fronty. Tato metoda není bezpečná souběžnosti.  
  
```
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace typu `iterator` nebo `const_iterator` na začátek objekt souběžných fronty.  
  
### <a name="remarks"></a>Poznámky  
 Iterátory pro `concurrent_queue` třídy jsou primárně určený pro ladění, jako jsou pomalé a iterace není bezpečné souběžnosti s ohledem na jiné operace fronty.  
  
##  <a name="unsafe_end"></a>unsafe_end – 

 Vrátí iterovat typu `iterator` nebo `const_iterator` na konec souběžných fronty. Tato metoda není bezpečná souběžnosti.  
  
```
iterator unsafe_end();

const_iterator unsafe_end() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterace typu `iterator` nebo `const_iterator` na konec souběžných fronty.  
  
### <a name="remarks"></a>Poznámky  
 Iterátory pro `concurrent_queue` třídy jsou primárně určený pro ladění, jako jsou pomalé a iterace není bezpečné souběžnosti s ohledem na jiné operace fronty.  
  
##  <a name="unsafe_size"></a>unsafe_size – 

 Vrátí počet položek ve frontě. Tato metoda není bezpečná souběžnosti.  
  
```
size_type unsafe_size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost souběžných fronty.  
  
### <a name="remarks"></a>Poznámky  
 `unsafe_size`není bezpečné souběžného zpracování a může způsobit nesprávné výsledky, pokud volána souběžně volání metod `push`, `try_pop`, a `empty`.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)
