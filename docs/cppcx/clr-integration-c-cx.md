---
title: Integrace modulu CLR (C + +/ CX) | Microsoft Docs
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f9851a7aa0d1dad84a37504b479c551ffa63bcf9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="clr-integration-ccx"></a>Integrace modulu CLR (C + +/ CX)
Některé typy prostředí Windows Runtime přijímat zvláštní zpracování v jazyce C + +/ CX a jazyky, které jsou založeny na modul CLR (CLR). Tento článek popisuje, jak několik typů v jednom jazyce mapování na jiném jazyce. Například modulu CLR mapuje Windows.Foundation.IVector System.Collections.IList, Windows.Foundation.IMap System.Collections.IDictionary a tak dále. Podobně platí, jazyka C + +/ CX speciálně mapuje typy například Platform::Delegate a Platform::String.  
  
## <a name="mapping-the-windows-runtime-to-ccx"></a>Mapování prostředí Windows Runtime pro C + +/ CX  
 Když C + +/ CX čtení souboru metadat (.winmd) systému Windows, kompilátor automaticky mapuje běžné prostředí Windows Runtime obory názvů a typy pro C + +/ CX obory názvů a typy. Například číselného typu prostředí Windows Runtime `UInt32` se automaticky mapují na `default::uint32`.  
  
 C + +/ CX mapuje několik dalších typů prostředí Windows Runtime k **platformy** oboru názvů. Například **Windows::Foundation –** HSTRING popisovač, který představuje jen pro čtení textového řetězce Unicode, je namapovaný na C + +/ CX `Platform::String` třídy. Při operaci prostředí Windows Runtime vrátí chybu HRESULT, je mapován na C + +/ CX `Platform::Exception`. Další informace najdete v tématu [vestavěné typy](http://msdn.microsoft.com/en-us/acc196fd-09da-4882-b554-6c94685ec75f).  
  
 C + +/ CX také mapuje určité typy v oborech názvů prostředí Windows Runtime k rozšíření funkcí typu. U těchto typů, C + +/ CX poskytuje pomocníka konstruktorů a metod, které jsou specifické pro C++ a nejsou k dispozici v souboru standardní .winmd tohoto typu.  
  
 Následující seznamy shrnují struktury hodnotu, která podporuje nové konstruktory a pomocné metody. Pokud jste napsali dříve kód, který používá struktura inicializace seznamy, změňte ho na použití nově přidané konstruktory.  
  
 **Windows::Foundation –**  
  
-   bod  
  
-   Rect –  
  
-   Velikost  
  
 **Windows::UI**  
  
-   Barva  
  
 **Windows::UI::XAML**  
  
-   CornerRadius  
  
-   Doba trvání  
  
-   GridLength  
  
-   Tloušťka  
  
 **Windows::UI::XAML::Interop**  
  
1.  TypeName  
  
 **Windows::UI::XAML::Media**  
  
-   Matice  
  
 **Windows::UI::XAML::Media::Animation**  
  
-   KeyTime  
  
-   RepeatBehavior  
  
 **Windows::UI::XAML::Media::Media3D**  
  
-   Matrix3D  
  
## <a name="mapping-the-clr-to-ccx"></a>Mapování modulu CLR pro C + +/ CX  
 Soubor .winmd přečtení kompilátory jazyka Visual C++ nebo C# mapují automaticky určitých typů v souboru metadat pro příslušné C + +/ CX nebo CLR typů. Například v modulu CLR, IVector\<T > rozhraní je namapována na IList\<T >. Ale v jazyce C + +/ CX, IVector\<T > rozhraní není namapován na jiný typ.  
  
 IReference\<T > v prostředí Windows Runtime mapuje Nullable\<T > v rozhraní .NET.  
  
## <a name="see-also"></a>Viz také  
 [Spolupráce s jinými jazyky](../cppcx/interoperating-with-other-languages-c-cx.md)