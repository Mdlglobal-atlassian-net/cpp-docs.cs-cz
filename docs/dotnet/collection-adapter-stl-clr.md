---
title: "collection_adapter – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::collection_adapter
dev_langs: C++
helpviewer_keywords: collection_adapter class [STL/CLR]
ms.assetid: 31964058-1f50-48bf-82c2-b0b3cc8a7887
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 79dbc2ff2e47e7aa277a2176dbd8605c5a78c749
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="collectionadapter-stlclr"></a>collection_adapter (STL/CLR)
Zabalí typu .NET collection používat jako kontejner STL/CLR. A `collection_adapter` je třída šablony, která popisuje jednoduchého objektu kontejneru STL/CLR. Zabalí základní třídy knihovny (BCL) rozhraní a vrátí dvojici iterator, který používáte k manipulaci s řízené sekvenci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Coll>  
    ref class collection_adapter;  
  
template<>  
    ref class collection_adapter<  
        System::Collections::ICollection>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IEnumerable>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IList>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IDictionary>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::ICollection<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IEnumerable<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IList<Value>>;  
template<typename Key,  
    typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IDictionary<Key, Value>>;  
```  
  
#### <a name="parameters"></a>Parametry  
 Kol.  
 Typ zabalené kolekce.  
  
## <a name="specializations"></a>Specializace  
  
|Specializace|Popis|  
|--------------------|-----------------|  
|Rozhraní IEnumerable|Pořadí pomocí elementů.|  
|ICollection|Udržuje skupinu elementů.|  
|Rozhraní IList.|Udržuje seřazené skupinu elementů.|  
|IDictionary|Udržovat sadu {klíč a hodnotu} páry.|  
|Rozhraní IEnumerable\<hodnota >|Pořadí prostřednictvím typové elementy.|  
|ICollection\<hodnota >|Udržuje typové prvků.|  
|IList\<hodnota >|Udržuje uspořádanou skupinu typové elementy.|  
|IDictionary\<hodnota >|Udržuje sadu typu {klíč a hodnotu} páry.|  
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[collection_adapter::difference_type (STL/CLR)](../dotnet/collection-adapter-difference-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[collection_adapter::iterator (STL/CLR)](../dotnet/collection-adapter-iterator-stl-clr.md)|Typ iterátoru řízené sekvence|  
|[collection_adapter::key_type (STL/CLR)](../dotnet/collection-adapter-key-type-stl-clr.md)|Typ klíče slovníku.|  
|[collection_adapter::mapped_type (STL/CLR)](../dotnet/collection-adapter-mapped-type-stl-clr.md)|Typ hodnoty slovníku.|  
|[collection_adapter::Reference (STL/CLR)](../dotnet/collection-adapter-reference-stl-clr.md)|Typ odkazu na prvek|  
|[collection_adapter::size_type (STL/CLR)](../dotnet/collection-adapter-size-type-stl-clr.md)|Typ vzdálenosti se znaménkem mezi dvěma prvky|  
|[collection_adapter::value_type (STL/CLR)](../dotnet/collection-adapter-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[collection_adapter::Base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)|Označí zabalené BCL rozhraní.|  
|[collection_adapter::begin (STL/CLR)](../dotnet/collection-adapter-begin-stl-clr.md)|Určuje začátek řízené sekvence.|  
|[collection_adapter::collection_adapter (STL/CLR)](../dotnet/collection-adapter-collection-adapter-stl-clr.md)|Vytvoří objekt adaptéru.|  
|[collection_adapter::end (STL/CLR)](../dotnet/collection-adapter-end-stl-clr.md)|Určuje konec řízené sekvence.|  
|[collection_adapter::size (STL/CLR)](../dotnet/collection-adapter-size-stl-clr.md)|Spočítá počet prvků.|  
|[collection_adapter::swap (STL/CLR)](../dotnet/collection-adapter-swap-stl-clr.md)|Zamění obsah dvou kontejnerů.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[collection_adapter::Operator = (STL/CLR)](../dotnet/collection-adapter-operator-assign-stl-clr.md)|Nahradí uložené BCL popisovač.|  
  
## <a name="remarks"></a>Poznámky  
 Tuto třídu šablony můžete použít k manipulaci s BCL kontejneru jako kontejner STL/CLR. `collection_adapter` Uloží popisovač do rozhraní BCL, který naopak řídí pořadí elementů. A `collection_adapter` objekt `X` vrátí pár vstupní iterátory `X.begin()` a `X.end()` , které umožňují najdete prvky, v pořadí. Některé odborností, které vám také umožní zápisu `X.size()` k určení délky řízené sekvenci.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo adaptér >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [range_adapter – (STL/CLR)](../dotnet/range-adapter-stl-clr.md)   
 [make_collection – (STL/CLR)](../dotnet/make-collection-stl-clr.md)