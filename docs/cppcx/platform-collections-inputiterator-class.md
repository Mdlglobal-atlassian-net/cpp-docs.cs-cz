---
title: Třída Platform::Collections::InputIterator | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
dev_langs:
- C++
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7188cba0655e2ca89f82b60ffe9ee4b8ce94633a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator – třída
Poskytuje standardní InputIterator knihovny šablony pro kolekce, které jsou odvozené z prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename X>  
class InputIterator;  
```  
  
#### <a name="parameters"></a>Parametry  
 `X`  
 Typename InputIterator šablony třídy.  
  
### <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`difference_type`|Ukazatel rozdíl (ptrdiff_t –).|  
|`iterator_category`|Kategorie vstupní iterator (:: std::input_iterator_tag).|  
|`pointer`|Ukazatel na `const X`|  
|`reference`|Odkaz na `const X`|  
|`value_type`|`X` Typename.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[InputIterator::InputIterator](#ctor)|Inicializuje novou instanci třídy InputIterator.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[InputIterator::operator! = – operátor](#operator-inequality)|Určuje, zda aktuální InputIterator se nerovná zadané InputIterator.|  
|[InputIterator::operator * – operátor](#operator-decrement)|Získá odkaz na element určeného aktuální InputIterator.|  
|[InputIterator::operator ++ – operátor](#operator-increment)|Zvýší aktuální InputIterator.|  
|[InputIterator::operator == – operátor](#operator-equality)|Určuje, zda je aktuální InputIterator rovná zadané InputIterator.|  
|[InputIterator::operator -> – operátor](#operator-arrow)|Načte adresu odkazuje aktuální InputIterator elementu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `InputIterator`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="ctor"></a>  InputIterator::InputIterator – konstruktor
Inicializuje novou instanci třídy InputIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
InputIterator();  
explicit InputIterator(Windows::Foundation::Collections<X>^ iter);  
```  
  
### <a name="parameters"></a>Parametry  
 `iter`  
 Iterator objekt.  
  


## <a name="operator-arrow"></a>  InputIterator::operator -&gt; – operátor
Načte adresu určeného aktuální InputIterator elementu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
pointer operator->() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresa určeného aktuální InputIterator elementu.  
  


## <a name="operator-dereference"></a>  InputIterator::operator * – operátor
Získá odkaz na element určeného aktuální InputIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Element určeného aktuální InputIterator.  
  


## <a name="operator-equality"></a>  InputIterator::operator == – operátor
Určuje, zda je aktuální InputIterator rovná zadané InputIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator== (const InputIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné InputIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud se rovná aktuální InputIterator `other`, jinak hodnota `false`.  
  


## <a name="operator-increment"></a>  InputIterator::operator ++ – operátor
Zvýší aktuální InputIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```    
InputIterator& operator++();   
InputIterator operator++(int);  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 První syntaxe zvýší a vrátí aktuální InputIterator. Druhý syntaxe vrátí kopii aktuální InputIterator a pak zvýší aktuální InputIterator.  
  
### <a name="remarks"></a>Poznámky  
 První syntaxe InputIterator předem zvýší aktuální InputIterator.  
  
 Druhý syntaxe po zvýší aktuální InputIterator. `int` Typu v druhé syntaxi označuje po přírůstek operaci, nebyl operand skutečné celé číslo.  
  


## <a name="operator-inequality"></a>  InputIterator::operator! = – operátor
Určuje, zda aktuální InputIterator se nerovná zadané InputIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator!=(const InputIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné InputIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud aktuální InputIterator není rovno `other`, jinak hodnota `false`.   

  
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)