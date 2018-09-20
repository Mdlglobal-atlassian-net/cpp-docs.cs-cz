---
title: Smíšená (nativní a spravovaná) sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/18/2018
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
ms.openlocfilehash: 4ee94905bc4c40f6d080e34098e24bd71d495141
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494488"
---
# <a name="mixed-native-and-managed-assemblies"></a>Smíšená (nativní a spravovaná) sestavení

Smíšená sestavení jsou schopné obsahující nespravované strojové instrukce a instrukce jazyka MSIL. Díky tomu je možné vyvolat v součásti .NET, při zachování kompatibility s nativních knihoven C++ a volání. Pomocí smíšená sestavení, mohou vývojáři vytvářet aplikace pomocí kombinaci .NET a nativního kódu C++.

Například již existující knihovny, které obsahuje jenom nativní kód C++, může být přenesena na platformě .NET opětovnou kompilací pouze jeden modul s **/CLR** přepínač kompilátoru. Tento modul je pak možné používat funkce rozhraní .NET, ale zůstane kompatibilní s zbytek aplikace. Dokonce můžete rozhodnout mezi spravovaný a nativní kompilace na základě funkce funkce ve stejném souboru (viz [spravované, nespravované](../preprocessor/managed-unmanaged.md)).

Generování smíšené spravované sestavení Visual C++ podporuje pouze s použitím **/CLR** – možnost kompilátoru. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017. Pokud budete potřebovat čisté a ověřitelné spravovaná sestavení, doporučujeme že vytvořit pomocí jazyka C#.

Starší verze sady nástrojů kompilátoru Visual C++ nepodporuje generování tří různých typů spravovaných sestavení: smíšené, čisté a ověřitelné. Poslední dva jsou popsány v [prázdná a ověřitelný kód (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>V tomto oddílu

[Postupy: přechod na/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
Popisuje doporučené kroky pro zavedení nebo upgradu funkce rozhraní .NET ve vaší aplikaci.

[Postupy: kompilace/CLR MFC a ATL kódu s použitím](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
Popisuje, jak kompilovat existující programy MFC a ATL cílit na modul Common Language Runtime.

[Inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md)<br/>
Popisuje "zámek zavaděče" problémy a řešení.

[Podpora knihovny pro smíšená sestavení](../dotnet/library-support-for-mixed-assemblies.md)<br/>
Tento článek popisuje způsob použití nativních knihoven v **/CLR** kompilace.

[Důležité informace o výkonu](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
Popisuje vliv na výkon smíšená sestavení a data zařazování.

[Domény aplikace a jazyk Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
Tento článek popisuje podporu Visual C++ pro aplikační domény.

[Dvojitému](../dotnet/double-thunking-cpp.md)<br/>
Tento článek popisuje vliv na výkon, nativní vstupního bodu pro spravované funkce.

[Obcházení výjimek na CLR vypnutí při spotřebě objektů COM sestavených s parametrem/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
Popisuje, jak k zajištění řádné vypnutí spravovanou aplikaci, která využívá objekt modelu COM zkompilovaná **/CLR**.

[Postupy: Vytvoření částečně důvěryhodné aplikace CRT odebráním závislosti na knihovně DLL](../dotnet/create-a-partially-trusted-application.md)<br/>
Tento článek popisuje postup vytvoření částečně důvěryhodné aplikace Common Language Runtime pomocí jazyka Visual C++ odebráním závislosti na msvcm90.dll.

Další informace o pokynech pro kódování pro smíšená sestavení, najdete v článku na webu MSDN [přehled ze spravovaného/nespravovaného kódu Interoperability](https://msdn.microsoft.com/library/ms973872.aspx).

## <a name="see-also"></a>Viz také:

- [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)
