---
title: "combinable – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
dev_langs:
- C++
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9bec5ce0e6679af71d8d3372fb939223691152a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="combinable-class"></a>combinable – třída
`combinable<T>` Objektu slouží jako vlákno privátní kopií dat, provádět výpočty dílčí uvolnění zámku místní během paralelní algoritmy. Na konci paralelní operace dílčí výpočty vlákno privátní můžete pak sloučit konečný výsledek. Tato třída je možné místo sdílené proměnné a může mít za následek zlepšování výkonu Pokud by jinak byly spoustu kolizí sdílené proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T>
class combinable;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ sloučené konečný výsledek. Tento typ musí mít konstruktor kopie a výchozí konstruktor.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[combinable](#ctor)|Přetíženo. Vytvoří nový `combinable` objektu.|  
|[~combinable Destructor](#dtor)|Zničí `combinable` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[clear](#clear)|Vymaže všechny zprostředkující výpočetní výsledky z předchozí využití.|  
|[kombinování](#combine)|Vypočítá konečná hodnota ze sady dílčí výpočty místní voláním functor zadané kombinační.|  
|[combine_each](#combine_each)|Vypočítá konečná hodnota ze sady dílčí výpočty místní voláním functor zadané kombinační jednou za výpočetní dílčí místní. Konečný výsledek je shromážděných řešením objekt funkce.|  
|[místní](#local)|Přetíženo. Vrátí odkaz na dílčí výpočet privátní přístup z více vláken.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator=](#operator_eq)|Přiřadí `combinable` objekt z jiné `combinable` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [paralelní kontejnery a objekty](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `combinable`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="clear"></a> Zrušte zaškrtnutí 

 Vymaže všechny zprostředkující výpočetní výsledky z předchozí využití.  
  
```
void clear();
```  
  
##  <a name="ctor"></a> combinable 

 Vytvoří nový `combinable` objektu.  
  
```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ objektu functor inicializace.  
  
 `_FnInitialize`  
 Funkci, která bude volána k inicializaci každou novou hodnotu privátní přístup z více vláken typu `T`. Operátor volání funkce s podpisem musí podporovat `T ()`.  
  
 `_Copy`  
 Existující `combinable` objekt, který má být zkopírován do této jeden.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje nové prvky s výchozím konstruktorem pro typ `T`.  
  
 Druhý konstruktor inicializuje nových elementů pomocí functor inicializace jako zadána `_FnInitialize` parametr.  
  
 Třetí konstruktor je konstruktor copy.  
  
##  <a name="dtor"></a> ~ combinable 

 Zničí `combinable` objektu.  
  
```
~combinable();
```  
  
##  <a name="combine">kombinování</a> 

 Vypočítá konečná hodnota ze sady dílčí výpočty místní voláním functor zadané kombinační.  
  
```
template<typename _Function>
T combine(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ objektu funkce, která bude volána kombinovat dvě dílčí výpočty místní.  
  
 `_FnCombine`  
 Functor, který slouží k kombinovat dílčí výpočty. Podpis je `T (T, T)` nebo `T (const T&, const T&)`, a musí být asociativní a komutativní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Konečný výsledek kombinace všechny výpočty dílčí privátní přístup z více vláken.  
  
##  <a name="combine_each"></a> combine_each 

 Vypočítá konečná hodnota ze sady dílčí výpočty místní voláním functor zadané kombinační jednou za výpočetní dílčí místní. Konečný výsledek je shromážděných řešením objekt funkce.  
  
```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ objektu funkce, která bude volána kombinovat jeden dílčí výpočet místní.  
  
 `_FnCombine`  
 Functor, který kombinuje jeden dílčí výpočtu. Podpis je `void (T)` nebo `void (const T&)`a musí být asociativní a komutativní.  
  
##  <a name="local">místní</a> 

 Vrátí odkaz na dílčí výpočet privátní přístup z více vláken.  
  
```
T& local();

T& local(bool& _Exists);
```  
  
### <a name="parameters"></a>Parametry  
 `_Exists`  
 Odkaz na logickou hodnotu. Logická hodnota odkazuje tento argument je možnost `true` když dílčí výpočet již byly na tento přístup z více vláken a nastaví `false` by šlo o první dílčí výpočet na tento přístup z více vláken.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na dílčí výpočet privátní přístup z více vláken.  
  
##  <a name="operator_eq"></a> operátor = 

 Přiřadí `combinable` objekt z jiné `combinable` objektu.  
  
```
combinable& operator= (const combinable& _Copy);
```  
  
### <a name="parameters"></a>Parametry  
 `_Copy`  
 Existující `combinable` objekt, který má být zkopírován do této jeden.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `combinable` objektu.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
