---
title: "Koncepty izolovaných aplikací a souběžně sdílená sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9166f62c51344cc9c620da34d9c6fcee4665f400
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>Koncept izolovaných aplikací a souběžných sestavení
Aplikace se považuje za [izolované aplikace](http://msdn.microsoft.com/library/aa375190) Pokud jsou všechny jeho komponenty [souběžně sdílená sestavení](http://msdn.microsoft.com/library/ff951640). Souběžné sestavení je kolekce prostředků – skupina knihoven DLL, tříd oken, serverů COM, knihoven typů nebo rozhraní – které se nasazují společně a které jsou dostupné spuštěné aplikaci. Souběžné sestavení je zpravidla jedna až několik knihoven DLL.  
  
## <a name="shared-or-private"></a>Sdílené nebo soukromé  
 Souběžné sestavení může být buď sdílené, nebo soukromé. [Sdílená souběžně sdílená sestavení](https://msdn.microsoft.com/en-us/library/aa375996.aspx) může být používán více aplikací, která zadáte v jejich manifesty závislost na sestavení. Několik verzí souběžného sestavení může být sdíleno různými aplikacemi, které běží současně. A [privátní sestavení](http://msdn.microsoft.com/library/ff951638) je sestavení, které je nasazeno společně s aplikací pro výhradní použití této aplikace. Soukromá sestavení se instalují do složky, která obsahuje spustitelný soubor aplikace nebo některou z jejích podsložek.  
  
## <a name="manifests-and-search-order"></a>Manifesty a pořadí hledání  
 Izolované aplikace a souběžně sdílená sestavení jsou popsána v [manifesty](http://msdn.microsoft.com/library/aa375365). Manifest je dokument XML, který může mít formu externího souboru nebo může být vložen do aplikace nebo sestavení jako prostředek. Soubor manifestu izolované aplikace slouží ke správě názvů a verzí sdílených souběžných sestavení, na které by aplikace při běhu měla vytvořit vazbu. Manifest souběžného sestavení obsahuje názvy, verze, prostředky a závislá sestavení souběžných sestavení. Manifest sdílených souběžných sestavení se instaluje do složky %WINDIR%\WinSxS\Manifests\. V případě soukromého sestavení doporučujeme jeho manifest zahrnout do knihovny DLL jako prostředek, jehož ID je rovno 1. Soukromé sestavení může mít také stejný název jako knihovna DLL. Další informace najdete v tématu [soukromá sestavení](http://msdn.microsoft.com/library/ff951638).  
  
 Při běhu používá systém Windows informace o sestavení z manifestu aplikace k vyhledání a načtení odpovídajícího souběžného sestavení. Pokud je izolovaná aplikace závislá na nějakém sestavení, hledá operační systém toto sestavení nejprve mezi sdílenými sestaveními v mezipaměti nativních sestavení ve složce %WINDIR%\WinSxS\. Není-li požadované sestavení nalezeno, hledá pak operační systém soukromé sestavení ve složce adresářové struktury aplikace. Další informace najdete v tématu [pořadí hledání sestavení](http://msdn.microsoft.com/library/aa374224).  
  
## <a name="changing-dependencies"></a>Změna závislostí  
 Souběžně sdílená sestavení závislosti můžete změnit po nasazení aplikace změnou [vydavatele konfigurační soubory](http://msdn.microsoft.com/library/aa375682) a [konfigurační soubory aplikace](http://msdn.microsoft.com/library/aa374182). Konfigurační soubor vydavatele, označovaný také jako soubor zásad vydavatele, je soubor XML, který globálně přesměrovává aplikace a sestavení od používání jedné verze souběžného sestavení k používání jiné verze téhož sestavení. Závislost můžete například změnit, pokud je pro souběžné sestavení nasazena oprava chyby nebo zabezpečení, a chcete všechny aplikace přesměrovat tak, aby používaly tuto opravenou verzi. Konfigurační soubor aplikace je soubor XML, který přesměrovává konkrétní aplikaci od používání jedné verze souběžného sestavení k používání jiné verze téhož sestavení. Pomocí konfiguračního souboru aplikace můžete přesměrovat konkrétní aplikaci tak, aby používala jinou verzi souběžného sestavení, než která je definovaná v konfiguračním souboru vydavatele. Další informace najdete v tématu [konfigurace](http://msdn.microsoft.com/library/aa375123).  
  
## <a name="visual-c-libraries"></a>Knihovny jazyka Visual C++  
 V sadě Visual Studio 2005 a Visual Studio 2008 byly distribuovatelné knihovny (například ATL, MFC, CRT, Standard C++, OpenMP a MSDIA) nasazeny jako sdílená souběžná sestavení do mezipaměti nativních sestavení. V aktuální verzi používají distribuovatelné knihovny centrální nasazení. Všechny aplikace vytvořené pomocí jazyka Visual C++ jsou standardně sestaveny s manifestem vloženým do konečného binárního souboru, přičemž tento manifest popisuje závislosti binárního souboru na knihovnách jazyka Visual C++. Pochopit generování manifestu pro aplikace Visual C++, najdete v části [Principy generování manifestu pro programy C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md). Manifest se nevyžaduje pro aplikace staticky propojené s knihovnami, které používají, nebo které používají místní nasazení. Další informace o nasazení najdete v tématu [nasazení v jazyce Visual C++](../ide/deployment-in-visual-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)