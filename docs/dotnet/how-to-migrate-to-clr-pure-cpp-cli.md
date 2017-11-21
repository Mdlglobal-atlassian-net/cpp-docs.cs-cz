---
title: "Postupy: migrace na - clr: pure (C + +/ rozhraní příkazového řádku) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /clr compiler option [C++], migrating to /clr:pure
- migration [C++], pure MSIL
- pure MSIL [C++], porting to
ms.assetid: 5ffb1184-2095-4ade-84aa-4fa6324bc764
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ebff4ae1ac304ee0af073de49f4ee988922247d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-migrate-to-clrpure-ccli"></a>Postupy: Přechod na /clr:pure (C++/CLI)
Toto téma popisuje problémy, které mohou nastat při migraci do čistého pomocí MSIL **/CLR: pure** (najdete v části [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) Další informace). Toto téma předpokládá, že přenášený kód aktuálně vyhovuje podmínkám smíšeného sestavení pomocí **/CLR** možnost, protože cesty migrace z nespravovaného kódu na čistá MSIL není přímá. Nespravovaný kód, najdete v části [postupy: přechod na/CLR](../dotnet/how-to-migrate-to-clr.md) před pokusem o migraci na čistá MSIL.  
  
## <a name="basic-changes"></a>Základní změny  
 Čistá MSIL se skládá z MSIL pokyny, takže kód, který obsahuje funkce, které nelze vyjádřit v MSIL zabrání kompilaci. To zahrnuje funkcí definovaných jako jiné než pomocí konvencí volání [__clrcall](../cpp/clrcall.md). (Funkce bez __clrcall může být volána v čistá MSIL součást, ale není definována.)  
  
 Aby se zajistilo žádné chyby za běhu, měli byste povolit C4412 upozornění. Povolte C4412 přidáním `#pragma warning (default : 4412)` pro každý kompilace, který kompilujete s **/CLR: pure** a který předává typy C++ do a z IJW (**/CLR)** nebo nativního kódu. V tématu [upozornění kompilátoru (úroveň 2) C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) Další informace.  
  
## <a name="architectural-considerations"></a>Aspekty architektury  
 Některá omezení sestavení MSIL uvedené v [prázdná a ověřitelný kód (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) mít velký vliv na strategie návrhu a migrace aplikací. Na rozdíl od smíšená sestavení, zejména, není čistá sestavení MSIL Získejte úplnou kompatibilitu s nespravovanými moduly.  
  
 Čistá MSIL sestavení může volání nespravovaných funkcí, ale nelze volat z nespravovaných funkcí. Čistá MSIL v důsledku toho je lepší kandidátem na klientský kód, který používá nespravovaných funkcí, než je pro server kód, který je používán nespravovaných funkcí. Pokud funkce obsažené v čistá sestavení MSIL má být používána nespravovaných funkcí, třeba zadat jako vrstva rozhraní smíšená sestavení.  
  
 Aplikace, které používají ATL nebo MFC nejsou vhodné pro migraci čistá MSIL jako tyto knihovny nejsou v této verzi podporovány. Podobně [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] obsahuje soubory hlaviček, které nejde kompilovat v části **/CLR: pure**.  
  
 Při sestavení MSIL můžete volání nespravovaných funkcí, tato možnost je omezena na jednoduchý funkce jazyka C. Použití nespravovaného rozhraní API složitější bude pravděpodobně vyžadovat nespravované funkce, které mají být exponovány ve formě rozhraní modelu COM nebo smíšená sestavení, které může fungovat jako rozhraní mezi čistá MSIL a nespravované součásti. Použití vrstvy smíšeného sestavení je jediným způsobem, jak používat nespravovaných funkcí, které přebírají funkce zpětného volání, například jako čistá sestavení není schopen poskytnout nativní možné volat funkci pro použití jako zpětné volání.  
  
## <a name="application-domains-and-calling-conventions"></a>Aplikační domény a konvence volání  
 Přestože je možné pro čistá MSIL sestavení využívat nespravované funkce, funkce a statických dat jsou zpracovány jinak. V čistá sestavení jsou funkce implementovány s [__clrcall](../cpp/clrcall.md) volání konvence a statických dat je uložené pro aplikační doménu. Tím se liší od výchozí nastavení pro nespravovaná a smíšená sestavení, které používají [__cdecl](../cpp/cdecl.md) konvence volání funkcí a ukládání statických dat na základě procesů.  
  
 V kontextu čistá MSIL (a ověřitelný kód kompilovat s/clr: safe) jsou tyto výchozí hodnoty transparentní, jako [__clrcall](../cpp/clrcall.md) je výchozí konvenci volání modulu CLR a aplikační domény jsou nativním rozsahem pro statické a globální data v aplikacích .NET. Ale při propojování s nespravované nebo smíšeném součástí, odlišné zacházení s funkcemi a globální data může způsobit problémy.  
  
 Například pokud čistá MSIL součást je volání funkce v nespravované knihovně DLL, soubor hlavičky pro knihovnu DLL se použije ke kompilaci čistá sestavení. Ale pokud konvence volání pro každou funkci v hlavičce je explicitně uvedena, budou všechny pokládány být [__clrcall](../cpp/clrcall.md). To později způsobí selhání modulu runtime, jak tyto funkce jsou pravděpodobně implementuje pomocí [__cdecl](../cpp/cdecl.md) konvence. Funkce v nespravovaném souboru hlavičky mohou být explicitně označeny jako [__cdecl](../cpp/cdecl.md), nebo celý zdrojový kód knihovny DLL musí zopakovat pod **/CLR: pure**.  
  
 Podobně, jsou ukazatele na funkce předpokládá tak, aby odkazoval na [__clrcall](../cpp/clrcall.md) funkcí v části **/CLR: pure** kompilace. Tyto příliš musí být explicitně opatřena poznámkou správnou konvenci volání.  
  
 Další informace najdete v tématu [domény aplikace a jazyk Visual C++](../dotnet/application-domains-and-visual-cpp.md).  
  
## <a name="linking-limitations"></a>Omezení propojení  
 Linkeru jazyka Visual C++ se nebude pokoušet propojit smíšené a čisté soubory OBJ jako úložiště oboru a volání konvence se liší.  
  
## <a name="see-also"></a>Viz také  
 [Čistý a ověřitelný kód (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)