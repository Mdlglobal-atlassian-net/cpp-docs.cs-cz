---
title: "Třída Platform::Collections::VectorIterator | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COLLECTION/Platform::Collections::VectorIterator::VectorIterator
dev_langs: C++
helpviewer_keywords: VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 703035c7a5b2b32df95f83b42327b0965c98b4fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator – třída
Poskytuje standardní knihovny šablon iterator pro objekty, které jsou odvozené z rozhraní Windows Runtime IVector.  
  
 VectorIterator je iterator proxy, která ukládá elementy typu VectorProxy\<T >. Objekt proxy serveru je však téměř žádné viditelné pro uživatelského kódu. Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T>  
class VectorIterator;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typename VectorIterator šablony třídy.  
  
### <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`difference_type`|Ukazatel rozdíl (ptrdiff_t –).|  
|`iterator_category`|Kategorie iterator náhodným přístupem (:: std::random_access_iterator_tag).|  
|`pointer`|Ukazatel na interní typ, Platform::Collections::Details::VectorProxy\<T >, která je potřeba pro implementaci VectorIterator.|  
|`reference`|Odkaz na typ interní Platform::Collections::Details::VectorProxy\<T >,, to je nezbytné k provedení VectorIterator.|  
|`value_type`|`T` Typename.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[VectorIterator::VectorIterator](#ctor)|Inicializuje novou instanci třídy VectorIterator.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[VectorIterator::operator-– operátor](#operator-minus)|Odečítá od buď zadaný počet elementů od aktuální iterator je nové iterator nebo zadaný iterator z aktuální iterator je počet elementů mezi iterátory.|  
|[VectorIterator::operator – operátor](#operator-decrement)|Snižuje aktuální VectorIterator.|  
|[VectorIterator::operator! = – operátor](#operator-inequality)|Určuje, zda aktuální VectorIterator se nerovná zadané VectorIterator.|  
|[VectorIterator::operator * – operátor](#operator-dereference)|Získá odkaz na element určeného aktuální VectorIterator.|  
|[VectorIterator::operator\[\]](#operator-at)|Získá odkaz na element, který je zadaný přestavění z aktuální VectorIterator.|  
|[VectorIterator::operator + – operátor](#operator-plus)|Vrátí VectorIterator, který odkazuje na element v zadané posunutí ze zadaného VectorIterator.|  
|[VectorIterator::operator ++ – operátor](#operator-increment)|Zvýší aktuální VectorIterator.|  
|[VectorIterator::operator += – operátor](#operator-plus-assign)|Zvýší aktuální VectorIterator podle zadaného posunutí.|  
|[VectorIterator::operator < – operátor](#operator-less-than)|Určuje, zda aktuální VectorIterator je menší než zadaný VectorIterator.|  
|[VectorIterator::operator\<= – operátor](#operator-less-than-or-equals)|Určuje, zda aktuální VectorIterator je menší než nebo rovna hodnotě zadané VectorIterator.|  
|[VectorIterator::operator-= – operátor](#operator-subtract-assign)|Snižuje aktuální VectorIterator podle zadaného posunutí.|  
|[VectorIterator::operator == – operátor](#operator-equality)|Určuje, zda je aktuální VectorIterator rovná zadané VectorIterator.|  
|[VectorIterator::operator > – operátor](#operator-greater-than)|Určuje, zda aktuální VectorIterator je větší než zadaná VectorIterator.|  
|[VectorIterator::operator -> – operátor](#operator-arrow)|Načte adresu odkazuje aktuální VectorIterator elementu.|  
|[VectorIterator::operator > = – operátor](#operator-greater-than-or-equal)|Určuje, zda aktuální VectorIterator je větší než nebo rovna hodnotě zadané VectorIterator.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `VectorIterator`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="operator-arrow"></a>VectorIterator::operator -&gt; – operátor
Načte adresu odkazuje aktuální VectorIterator elementu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota elementu, který je odkazován objektem aktuální VectorIterator.  
  
 Typ vrácené hodnoty je neurčené vnitřní typ, který je vyžadován pro implementaci tohoto operátoru.  
  


## <a name="operator-decrement"></a>VectorIterator::operator – operátor
Snižuje aktuální VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorIterator& operator--();  
VectorIterator operator--(int);  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 První snižuje syntaxe a poté vrátí aktuální VectorIterator. Druhý syntaxe vrátí kopii aktuální VectorIterator a snižují se vždy aktuální VectorIterator.  
  
### <a name="remarks"></a>Poznámky  
 První syntaxe VectorIterator předem decrements aktuální VectorIterator.  
  
 Druhý syntaxe po decrements aktuální VectorIterator. `int` Typu v druhé syntaxi označuje po snížení operaci, nebyl operand skutečné celé číslo.  
  


## <a name="operator-dereference"></a>VectorIterator::operator * – operátor
Načte adresu určeného aktuální VectorIterator elementu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Element určeného aktuální VectorIterator.  
  


## <a name="operator-equality"></a>VectorIterator::operator == – operátor
Určuje, zda je aktuální VectorIterator rovná zadané VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator==(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud se rovná aktuální VectorIterator `other`, jinak hodnota `false`.  
  


## <a name="operator-greater-than"></a>VectorIterator::operator&gt; – operátor
Určuje, zda aktuální VectorIterator je větší než zadaná VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
bool operator>(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je větší než aktuální VectorIterator `other`, jinak hodnota `false`.  
  


## <a name="operator-greater-than-or-equals"></a>VectorIterator::operator&gt;= – operátor
Určuje, zda aktuální VectorIterator je větší než nebo rovna hodnotě zadané VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
bool operator>=(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud aktuální VectorIterator je větší než nebo rovna hodnotě `other`, jinak hodnota `false`.    


## <a name="operator-increment"></a>VectorIterator::operator ++ – operátor
Zvýší aktuální VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```    
VectorIterator& operator++();  
VectorIterator operator++(int);  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 První syntaxe zvýší a vrátí aktuální VectorIterator. Druhý syntaxe vrátí kopii aktuální VectorIterator a pak zvýší aktuální VectorIterator.  
  
### <a name="remarks"></a>Poznámky  
 První syntaxe VectorIterator předem zvýší aktuální VectorIterator.  
  
 Druhý syntaxe po zvýší aktuální VectorIterator. `int` Typu v druhé syntaxi označuje po přírůstek operaci, nebyl operand skutečné celé číslo.  
  


## <a name="operator-inequality"></a>VectorIterator::operator! = – operátor
Určuje, zda aktuální VectorIterator se nerovná zadané VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator!=(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud aktuální VectorIterator není rovno `other`, jinak hodnota `false`.  
  


## <a name="operator-less-than"></a>VectorIterator::operator&lt; – operátor
Určuje, zda aktuální VectorIterator je menší než zadaný VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
bool operator<(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je aktuální VectorIterator menší než `other`, jinak hodnota `false`.  
  


## <a name="operator-less-than-or-equals"></a>VectorIterator::operator&lt;= – operátor
Určuje, zda aktuální VectorIterator je menší než nebo rovna hodnotě zadané VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
bool operator<=(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud aktuální VectorIterator je menší než nebo rovno `other`, jinak hodnota `false`.  
  


## <a name="operator-minus"></a>VectorIterator::operator-– operátor
Odečítá od buď zadaný počet elementů od aktuální iterator je nové iterator nebo zadaný iterator z aktuální iterator je počet elementů mezi iterátory.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorIterator operator-(difference_type n) const;  
  
difference_type operator-(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Počet elementů.  
  
 `other`  
 Jiné VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první syntaxe operátor VectorIterator objekt, který je `n` elementy menší než aktuální VectorIterator. Druhý syntaxe operátor vrátí počet prvků mezi aktuální a `other` VectorIterator.  
  


## <a name="operator-plus-assign"></a>VectorIterator::operator += – operátor
Zvýší aktuální VectorIterator podle zadaného posunutí.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorIterator& operator+=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Posunutí celé číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktualizované VectorIterator.  
  


## <a name="operator-plus"></a>ectorIterator::operator + – operátor
Vrátí VectorIterator, který odkazuje na element v zadané posunutí ze zadaného VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorIterator operator+(difference_type n);  
  
template <typename T>  
inline VectorIterator<T> operator+(
  ptrdiff_t n, 
  const VectorIterator<T>& i);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 V druhé syntaxe typename VectorIterator.  
  
 `n`  
 Posunutí celé číslo.  
  
 `i`  
 V druhé syntaxe VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 V první syntaxe VectorIterator, který odkazuje na element v zadané posunutí z aktuální VectorIterator.  
  
 V druhé syntaxi VectorIterator, který odkazuje na element v zadaný posun od začátku parametr `i`.  
  
### <a name="remarks"></a>Poznámky  
 V prvním příkladu syntaxe  
  


## <a name="operator-minus-equals"></a>VectorIterator::operator-= – operátor
Snižuje aktuální VectorIterator podle zadaného posunutí.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorIterator& operator-=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Posunutí celé číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktualizované VectorIterator.  
  


## <a name="operator-at"></a>VectorIterator::operator\[\]
Získá odkaz na element, který je zadaný přestavění z aktuální VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```    
reference operator[](difference_type n) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Posunutí celé číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Element, který je posunout o `n` elementy z aktuální VectorIterator.  
  


## <a name="ctor"></a>VectorIterator::VectorIterator – konstruktor
Inicializuje novou instanci třídy VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```    
VectorIterator();  
  
explicit VectorIterator(  
   Windows::Foundation::Collections::IVector<T>^ v);  
```  
  
### <a name="parameters"></a>Parametry  
 `v`  
 IVector\<T > objektu.  
  
### <a name="remarks"></a>Poznámky  
 V prvním příkladu syntaxe je výchozí konstruktor. V druhém příkladu syntaxe je explicitní konstruktor, který se používá pro konstrukci VectorIterator z IVector\<T > objektu.  
  


  
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)