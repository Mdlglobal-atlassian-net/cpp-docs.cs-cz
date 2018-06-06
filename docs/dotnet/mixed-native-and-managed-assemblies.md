---
title: Smíšená (nativní a spravovaná) sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 469e0429408e1b8afed65889539202650cd28413
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704786"
---
# <a name="mixed-native-and-managed-assemblies"></a>Smíšená (nativní a spravovaná) sestavení

Smíšená sestavení jsou schopná využívat obsahující pokyny nespravovaném počítači a MSIL pokyny. To umožňuje, aby volání a volat součásti rozhraní .NET, při zachování kompatibility s součásti, které jsou zcela nespravované. Pomocí smíšená sestavení, vývojářům vytvářet aplikace, které používají směs spravovaných a nespravovaných funkcí. Smíšená sestavení díky ideální pro migraci stávajících aplikací Visual C++ pro platformu .NET.

Například existující aplikaci, která obsahuje jenom nespravované funkce, může být přenesena na platformě .NET opětovnou kompilací pouze jeden modul s **/CLR** přepínače kompilátoru. Tento modul je pak možné použít funkce rozhraní .NET, ale zůstává kompatibilní se zbývající částí aplikace. Tímto způsobem lze převést aplikaci na platformě .NET postupná, část jednotlivé způsobem. Je dokonce možné se rozhodnout mezi spravovanými a nespravovanými kompilace na základě pomocí funkcí v rámci stejného souboru (viz [spravované, nespravované](../preprocessor/managed-unmanaged.md)).

Visual C++ podporuje pouze generování smíšená sestavení spravované pomocí **/CLR** – možnost kompilátoru. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017. Pokud budete potřebovat čistý a ověřitelný spravovaná sestavení, doporučujeme že vytvořit pomocí jazyka C#.

Starší verze sady nástrojů kompilátoru Visual C++ podporované generování tři odlišné typy spravovaných sestavení: smíšené, čisté a ověřitelné. Poslední dva jsou popsány v [prázdná a ověřitelný kód (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: přechod na/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
Popisuje doporučené kroky pro zavedení nebo upgrade funkcí .NET ve vaší aplikaci.

[Postupy: kompilování MFC a knihovny ATL kódu s použitím přepínače/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
Popisuje způsob kompilace existující MFC a knihovna ATL programů, pro které modul Common Language Runtime.

[Inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md)<br/>
Popisuje problém "zámek zavaděče" a řešení.

[Podpora knihovny pro smíšená sestavení](../dotnet/library-support-for-mixed-assemblies.md)<br/>
Popisuje, jak používat nativní knihovny v **/CLR** kompilace.

[Důležité informace o výkonu](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
Popisuje vliv na výkon smíšená sestavení a zařazování data.

[Domény aplikace a jazyk Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
Popisuje podporu Visual C++ pro aplikační domény.

[Dvojitý převod adres](../dotnet/double-thunking-cpp.md)<br/>
Popisuje vliv na výkon nativní vstupní bod pro spravované funkce.

[Obcházení výjimek na CLR vypnutí při spotřebě objektů COM sestavených s volbou/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
Popisuje, jak zajistit řádné vypnutí spravované aplikace, která zpracovává objekt COM kompilovat s **/CLR**.

[Postupy: Vytvoření částečně důvěryhodné aplikace CRT odebráním závislosti na knihovně DLL](../dotnet/create-a-partially-trusted-application.md)<br/>
Popisuje postup vytvoření částečně důvěryhodné aplikace modul Common Language Runtime Visual C++ pomocí odebráním závislosti na msvcm90.dll.

Další informace o pokyny pro kódování pro smíšená sestavení, najdete v článku na webu MSDN [přehled o spravované nebo nespravované kód interoperabilita](https://msdn.microsoft.com/en-us/library/ms973872.aspx).

## <a name="see-also"></a>Viz také:

- [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)
