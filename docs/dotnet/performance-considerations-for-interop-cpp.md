---
title: Faktory ovlivňující výkon u zprostředkovatelů komunikace (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9223c52e4ef831a9a1ff657db1a0d7859dd6ce6c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="performance-considerations-for-interop-c"></a>Faktory ovlivňující výkon u zprostředkovatelů komunikace (C++)
Toto téma obsahuje pokyny pro snížení účinku spravované nebo nespravované spolupráce přechody na výkon.  
  
 Visual C++ podporuje stejné mechanismy spolupráce jako jinými jazyky rozhraní .NET, jako je například Visual Basic a C# (P/Invoke), ale také poskytuje spolupráce podpory, které jsou specifické pro aplikaci Visual C++ (C++ interop). Pro aplikace důležité pro výkon je důležité si uvědomit, vliv na výkon každé techniky vzájemné spolupráce.  
  
 Bez ohledu na použitou techniku speciální sekvence přechodu, nazvané převody, je potřeba pokaždé, když spravovaná funkce volá nespravované naopak funkce a naopak. Tyto převody budou automaticky vloženy ve Visual C++ compiler, ale je důležité mít na paměti, že kumulativně, mohou být tyto přechody nákladné z hlediska výkonu.  
  
## <a name="reducing-transitions"></a>Snížení přechodů  
 Jedním ze způsobů vyhnout nebo je snížit náklady na převodů vzájemné spolupráce je refaktorovat rozhraní podílet na minimalizovat přechody spravované nebo nespravované. Výraznému zlepšení výkonu můžete provést pomocí cílení chatty rozhraní, které jsou ty, které se podílejí častých volání přes hranice spravované nebo nespravované. Spravované funkci, která volá nespravované funkce ve smyčce úzkou, je třeba vhodným kandidátem pro refaktoring. Pokud smyčky samotné je přesunuta do nespravovaných straně, nebo pokud spravovaná alternativa k se vytvoří nespravovaného volání (možná fronta dat na spravované straně a pak zařazování na nespravovaného rozhraní API najednou po smyčky), může být počtu přechodů snížit přihlášení ificantly.  
  
## <a name="pinvoke-vs-c-interop"></a>P/Invoke vs. interoperabilita C++  
 Pro jazyky rozhraní .NET, jako je Visual Basic a C# je předepsané metodu pro spolupráce s nativním součásti P/Invoke. Protože P/Invoke je podporovaný rozhraním .NET Framework, také Visual C++ ji podporuje, ale Visual C++ také poskytuje podporu vlastní vzájemná funkční spolupráce, který se označuje jako zprostředkovatele komunikace C++. Interoperabilita C++ je přes P/Invoke preferovaná, protože P/Invoke není bezpečnost typů. V důsledku toho jsou primárně hlášeny chyby za běhu, ale zprostředkovatele komunikace C++ má také výhody výkonu přes P/Invoke.  
  
 Obě tyto metody vyžadují několik kroků k provedení spravované funkce volání nespravované funkce:  
  
-   Argumenty pro volání funkce přeuspořádány z modulu CLR na nativní typy.  
  
-   Je proveden převod se spravované na nespravované.  
  
-   Nespravované funkce je volána (pomocí nativní verze argumenty).  
  
-   Převodu z nespravovaného do spravovaného je spustit.  
  
-   Návratový typ a všechny "out" nebo "v, out" argumenty jsou zařazeny z nativní na typy CLR.  
  
 Převody spravované nebo nespravované jsou nezbytné pro práci na všech vzájemné funkční spolupráce, ale zařazování dat, která je požadována, závisí na souvisejících datových typech, podpis funkce a použití data.  
  
 Zařazování dat, které se provádí zprostředkovatele komunikace C++ je nejjednodušší forma možných: parametry jsou jednoduše zkopírovány přes spravované nebo nespravované hranice bitové způsobem; není provedena žádná transformace. Pro P/Invoke, toto je pouze hodnotu true, pokud jsou všechny parametry jednoduché, přenositelné typy. Jinak, provede P/Invoke nepříliš robustní kroky pro každý spravovaný parametr převést na odpovídající nativní typ, a naopak v případě, že argumenty, které jsou označeny jako "out" nebo "v, out".  
  
 Jinými slovy zprostředkovatele komunikace C++ používá metodu nejrychlejší možné zařazování dat, zatímco P/Invoke používá metodu nejvíce robustní. To znamená, že zprostředkovatele komunikace C++ (ve tvaru typickém pro jazyk C++) poskytuje optimální výkon ve výchozím nastavení a programátorů zodpovídá za adresách případech, kdy je toto chování není bezpečné nebo vhodné.  
  
 Interoperabilita C++ proto vyžaduje, aby zařazování dat je třeba zadat explicitně, ale výhoda spočívá v tom, že je programátorů mohou rozhodnout, co je vhodné pro danou povaha data a jak se má použít. Kromě toho Přestože chování zařazování dat P/Invoke můžete změnit na míru určitý stupeň, zprostředkovatele komunikace C++ umožňuje dat – zařazování k přizpůsobení pro volání volání. To není možné pomocí P/Invoke.  
  
 Další informace o zprostředkovatele komunikace C++ najdete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
## <a name="see-also"></a>Viz také  
 [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)