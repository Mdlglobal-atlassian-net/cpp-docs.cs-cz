---
title: "Platform::Collections:: unorderedmapview – třída | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 13e38563fe542eda08f436439ce3ad91a3e7a53e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView – třída
Představuje zobrazení jen pro čtení do *mapy*, což je kolekce párů klíč hodnota.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
   typename K,  
   typename V,  
   typename C = ::std::equal_to<K>>  
ref class UnorderedMapView sealed;  
```  
  
#### <a name="parameters"></a>Parametry  
 `K`  
 Typ klíče v dvojice klíč hodnota.  
  
 `V`  
 Typ hodnoty v páru klíč / hodnota.  
  
 `C`  
 Typ, který poskytuje funkce objekt, který můžete porovnat dvě hodnoty klíče rovnosti. Ve výchozím nastavení [std::equal_to\<kB >](../standard-library/equal-to-struct.md)  
  
### <a name="remarks"></a>Poznámky  
 UnorderedMapView je konkrétní implementaci C++ [Windows::Foundation::Collections::IMapView\<tisíc, V >](http://go.microsoft.com/fwlink/p/?LinkId=262409) rozhraní, které je předán přes rozhraní binární aplikace (ABI). Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).  
  
### <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Unorderedmapview::unorderedmapview –](#ctor)|Inicializuje novou instanci třídy UnorderedMapView.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Unorderedmapview::First –](#first)|Vrátí první prvek v zobrazení mapy iterátor, který je inicializován.|  
|[Unorderedmapview::haskey –](#haskey)|Určuje, zda aktuální UnorderedMapView obsahuje zadaný klíč.|  
|[Unorderedmapview::Lookup –](#lookup)|Načte element v zadaný klíč v aktuálním objektu UnorderedMapView.|  
|[Unorderedmapview::size –](#size)|Vrátí počet prvků v aktuálním objektu UnorderedMapView.|  
|[Unorderedmapview::split –](#split)|Původní objekt UnorderedMapView rozdělí na dva objekty UnorderedMapView.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `UnorderedMapView`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="first"></a>Unorderedmapview::First – metoda
Vrátí iterátor, který určuje první [Windows::Foundation::Collections::IKeyValuePair\<tisíc, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) element v neuspořádaný mapy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp   
virtual Windows::Foundation::Collections::IIterator<  
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^   
    First();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator, který určuje první prvek v zobrazení mapy.  
  
### <a name="remarks"></a>Poznámky  
 Pohodlný způsob pro uložení iterator vrácený First() je přiřadit návratovou hodnotu proměnné, která je deklarovaný s **automaticky** zadejte odvození – klíčové slovo. Například `auto x = myMapView->First();`.  
  


## <a name="haskey"></a>Unorderedmapview::haskey – metoda
Určuje, zda aktuální UnorderedMap obsahuje zadaný klíč.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
bool HasKey(K key);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč používaný k vyhledání prvku. Typ `key` je typename *tisíc*.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je nalezen klíč; v opačném `false`.  
  


## <a name="lookup"></a>Unorderedmapview::Lookup – metoda
Načte hodnotu z typu V, který je přidružen k zadanému klíči typu K.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
V Lookup(K key);  
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč používaná k nalezení element v UnorderedMapView. Typ `key` je typename *tisíc*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která je spárován s `key`. Typ vrácené hodnoty je typename *V*.  
  


## <a name="size"></a>Unorderedmapview::size – metoda
Vrátí počet [Windows::Foundation::Collections::IKeyValuePair\<tisíc, V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) elementů v UnorderedMapView.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp    
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů v Neseřazený MapView.  
  


## <a name="split"></a>Unorderedmapview::split – metoda
Aktuální objekt UnorderedMapView rozdělí na dva objekty UnorderedMapView. Tato metoda je nefunkční.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
void Split(  
   Windows::Foundation::Collections::IMapView<  
                         K,V>^ * firstPartition,  
   Windows::Foundation::Collections::IMapView<  
                         K,V>^ * secondPartition);  
```  
  
### <a name="parameters"></a>Parametry  
 `firstPartition`  
 První část původní objekt UnorderedMapView.  
  
 `secondPartition`  
 Druhá část původní objekt UnorderedMapView.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda není v provozu; neprovede žádnou akci.  
  


## <a name="ctor"></a>Unorderedmapview::unorderedmapview – konstruktor
Inicializuje novou instanci třídy UnorderedMapView.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
UnorderedMapView();    
explicit UnorderedMapView(size_t n);   
UnorderedMapView(size_t n, const H& h);   
UnorderedMapView(size_t n, const H& h, const P& p);  
  
explicit UnorderedMapView(  
    const std::unordered_map<K, V, H, P>& m);  
explicit UnorderedMapView(  
    std::unordered_map<K, V, H, P>&& m);  
  
template <typename InIt> UnorderedMapView(InIt first, InIt last );  
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h,  
    const P& p );  
  
UnorderedMapView(std::initializer_list<std::pair<const K, V>);  
  
UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n   
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h);  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h,  
    const P& p );  
```  
  
### <a name="parameters"></a>Parametry  
 n  
 Počet elementů pro předběžné přidělení místa pro.  
  
 `InIt`  
 Typename UnorderedMapView.  
  
 `H`  
 Funkce objekt, který můžete hodnotu hash pro klíč. Použije se výchozí hodnota [std::hash\<kB >](http://msdn.microsoft.com/en-us/54f67435-af9d-4217-a29d-fa4d2491a104) pro typy, `std::hash` podporuje.  
  
 `P`  
 Typ, který poskytuje funkce objekt, který můžete porovnat dva klíče určit jejich rovnosti. Použije se výchozí hodnota [std::equal_to\<kB >](../standard-library/equal-to-struct.md).  
  
 `m`  
 Odkaz nebo [hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k [std::unordered_map](../standard-library/unordered-map-class.md) používané k chybě při inicializaci UnorderedMapView.  
  
 `first`  
 Vstupní iteraci prvním elementem v rozsahu prvků použitý k inicializaci UnorderedMapView.  
  
 `last`  
 Vstupní iterator první elementu po celou řadu prvky používané k chybě při inicializaci UnorderedMapView.  
   
## <a name="see-also"></a>Viz také  
 [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md)   
 [Windows::Foundation::IMapView](http://go.microsoft.com/fwlink/p/?LinkId=262409)