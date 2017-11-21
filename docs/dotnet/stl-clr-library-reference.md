---
title: Odkaz na knihovnu | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5906ffd662bb8b88c1c7ec42879da7f3730020f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stlclr-library-reference"></a>STL/CLR – Referenční dokumentace knihoven
Knihovny STL/CLR je balíčkovacím podmnožinu standardní knihovna C++ pro použití s C++ a rozhraní .NET Framework common language runtime (CLR). STL/CLR můžete všechny kontejnery, iterátory a algoritmy standardní knihovny ve spravovaném prostředí.  
  
 Použití STL/CLR:  
  
-   Patří hlavičky z **cliext –** zahrnují podadresáři místo obvyklé standardní knihovna C++ ekvivalenty.  
  
-   Kvalifikaci – názvy knihoven s `cliext::` místo `std::`.  
  
 STL/CLR zpřístupní obecné typy a rozhraní, které se používá ve scénářích mezi sestaveními v sestavení rozhraní .NET **Microsoft.VisualC.STLCLR.dll**. Tento soubor DLL je obsažena v rozhraní .NET Framework 3.5. Pokud je znovu distribuovat aplikace, která používá STL/CLR, musíte zahrnout rozhraní .NET Framework 3.5, jakož i jiné knihovny jazyka Visual C++, které používá váš projekt, v části závislosti projektu instalace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [cliext – Namespace](../dotnet/cliext-namespace.md)  
 Popisuje obor názvů, který obsahuje všechny typy knihovny STL/CLR.  
  
 [STL/CLR – kontejnery](../dotnet/stl-clr-containers.md)  
 Poskytuje přehled kontejnerů, které se nacházejí ve standardní knihovně C++, včetně požadavky na elementy kontejnerů, typy elementů, které lze vložit a vlastnictví problémy.  
  
 [Požadavky na elementy kontejnerů STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md)  
 Popisuje minimální požadavky pro všechny odkazové typy, které jsou vloženy do kontejnerů standardní knihovna C++.  
  
 [Postupy: převod typu .NET Collection na kontejner STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)  
 Popisuje, jak převést typu .NET collection na kontejner STL/CLR.  
  
 [Postupy: převod kontejneru STL/CLR na typ .NET Collection](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)  
 Popisuje, jak převést na typ .NET collection kontejner STL/CLR.  
  
 [Postupy: vystavení kontejneru STL/CLR ze sestavení](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)  
 Ukazuje, jak se zobrazí prvky několik kontejnerů STL/CLR, které jsou napsané v sestavení C++.  
  
 Kromě toho tato část také popisuje následující komponenty aplikace STL/CLR:  
  
|||  
|-|-|  
|[adaptér (STL/CLR)](../dotnet/adapter-stl-clr.md)|[algoritmus (STL/CLR)](../dotnet/algorithm-stl-clr.md)|  
|[deque (STL/CLR)](../dotnet/deque-stl-clr.md)|[pro každou v](../dotnet/for-each-in.md)|  
|[funkční (STL/CLR)](../dotnet/functional-stl-clr.md)|[hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)|  
|[hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)|[hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)|  
|[hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)|[seznam (STL/CLR)](../dotnet/list-stl-clr.md)|  
|[mapy (STL/CLR)](../dotnet/map-stl-clr.md)|[multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)|  
|[multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)|[číselný (STL/CLR)](../dotnet/numeric-stl-clr.md)|  
|[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)|[fronty (STL/CLR)](../dotnet/queue-stl-clr.md)|  
|[Sada (STL/CLR)](../dotnet/set-stl-clr.md)|[Zásobník (STL/CLR)](../dotnet/stack-stl-clr.md)|  
|[Nástroj (STL/CLR)](../dotnet/utility-stl-clr.md)|[vektor (STL/CLR)](../dotnet/vector-stl-clr.md)|  
  
## <a name="see-also"></a>Viz také  
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)