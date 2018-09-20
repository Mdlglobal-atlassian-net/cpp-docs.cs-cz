---
title: Referenční dokumentace knihoven STL/CLR | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 78dc5c57ca000dfa03dba640c46cec16aaca133f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429471"
---
# <a name="stlclr-library-reference"></a>STL/CLR – Referenční dokumentace knihoven

Knihovna STL/CLR je obal podmnožiny standardní knihovny C++ pro použití s C++ a .NET Framework common language runtime (CLR). STL/CLR můžete kontejnerů, iterátorů a algoritmů standardní knihovny ve spravovaném prostředí.

Použití STL/CLR:

- Zahrnutá záhlaví z **cliext –** obsahují podadresáře místo obvyklých ekvivalentů standardní knihovny C++.

- Kvalifikovat názvy knihovny `cliext::` místo `std::`.

STL/CLR poskytují obecné typy a rozhraní, které poté používají ve scénářích mezi sestaveními v rámci sestavení .NET **Microsoft.VisualC.STLCLR.dll**. Tato knihovna DLL je součástí rozhraní .NET Framework 3.5. Pokud redistribuujete aplikaci, která používá STL/CLR, musíte zahrnout rozhraní .NET Framework 3.5, jakož i jiné knihovny Visual C++, které používá váš projekt, v oblasti závislostí projektu instalace.

## <a name="in-this-section"></a>V tomto oddílu

[Obor názvů cliext](../dotnet/cliext-namespace.md)<br/>
Tento článek popisuje obor názvů, který obsahuje všechny typy knihovny STL/CLR.

[Kontejnery STL/CLR](../dotnet/stl-clr-containers.md)<br/>
Poskytuje přehled kontejnerů, které se nacházejí ve standardní knihovně jazyka C++, včetně požadavků na prvky kontejneru, typy prvků, které lze vložit a potíže s vlastnictvím.

[Požadavky n prvky kontejneru STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
Popisuje minimální požadavky pro všechny typy odkazů, které jsou vloženy do kontejnery standardní knihovny C++.

[Postupy: Převod kolekce .NET na kontejner STL/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
Popisuje, jak převést kolekci .NET na kontejner STL/CLR.

[Postupy: Převod kontejneru STL/CLR na kolekci .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
Popisuje, jak převést kontejner STL/CLR na kolekci .NET.

[Postupy: Zveřejnění kontejneru STL/CLR ze sestavení](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
Ukazuje, jak zobrazit prvky několika kontejnerů STL/CLR napsané v sestavení C++.

Kromě toho tato část také popisuje následující součásti STL/CLR:

|||
|-|-|
|[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)|[algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)|
|[deque (STL/CLR)](../dotnet/deque-stl-clr.md)|[for each, in](../dotnet/for-each-in.md)|
|[functional (STL/CLR)](../dotnet/functional-stl-clr.md)|[hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)|
|[hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)|[hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)|
|[hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)|[list (STL/CLR)](../dotnet/list-stl-clr.md)|
|[map (STL/CLR)](../dotnet/map-stl-clr.md)|[multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)|
|[multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)|[numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)|
|[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)|[queue (STL/CLR)](../dotnet/queue-stl-clr.md)|
|[set (STL/CLR)](../dotnet/set-stl-clr.md)|[stack (STL/CLR)](../dotnet/stack-stl-clr.md)|
|[utility (STL/CLR)](../dotnet/utility-stl-clr.md)|[vector (STL/CLR)](../dotnet/vector-stl-clr.md)|

## <a name="see-also"></a>Viz také

[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)