---
title: "Třída Platform::Collections::VectorViewIterator | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
dev_langs: C++
helpviewer_keywords: VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b572d829c21c37457fc9fdab5f745616a6318ff1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator – třída
Poskytuje standardní knihovny šablon iterator pro objekty, které jsou odvozené z prostředí Windows Runtime`IVectorView` rozhraní.  
  
 `ViewVectorIterator`je iterator proxy, která ukládá elementy typu `VectorProxy<T>`. Objekt proxy serveru je však téměř žádné viditelné pro uživatelského kódu. Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T>  
class VectorViewIterator;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typename VectorViewIterator šablony třídy.  
  
### <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`difference_type`|Ukazatel rozdíl (ptrdiff_t –).|  
|`iterator_category`|Kategorie iterator náhodným přístupem (:: std::random_access_iterator_tag).|  
|`pointer`|Ukazatel na vnitřní typ, který je vyžadován pro implementaci VectorViewIterator.|  
|`reference`|Odkaz na vnitřní typ, který je vyžadován pro implementaci VectorViewIterator.|  
|`value_type`|`T` Typename.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[VectorViewIterator::VectorViewIterator](#ctor)|Inicializuje novou instanci třídy VectorViewIterator.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[VectorViewIterator::operator-– operátor](#operator-minus)|Odečítá od buď zadaný počet elementů od aktuální iterator je nové iterator nebo zadaný iterator z aktuální iterator je počet elementů mezi iterátory.|  
|[VectorViewIterator::operator – operátor](#operator-decrement)|Snižuje aktuální VectorViewIterator.|  
|[VectorViewIterator::operator! = – operátor](#operator-inequality)|Určuje, zda aktuální VectorViewIterator se nerovná zadané VectorViewIterator.|  
|[VectorViewIterator::operator * – operátor](#operator-dereference)|Získá odkaz na element určeného aktuální VectorViewIterator.|  
|[VectorViewIterator::operator\[\]](#operator-at)|Získá odkaz na element, který je zadaný přestavění z aktuální VectorViewIterator.|  
|[VectorViewIterator::operator + – operátor](#operator-plus)|Vrátí VectorViewIterator, který odkazuje na element v zadané posunutí ze zadaného VectorViewIterator.|  
|[VectorViewIterator::operator ++ – operátor](#operator-increment)|Zvýší aktuální VectorViewIterator.|  
|[VectorViewIterator::operator += – operátor](#operator-plus-assign)|Zvýší aktuální VectorViewIterator podle zadaného posunutí.|  
|[VectorViewIterator::operator < – operátor](#operator-less-than)|Určuje, zda aktuální VectorViewIterator je menší než zadaný VectorViewIterator.|  
|[VectorViewIterator::operator\<= – operátor](#operator-less-than-or-equals)|Určuje, zda aktuální VectorViewIterator je menší než nebo rovna hodnotě zadané VectorViewIterator.|  
|[VectorViewIterator::operator-= – operátor](#operator-minus-assign)|Snižuje aktuální VectorViewIterator podle zadaného posunutí.|  
|[VectorViewIterator::operator == – operátor](#operator-equality)|Určuje, zda je aktuální VectorViewIterator rovná zadané VectorViewIterator.|  
|[VectorViewIterator::operator > – operátor](#operator-greater-than)|Určuje, zda aktuální VectorViewIterator je větší než zadaná VectorViewIterator.|  
|[VectorViewIterator::operator -> – operátor](#operator-arrow)|Načte adresu odkazuje aktuální VectorViewIterator elementu.|  
|[VectorViewIterator::operator > = – operátor](#operator-greater-than-or-equals)|Určuje, zda aktuální VectorViewIterator je větší než nebo rovna hodnotě zadané VectorViewIterator.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `VectorViewIterator`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="operator-arrow"></a>VectorViewIterator::operator -&gt; – operátor
Načte adresu odkazuje aktuální VectorViewIterator elementu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota elementu, který je odkazován objektem aktuální VectorViewIterator.  
  
 Typ vrácené hodnoty je neurčené vnitřní typ, který je vyžadován pro implementaci tohoto operátoru.  
  


## <a name="operator-decrement"></a>VectorViewIterator::operator – operátor
Snižuje aktuální VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorViewIterator& operator--();  
VectorViewIterator operator--(int);  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 První snižuje syntaxe a poté vrátí aktuální VectorViewIterator. Druhý syntaxe vrátí kopii aktuální VectorViewIterator a snižují se vždy aktuální VectorViewIterator.  
  
### <a name="remarks"></a>Poznámky  
 První syntaxe VectorViewIterator předem decrements aktuální VectorViewIterator.  
  
 Druhý syntaxe po decrements aktuální VectorViewIterator. `int` Typu v druhé syntaxi označuje po snížení operaci, nebyl operand skutečné celé číslo.  
  


## <a name="operator-dereference"></a>VectorViewIterator::operator * – operátor
Získá odkaz na element určeného aktuální VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Element určeného aktuální VectorViewIterator.  
  


## <a name="operator-equality"></a>VectorViewIterator::operator == – operátor
Určuje, zda je aktuální VectorViewIterator rovná zadané VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator==(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud se rovná aktuální VectorViewIterator `other`, jinak hodnota `false`.  
  


## <a name="operator-greater-than"></a>VectorViewIterator::operator&gt; – operátor
Určuje, zda aktuální VectorViewIterator je větší než zadaná VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
bool operator>(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je větší než aktuální VectorViewIterator `other`, jinak hodnota `false`.  
  


## <a name="operator-greater-than-or-equals"></a>VectorViewIterator::operator&gt;= – operátor
Určuje, zda aktuální VectorViewIterator je větší než nebo rovna hodnotě zadané VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
bool operator>=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud aktuální VectorViewIterator je větší než nebo rovna hodnotě `other`, jinak hodnota `false`.  
  


## <a name="operator-increment"></a>VectorViewIterator::operator ++ – operátor
Zvýší aktuální VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorViewIterator& operator++();  
VectorViewIterator operator++(int);  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 První syntaxe zvýší a vrátí aktuální VectorViewIterator. Druhý syntaxe vrátí kopii aktuální VectorViewIterator a pak zvýší aktuální VectorViewIterator.  
  
### <a name="remarks"></a>Poznámky  
 První syntaxe VectorViewIterator předem zvýší aktuální VectorViewIterator.  
  
 Druhý syntaxe po zvýší aktuální VectorViewIterator. `int` Typu v druhé syntaxi označuje po přírůstek operaci, nebyl operand skutečné celé číslo.  
  


## <a name="operator-inequality"></a>VectorViewIterator::operator! = – operátor
Určuje, zda aktuální VectorViewIterator se nerovná zadané VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator!=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud aktuální VectorViewIterator není rovno `other`, jinak hodnota `false`.  
  


## <a name="operator-less-than"></a>VectorViewIterator::operator&lt; – operátor
Určuje, zda aktuální VectorIterator je menší než zadaný VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator<(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je aktuální VectorIterator menší než `other`, jinak hodnota `false`.  
  


## <a name="operator-less-than-or-equals"></a>VectorViewIterator::operator&lt;= – operátor
Určuje, zda aktuální VectorIterator je menší než nebo rovna hodnotě zadané VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
bool operator<=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud aktuální VectorIterator je menší než nebo rovno `other`, jinak hodnota `false`.  
  


## <a name="operator-minus"></a>VectorViewIterator::operator-– operátor
Odečítá od buď zadaný počet elementů od aktuální iterator je nové iterator nebo zadaný iterator z aktuální iterator je počet elementů mezi iterátory.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorViewIterator operator-(difference_type n) const;  
  
difference_type operator-(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Počet elementů.  
  
 `other`  
 Jiné VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první syntaxe operátor VectorViewIterator objekt, který je `n` elementy menší než aktuální VectorViewIterator. Druhý syntaxe operátor vrátí počet prvků mezi aktuální a `other` VectorViewIterator.  
  


## <a name="operator-plus-equals"></a>VectorViewIterator::operator += – operátor
Zvýší aktuální VectorViewIterator podle zadaného posunutí.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorViewIterator& operator+=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Posunutí celé číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktualizované VectorViewIterator.  
  


## <a name="operator-plus"></a>VectorViewIterator::operator + – operátor
Vrátí VectorViewIterator, který odkazuje na element v zadané posunutí ze zadaného VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorViewIterator operator+(difference_type n) const;  
  
template <typename T>   
inline VectorViewIterator<T> operator+  
   (ptrdiff_t n,   
   const VectorViewIterator<T>& i);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 V druhé syntaxe typename VectorViewIterator.  
  
 `n`  
 Posunutí celé číslo.  
  
 `i`  
 V druhé syntaxe VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 V první syntaxe VectorViewIterator, který odkazuje na element v zadané posunutí z aktuální VectorViewIterator.  
  
 V druhé syntaxi VectorViewIterator, který odkazuje na element v zadaný posun od začátku parametr `i`.  
  


## <a name="operator-minus-assign"></a>VectorViewIterator::operator-= – operátor
Snižuje aktuální VectorIterator podle zadaného posunutí.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorViewIterator& operator-=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Posunutí celé číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktualizované VectorIterator.  
  


## <a name="operator-at"></a>VectorViewIterator::operator\[\]
Získá odkaz na element, který je zadaný přestavění z aktuální VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference operator[](difference_type n) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Posunutí celé číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Element, který je posunout o `n` elementy z aktuální VectorViewIterator.  
  


## <a name="ctor"></a>VectorViewIterator::VectorViewIterator – konstruktor
Inicializuje novou instanci třídy VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorViewIterator();  
  
explicit VectorViewIterator(  
   Windows::Foundation::Collections::IVectorView<T>^ v  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `v`  
 IVectorView\<T > objektu.  
  
### <a name="remarks"></a>Poznámky  
 V prvním příkladu syntaxe je výchozí konstruktor. V druhém příkladu syntaxe je explicitní konstruktor, který se používá pro konstrukci VectorViewIterator z IVectorView\<T > objektu.  
  

  
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)