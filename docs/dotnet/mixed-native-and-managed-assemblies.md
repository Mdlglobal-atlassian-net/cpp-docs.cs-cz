---
title: Smíšená (nativní a spravovaná) sestavení
ms.date: 09/18/2018
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
ms.openlocfilehash: 11bdfc98c64b2612129e10c002c68ee243bec7da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501140"
---
# <a name="mixed-native-and-managed-assemblies"></a>Smíšená (nativní a spravovaná) sestavení

Smíšená sestavení mohou obsahovat i nespravované instrukce pro počítače a instrukce jazyka MSIL. To jim umožňuje volat a volat komponenty .NET a přitom zachovat kompatibilitu s nativními C++ knihovnami. Pomocí smíšených sestavení mohou vývojáři vytvářet aplikace pomocí kombinace .NET a nativního C++ kódu.

Například existující knihovna skládající se výhradně z nativního C++ kódu může být přenesena na platformu .NET tím, že znovu zkompiluje pouze jeden modul s přepínačem **/CLR** . Tento modul pak může používat funkce .NET, ale zůstává kompatibilní se zbytkem aplikace. Je dokonce možné se rozhodnout mezi spravovanou a nativní kompilací na základě funkcí v rámci stejného souboru (viz [spravovaný, nespravovaný](../preprocessor/managed-unmanaged.md)).

Vizuál C++ podporuje pouze generování smíšených spravovaných sestavení pomocí možnosti kompilátoru **/CLR** . Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017. Pokud potřebujete čistá nebo ověřitelná spravovaná sestavení, doporučujeme je vytvořit pomocí C#.

Starší verze sady nástrojů Microsoft C++ Compiler podporovaly generování tří různých typů spravovaných sestavení: smíšené, čisté a ověřitelné. Druhá druhá je popsaná v části [čistý a ověřitelný kód (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: Migrovat na/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
Popisuje doporučený postup pro zavedení nebo upgrade funkcí .NET ve vaší aplikaci.

[Postupy: Kompilování kódu MFC a ATL pomocí/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
Popisuje, jak zkompilovat existující programy MFC a ATL pro cílení na modul CLR (Common Language Runtime).

[Inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md)<br/>
Popisuje problém a řešení "zámek zavaděče".

[Podpora knihovny pro smíšená sestavení](../dotnet/library-support-for-mixed-assemblies.md)<br/>
Popisuje, jak používat nativní knihovny v kompilacích **/CLR** .

[Důležité informace o výkonu](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
Popisuje dopad na výkon smíšených sestavení a zařazování dat.

[Domény aplikace a jazyk Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
Popisuje podporu C++ vizuálů pro domény aplikací.

[Dvojitá dvojitý](../dotnet/double-thunking-cpp.md)<br/>
Popisuje dopad na výkon nativního vstupního bodu pro spravovanou funkci.

[Předcházení výjimkám při vypínání modulu CLR při zpracování objektů COM sestavených s možností/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
Tento článek popisuje, jak zajistit správné vypnutí spravované aplikace, která využívá objekt modelu COM kompilovaný s možností **/CLR**.

[Postupy: Vytvoření částečně důvěryhodné aplikace CRT odebráním závislosti na knihovně DLL](../dotnet/create-a-partially-trusted-application.md)<br/>
Popisuje, jak vytvořit částečně důvěryhodný modul CLR (Common Language Runtime) C++ pomocí vizuálu odebráním závislosti na msvcm90. dll.

Další informace o pokynech pro kódování pro smíšená sestavení naleznete v článku na webu MSDN [Přehled interoperability spravovaného a nespravovaného kódu](/previous-versions/dotnet/articles/ms973872(v=msdn.10)).

## <a name="see-also"></a>Viz také:

- [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)
