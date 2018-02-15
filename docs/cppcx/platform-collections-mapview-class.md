---
title: "Třída Platform::Collections::MapView | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
dev_langs:
- C++
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f55a980f0d4fcb6982adb4d40353a47ee2f4d120
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView – třída
Představuje zobrazení jen pro čtení do *mapy*, což je kolekce párů klíč hodnota.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename K,  
   typename V,  
   typename C = ::std::less<K>>  
ref class MapView sealed;  
```  
  
#### <a name="parameters"></a>Parametry  
 `K`  
 Typ klíče v dvojice klíč hodnota.  
  
 `V`  
 Typ hodnoty v páru klíč / hodnota.  
  
 `C`  
 Typ, který poskytuje funkce objekt, který můžete porovnat dvě hodnoty element jako klíči řazení určit jejich relativní pořadí v MapView. Ve výchozím nastavení [std::less\<kB >](../standard-library/less-struct.md).  
  
### <a name="remarks"></a>Poznámky  
 MapView je konkrétní implementaci C++ [Windows::Foundation::Collections::IMapView \<tisíc, V >](http://go.microsoft.com/fwlink/p/?LinkId=262409) rozhraní, které je předán přes rozhraní binární aplikace (ABI). Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
### <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[MapView::MapView](#ctor)|Inicializuje novou instanci třídy MapView.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[MapView::First](#first)|Vrátí první prvek v zobrazení mapy iterátor, který je inicializován.|  
|[MapView::HasKey](#haskey)|Určuje, zda aktuální MapView obsahuje zadaný klíč.|  
|[MapView::Lookup](#lookup)|Načte element v zadaný klíč v aktuálním objektu MapView.|  
|[MapView::Size](#size)|Vrátí počet prvků v aktuálním objektu MapView.|  
|[MapView::Split](#split)|Původní objekt MapView rozdělí na dva objekty MapView.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `MapView`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** collection.h  
  
 **Namespace:** Platform::Collections  


## <a name="first"></a> MapView::First – metoda
Vrátí iterátor, který určuje první prvek v zobrazení mapy.  
  
### <a name="syntax"></a>Syntaxe  
  
```    
virtual Windows::Foundation::Collections::IIterator<  
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator, který určuje první prvek v zobrazení mapy.  
  
### <a name="remarks"></a>Poznámky  
 Pohodlný způsob pro uložení iterator vrácený First() je přiřadit návratovou hodnotu proměnné, která je deklarovaný s **automaticky** zadejte odvození – klíčové slovo. Například `auto x = myMapView->First();`.  
  


## <a name="haskey"></a>  MapView::HasKey – metoda
Určuje, zda aktuální MapView obsahuje zadaný klíč.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
bool HasKey(K key);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč používaná k nalezení MapView elementu. Typ `key` je typename *tisíc*.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je nalezen klíč; v opačném `false`.  
  


##  <a name="lookup"></a> MapView::Lookup – metoda
Načte hodnotu z typu V, který je přidružen k zadanému klíči typu K.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
V Lookup(K key);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč používaná k nalezení element v MapView. Typ `key` je typename *tisíc*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která je spárován s `key`. Typ vrácené hodnoty je typename *V*.  
  


##  <a name="ctor"></a> MapView::MapView – konstruktor
Inicializuje novou instanci třídy MapView.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
explicit MapView(const C& comp = C());  
  
explicit MapView(const ::std::map<K, V, C>& m);  
  
explicit MapView(std::map<K, V, C>&& m);  
  
template <typename InIt> MapView(  
    InIt first,  
    InIt last,  
    const C& comp = C());  
  
MapView(
    ::std::initializer_list<std::pair<const K, V>> il,  
    const C& comp = C());  
```  
  
### <a name="parameters"></a>Parametry  
 `InIt`  
 Typename aktuální MapView.  
  
 `comp`  
 Funkce objekt, který můžete porovnat dvě hodnoty element jako klíči řazení určit jejich relativní pořadí v MapView.  
  
 `m`  
 Odkaz nebo [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k `map Class` používané k chybě při inicializaci aktuální MapView.  
  
 `first`  
 Vstupní iteraci prvním elementem v rozsahu prvků použitý k inicializaci aktuální MapView.  
  
 `last`  
 Vstupní iterator první elementu po celou řadu prvky používané k chybě při inicializaci aktuální MapView.  
  
 il  
 A [std::initializer_list < std::pair\<tisíc, V >>](../standard-library/initializer-list-class.md) jehož elementy se vloží do MapView.  



##  <a name="size"></a> MapView::Size – metoda
Vrátí počet prvků v aktuálním objektu MapView.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů v aktuální MapView.  
  


##  <a name="split"></a> MapView::Split – metoda
Aktuální objekt MapView rozdělí na dva objekty MapView. Tato metoda je nefunkční.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void Split(  
   Windows::Foundation::Collections::IMapView<  
                         K, V>^ * firstPartition,  
   Windows::Foundation::Collections::IMapView<  
                         K, V>^ * secondPartition);  
```  
  
### <a name="parameters"></a>Parametry  
 `firstPartition`  
 První část původní objekt MapView.  
  
 `secondPartition`  
 Druhá část původní objekt MapView.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda není v provozu; neprovede žádnou akci.  
    
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)