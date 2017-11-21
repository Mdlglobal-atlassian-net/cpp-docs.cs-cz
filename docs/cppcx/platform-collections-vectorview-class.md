---
title: "Třída Platform::Collections::VectorView | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
dev_langs: C++
helpviewer_keywords: VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: c69052eec58bb84416561de93df845a09514490f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections::VectorView – třída
Představuje zobrazení sekvenční kolekcí objektů, které může být index individuálně získávat přístup jen pro čtení. Typ každý objekt v kolekci je určený parametrem šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T, typename E>  
   ref class VectorView sealed;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ elementů obsažených v `VectorView` objektu.  
  
 `E`  
 Určuje binární predikát pro testování rovnosti s hodnotami typu `T`. Výchozí hodnota je `std::equal_to<T>`.  
  
### <a name="remarks"></a>Poznámky  
 `VectorView` Třída implementuje [Windows::Foundation::Collections::IVectorView\<T >](http://go.microsoft.com/fwlink/p/?LinkId=262411) rozhraní a podpora pro standardní knihovny šablon iterátory.  
  
### <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[VectorView::VectorView](#ctor)|Inicializuje novou instanci třídy VectorView.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[VectorView::First](#first)|Vrátí iterátor, který určuje první prvek v VectorView.|  
|[VectorView::GetAt](#getat)|Načte element aktuální VectorView, označené v zadaném indexu.|  
|[VectorView::GetMany](#getmany)|Načte posloupnost položek z aktuální VectorView, počínaje zadaným indexem.|  
|[VectorView::IndexOf](#indexof)|Vyhledá zadanou položku v aktuální VectorView a pokud najde, vrátí index položky.|  
|[VectorView::Size](#size)|Vrátí počet prvků v aktuálním objektu VectorView.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `VectorView`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** collection.h  
  
 **Namespace:** Platform::Collections  

## <a name="first"></a>VectorView::First – metoda
Vrátí iterátor, který určuje první prvek v VectorView.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<T>^   
   First();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterator, který určuje první prvek v VectorView.  
  
### <a name="remarks"></a>Poznámky  
 Pohodlný způsob pro uložení iterator vrácený First() je přiřadit návratovou hodnotu proměnné, která je deklarovaný s **automaticky** zadejte odvození – klíčové slovo. Například `auto x = myVectorView->First();`.  
  


## <a name="getat"></a>VectorView::GetAt – metoda
Načte element aktuální VectorView, označené v zadaném indexu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
T GetAt(  
   UInt32 index  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `index`  
 Nulovým základem celé číslo bez znaménka určující určitý element v objektu VectorView.  
  
### <a name="return-value"></a>Návratová hodnota  
 Element určeného `index` parametr. Element typu je zadaný parametr šablony VectorView *T*.  
  


## <a name="getmany"></a>VectorView::GetMany – metoda
Načte posloupnost položek z aktuální VectorView, počínaje zadaným indexem.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
virtual unsigned int GetMany(  
   unsigned int startIndex,   
   ::Platform::WriteOnlyArray<T>^ dest  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `startIndex`  
 Index založený na nule spouštění položky, které chcete načíst.  
  
 `dest`  
 Když tato operace dokončí, pole položek, které začínají na element určeného `startIndex` a konec na posledním prvkem v VectorView.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek, které načíst.  
  


## <a name="indexof"></a>VectorView::IndexOf – metoda
Vyhledá zadanou položku v aktuální VectorView a pokud najde, vrátí index položky.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
virtual bool IndexOf(  
   T value,  
   unsigned int* index  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `value`  
 Položka k vyhledání.  
  
 `index`  
 Index založený na nule položky Pokud parametr `value` , jinak hodnota je 0.  
  
 `index` Parametru je 0, pokud položka je první prvek VectorView nebo položka nebyla nalezena. Pokud je vrácenou hodnotou `true`, položka byla nalezena a je první prvek; jinak, položka nebyla nalezena.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud zadaná položka není nalezena; v opačném `false`.  
  


## <a name="size"></a>VectorView::Size – metoda
Vrátí počet prvků v aktuálním objektu VectorView.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
  
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů v aktuální VectorView.  
  


## <a name="ctor"></a>VectorView::VectorView – konstruktor
Inicializuje novou instanci třídy VectorView.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
VectorView();  
explicit VectorView(  
   UInt32 size  
);  
VectorView(  
   UInt32 size,  
   T value  
);  
explicit VectorView(  
   const ::std::vector<T>& v  
);  
explicit VectorView(  
   ::std::vector<T>&& v  
);  
VectorView(  
   const T * ptr,  
   UInt32 size  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const T (&arr)[N]  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const ::std::array<T,  
   N>& a  
);  
  
explicit VectorView(  
   const ::Platform::Array<T>^ arr  
);  
  
template <  
   typename InIt  
>  
VectorView(  
   InItfirst,  
   InItlast  
);  
  
VectorView(  
   std::initializer_list<T> il  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `InIt`  
 Typ na kolekci objektů, který se používá k chybě při inicializaci aktuální VectorView.  
  
 IL  
 A [std::initializer_list](../standard-library/initializer-list-class.md) jehož elementy se použije k chybě při inicializaci VectorView.  
  
 `N`  
 Počet elementů v kolekci objektů, které slouží k inicializaci aktuální VectorView.  
  
 `size`  
 Počet elementů v VectorView.  
  
 `value`  
 Hodnota, která se používá k chybě při inicializaci každý prvek v aktuální VectorView.  
  
 `v`  
 [Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) k [std::vector](../standard-library/vector-class.md) používané k chybě při inicializaci aktuální VectorView.  
  
 `ptr`  
 Ukazatel na `std::vector` používané k chybě při inicializaci aktuální VectorView.  
  
 `arr`  
 A [Platform::Array](../cppcx/platform-array-class.md) objekt, který se používá k chybě při inicializaci aktuální VectorView.  
  
 `a`  
 A [std::array](../standard-library/array-class-stl.md) objekt, který se používá k chybě při inicializaci aktuální VectorView.  
  
 `first`  
 První prvek v pořadí objektů, které se používají k inicializaci aktuální VectorView. Typ `first` předávána prostřednictvím *ideální předávání*. Další informace najdete v tématu [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 `last`  
 Posledním prvkem v pořadí objektů, které se používají k inicializaci aktuální VectorView. Typ `last` předávána prostřednictvím *ideální předávání*. Další informace najdete v tématu [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  


  
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)   
 [Vytváření Windows Runtime komponent v jazyce C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md)