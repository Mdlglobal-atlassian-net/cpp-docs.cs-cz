---
title: "Smíšená (nativní a spravovaná) sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c58f69057a7da709ec79c614fe60beef5a203f0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mixed-native-and-managed-assemblies"></a>Smíšená (nativní a spravovaná) sestavení
Smíšená sestavení jsou schopná využívat obsahující pokyny nespravovaném počítači a MSIL pokyny. To umožňuje, aby volání a volat součásti rozhraní .NET, při zachování kompatibility s součásti, které jsou zcela nespravované. Pomocí smíšená sestavení, vývojářům vytvářet aplikace, které používají směs spravovaných a nespravovaných funkcí. Smíšená sestavení díky ideální pro migraci stávajících aplikací Visual C++ pro platformu .NET.  
  
 Například existující aplikaci, která obsahuje jenom nespravované funkce, může být přenesena na platformě .NET opětovnou kompilací pouze jeden modul s **/CLR** přepínače kompilátoru. Tento modul je pak možné použít funkce rozhraní .NET, ale zůstává kompatibilní se zbývající částí aplikace. Tímto způsobem lze převést aplikaci na platformě .NET postupná, část jednotlivé způsobem. Je dokonce možné se rozhodnout mezi spravovanými a nespravovanými kompilace na základě pomocí funkcí v rámci stejného souboru (viz [spravované, nespravované](../preprocessor/managed-unmanaged.md)).  
  
 Jazyk Visual C++ podporuje tři odlišné generace typů spravovaných sestavení: smíšené, čisté a ověřitelné. Poslední dva jsou popsány v [prázdná a ověřitelný kód (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: přechod na/CLR](../dotnet/how-to-migrate-to-clr.md)  
 Popisuje doporučené kroky pro zavedení nebo upgrade funkcí .NET ve vaší aplikaci.  
  
 [Postupy: kompilování MFC a knihovny ATL kódu s použitím přepínače/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)  
 Popisuje způsob kompilace existující MFC a knihovna ATL programů, pro které modul Common Language Runtime.  
  
 [Inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md)  
 Popisuje problém "zámek zavaděče" a řešení.  
  
 [Podpora knihovny pro smíšená sestavení](../dotnet/library-support-for-mixed-assemblies.md)  
 Popisuje, jak používat nativní knihovny v **/CLR** kompilace.  
  
 [Faktory ovlivňující výkon](../dotnet/performance-considerations-for-interop-cpp.md)  
 Popisuje vliv na výkon smíšená sestavení a zařazování data.  
  
 [Aplikační domény a Visual C++](../dotnet/application-domains-and-visual-cpp.md)  
 Popisuje podporu Visual C++ pro aplikační domény.  
  
 [Dvojitý převod adres](../dotnet/double-thunking-cpp.md)  
 Popisuje vliv na výkon nativní vstupní bod pro spravované funkce.  
  
 [Obcházení výjimek na CLR vypnutí při spotřebě objektů COM sestavených s volbou/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)  
 Popisuje, jak zajistit řádné vypnutí spravované aplikace, která zpracovává objekt COM kompilovat s **/CLR**.  
  
 [Postupy: Vytvoření částečně důvěryhodné aplikace odebráním závislosti na modulu DLL knihovny CRT](../dotnet/create-a-partially-trusted-application.md)  
 Popisuje postup vytvoření částečně důvěryhodné aplikace modul Common Language Runtime Visual C++ pomocí odebráním závislosti na msvcm90.dll.  
  
 Další informace o pokyny pro kódování pro smíšená sestavení, najdete v článku webu MSDN článku "přehled o spravované nebo nespravované kód" v [http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp](http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp).  
  
## <a name="see-also"></a>Viz také  
 [Nativní a interoperabilitě .NET](../dotnet/native-and-dotnet-interoperability.md)