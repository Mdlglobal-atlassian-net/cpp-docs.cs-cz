---
title: 'Platform::Collections:: vectorviewiterator – třída | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
dev_langs:
- C++
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f7894710957994faadcb22753c1fca389a13506
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597719"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections:: vectorviewiterator – třída
Poskytuje standardní knihovny šablon iterátor pro objekty, které jsou odvozeny z modulu Windows Runtime`IVectorView` rozhraní.  
  
 `ViewVectorIterator` je proxy iterátor, který ukládá prvky typu `VectorProxy<T>`. Objekt proxy je však téměř nikdy viditelné pro uživatelský kód. Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T>  
class VectorViewIterator;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastnost typename třídy VectorViewIterator šablony.  
  
### <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`difference_type`|Rozdíl ukazatelů (ptrdiff_t).|  
|`iterator_category`|Kategorie iterátor náhodného přístupu (:: std::random_access_iterator_tag).|  
|`pointer`|Ukazatel na vnitřní typ, který se vyžaduje k provedení VectorViewIterator.|  
|`reference`|Odkaz na vnitřní typ, který se vyžaduje k provedení VectorViewIterator.|  
|`value_type`|`T` Typename.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[VectorViewIterator::VectorViewIterator](#ctor)|Inicializuje novou instanci třídy VectorViewIterator.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[VectorViewIterator::operator-– operátor](#operator-minus)|Odečte buď zadaný počet prvků z aktuální iterace, což má za následek nové iterátor nebo iterátor zadané z aktuální iterace, což má za následek počet prvků mezi iterátory.|  
|[VectorViewIterator::operator--– operátor](#operator-decrement)|Sníží aktuální VectorViewIterator.|  
|[VectorViewIterator::operator! = – operátor](#operator-inequality)|Určuje, zda aktuální VectorViewIterator není roven zadané VectorViewIterator.|  
|[VectorViewIterator::operator * – operátor](#operator-dereference)|Získá odkaz na prvek určeném aktuálním VectorViewIterator.|  
|[VectorViewIterator::operator\[\]](#operator-at)|Získá odkaz na prvek, který je zadaný posun z aktuální VectorViewIterator.|  
|[VectorViewIterator::operator + – operátor](#operator-plus)|Vrátí VectorViewIterator, odkazující na prvek na zadané posunutí ze zadaného VectorViewIterator.|  
|[VectorViewIterator::operator ++ – operátor](#operator-increment)|Aktuální VectorViewIterator zvýší.|  
|[VectorViewIterator::operator += – operátor](#operator-plus-assign)|Zvětší aktuální VectorViewIterator podle zadaného posunu.|  
|[VectorViewIterator::operator < – operátor](#operator-less-than)|Označuje, zda aktuální VectorViewIterator je nižší než zadané VectorViewIterator.|  
|[VectorViewIterator::operator\<= – operátor](#operator-less-than-or-equals)|Označuje, zda aktuální VectorViewIterator je menší než nebo rovna hodnotě zadané VectorViewIterator.|  
|[VectorViewIterator::operator-= – operátor](#operator-minus-assign)|Sníží aktuální VectorViewIterator podle zadaného posunu.|  
|[VectorViewIterator::operator == – operátor](#operator-equality)|Určuje, zda aktuální VectorViewIterator rovná zadané VectorViewIterator.|  
|[VectorViewIterator::operator > – operátor](#operator-greater-than)|Označuje, zda je aktuální VectorViewIterator větší než zadaný VectorViewIterator.|  
|[VectorViewIterator::operator -> – operátor](#operator-arrow)|Načte adresu elementu, který odkazuje aktuální VectorViewIterator.|  
|[VectorViewIterator::operator > = – operátor](#operator-greater-than-or-equals)|Určuje, zda aktuální VectorViewIterator je větší než nebo rovna hodnotě zadané VectorViewIterator.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `VectorViewIterator`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** collection.h  
  
 **Namespace:** Platform::Collections –  

## <a name="operator-arrow"></a>  VectorViewIterator::operator -&gt; – operátor
Načte adresu elementu, který odkazuje aktuální VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota elementu, který se odkazuje aktuální VectorViewIterator.  
  
 Typ vrácené hodnoty je neurčená vnitřní typ, který se vyžaduje k provedení tohoto operátoru.  
  


## <a name="operator-decrement"></a>  VectorViewIterator::operator--– operátor
Sníží aktuální VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorViewIterator& operator--();  
VectorViewIterator operator--(int);  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 První syntaxe sníží a poté vrátí aktuální VectorViewIterator. Druhá syntaxe vrátí kopii aktuální VectorViewIterator a sníží aktuální VectorViewIterator.  
  
### <a name="remarks"></a>Poznámky  
 První syntaxe VectorViewIterator předem decrements aktuální VectorViewIterator.  
  
 Druhá syntaxe po decrements aktuální VectorViewIterator. `int` v druhé syntaxi označuje operaci po snížení, není skutečný celočíselný operand.  
  


## <a name="operator-dereference"></a>  VectorViewIterator::operator\* – operátor
Získá odkaz na prvek určeném aktuálním VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Element určeném aktuálním VectorViewIterator.  
  


## <a name="operator-equality"></a>  VectorViewIterator::operator == – operátor
Určuje, zda aktuální VectorViewIterator rovná zadané VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator==(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud se rovná aktuální VectorViewIterator `other`; v opačném případě `false`.  
  


## <a name="operator-greater-than"></a>  VectorViewIterator::operator&gt; – operátor
Označuje, zda je aktuální VectorViewIterator větší než zadaný VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
bool operator>(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je větší než aktuální VectorViewIterator `other`; v opačném případě `false`.  
  


## <a name="operator-greater-than-or-equals"></a>  VectorViewIterator::operator&gt;= – operátor
Určuje, zda aktuální VectorViewIterator je větší než nebo rovna hodnotě zadané VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
bool operator>=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud aktuální VectorViewIterator je větší než nebo rovna hodnotě `other`; v opačném případě `false`.  
  


## <a name="operator-increment"></a>  VectorViewIterator::operator ++ – operátor
Aktuální VectorViewIterator zvýší.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorViewIterator& operator++();  
VectorViewIterator operator++(int);  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 První syntaxe zvýší hodnotu a vrátí aktuální VectorViewIterator. Druhá syntaxe vrátí kopii objektu aktuální VectorViewIterator a potom zvýší aktuální VectorViewIterator.  
  
### <a name="remarks"></a>Poznámky  
 První syntaxe VectorViewIterator předem zvýší aktuální VectorViewIterator.  
  
 Druhá syntaxe po zvýší aktuální VectorViewIterator. `int` v druhé syntaxi označuje operaci po přírůstku není skutečný celočíselný operand.  
  


## <a name="operator-inequality"></a>  VectorViewIterator::operator! = – operátor
Určuje, zda aktuální VectorViewIterator není roven zadané VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator!=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud aktuální VectorViewIterator není roven `other`; v opačném případě `false`.  
  


## <a name="operator-less-than"></a>  VectorViewIterator::operator&lt; – operátor
Označuje, zda aktuální VectorIterator je nižší než zadané VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool operator<(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je aktuální VectorIterator menší než `other`; v opačném případě `false`.  
  


## <a name="operator-less-than-or-equals"></a>  VectorViewIterator::operator&lt;= – operátor
Označuje, zda aktuální VectorIterator je menší než nebo rovna hodnotě zadané VectorIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
bool operator<=(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `other`  
 Jiné VectorIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud aktuální VectorIterator je menší než nebo rovna `other`; v opačném případě `false`.  
  


## <a name="operator-minus"></a>  VectorViewIterator::operator-– operátor
Odečte buď zadaný počet prvků z aktuální iterace, což má za následek nové iterátor nebo iterátor zadané z aktuální iterace, což má za následek počet prvků mezi iterátory.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
VectorViewIterator operator-(difference_type n) const;  
  
difference_type operator-(const VectorViewIterator& other) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Počet prvků.  
  
 `other`  
 Jiné VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 Syntaxe první operátor vrací objekt VectorViewIterator, který je `n` prvky menší než aktuální VectorViewIterator. Syntaxe druhý operátor vrátí počet prvků mezi aktuálním a `other` VectorViewIterator.  
  


## <a name="operator-plus-equals"></a>  VectorViewIterator::operator += – operátor
Zvětší aktuální VectorViewIterator podle zadaného posunu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorViewIterator& operator+=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Posunutí celé číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktualizované VectorViewIterator.  
  


## <a name="operator-plus"></a>  VectorViewIterator::operator + – operátor
Vrátí VectorViewIterator, odkazující na prvek na zadané posunutí ze zadaného VectorViewIterator.  
  
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
 V druhém syntaxi typename VectorViewIterator.  
  
 `n`  
 Posunutí celé číslo.  
  
 `i`  
 V druhém syntaxi VectorViewIterator.  
  
### <a name="return-value"></a>Návratová hodnota  
 V první syntaxe VectorViewIterator, který odkazuje na element na zadaný posun z aktuální VectorViewIterator.  
  
 V druhém syntaxi VectorViewIterator, který odkazuje na element na zadaný posun od začátku parametru `i`.  
  


## <a name="operator-minus-assign"></a>  VectorViewIterator::operator-= – operátor
Sníží aktuální VectorIterator podle zadaného posunu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorViewIterator& operator-=(difference_type n);  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Posunutí celé číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktualizované VectorIterator.  
  


## <a name="operator-at"></a>  VectorViewIterator::operator\[\]
Získá odkaz na prvek, který je zadaný posun z aktuální VectorViewIterator.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
reference operator[](difference_type n) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `n`  
 Posunutí celé číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Prvek, který je posunout o `n` prvky z aktuální VectorViewIterator.  
  


## <a name="ctor"></a>  VectorViewIterator::VectorViewIterator konstruktor
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
 První příklad syntaxe je výchozí konstruktor. Druhý příklad syntaxe je explicitní konstruktor, který se používá ke konstrukci VectorViewIterator ze IVectorView\<T > objektu.  
  

  
## <a name="see-also"></a>Viz také  
 [Platforma Namespace](platform-namespace-c-cx.md)