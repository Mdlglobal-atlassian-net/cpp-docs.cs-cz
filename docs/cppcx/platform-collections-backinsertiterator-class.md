---
title: "Třída Platform::Collections::BackInsertIterator | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
dev_langs:
- C++
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 23c8b657a6cafb720cf0be07e2e67b5af0d7767d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform::Collections::BackInsertIterator – třída
Představuje iterátor, který se vloží, nikoli přepíše elementy do back-end sekvenční kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T>  
class BackInsertIterator : 
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ položky v aktuální kolekci.  
  
### <a name="remarks"></a>Poznámky  
 Třída BackInsertIterator implementuje pravidla vyžadují [back_insert_iterator – třída](../standard-library/back-insert-iterator-class.md).  
  
### <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[BackInsertIterator::BackInsertIterator](#ctor)|Inicializuje novou instanci třídy BackInsertIterator.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[BackInsertIterator::operator* Operator](#operator-dereference)|Získá odkaz na aktuální BackInsertIterator.|  
|[BackInsertIterator::operator++ Operator](#operator-increment)|Vrátí odkaz na aktuální BackInsertIterator. Iterace je beze změny.|  
|[BackInsertIterator::operator= Operator](#operator-assign)|Připojí zadaný objekt na konec aktuální sekvenční kolekcí.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `BackInsertIterator`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** collection.h  
  
 **Namespace:** Platform::Collections  
  
---
## <a name="ctor"></a>  BackInsertIterator::BackInsertIterator – konstruktor
Inicializuje novou instanci třídy `BackInsertIterator` třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
explicit BackInsertIterator(  
   Windows::Foundation::Collections::IVector<T>^ v);  
```  
  
#### <a name="parameters"></a>Parametry  
 `v`  
 IVector\<T > objektu.  
  
### <a name="remarks"></a>Poznámky  
 A `BackInsertIterator` vloží elementy za posledním elementem objektu zadaného parametrem `v`.  
 
## <a name="operator-assign"></a>  BackInsertIterator::operator= Operator
Připojí zadaný objekt na konec aktuální sekvenční kolekcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```    
BackInsertIterator& operator=( const T& t);  
```  
  
#### <a name="parameters"></a>Parametry  
 `t`  
 Objekt, který se má připojit k aktuální kolekci.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na aktuální BackInsertIterator.  

## <a name="operator-dereference"></a>  BackInsertIterator::operator * – operátor
Získá odkaz na aktuální BackInsertIterator.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BackInsertIterator& operator*();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na aktuální BackInsertIterator.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor vrátí odkaz na aktuální BackInsertIterator; není pro libovolný element v aktuální kolekci.  
 
## <a name="operator-increment"></a>  BackInsertIterator::operator ++ – operátor
Vrátí odkaz na aktuální BackInsertIterator. Iterace je beze změny.  
  
## <a name="syntax"></a>Syntaxe  
  
``` 
  
BackInsertIterator& operator++();  
  
BackInsertIterator operator++(int);  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na aktuální BackInsertIterator.  
  
### <a name="remarks"></a>Poznámky  
 Návrh v prvním příkladu syntaxe předem zvýší aktuální BackInsertIterator a druhý syntaxe po zvýší aktuální BackInsertIterator. `int` Typu v druhé syntaxi označuje po přírůstek operaci, nebyl operand skutečné celé číslo.  
  
 Však tento operátor. ve skutečnosti nezmění BackInsertIterator. Tento operátor. místo toho vrátí odkaz na iterator beze změny, aktuální. Toto je stejné chování jako [operátor *](#dereference-operator).  
  
  
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)