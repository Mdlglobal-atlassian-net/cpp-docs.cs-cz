---
title: Koncept izolovaných aplikací a souběžných sestavení
ms.date: 05/06/2019
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
ms.openlocfilehash: f75a95ccca214f437152d13e099fbd9d03eaaee2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493299"
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>Koncept izolovaných aplikací a souběžných sestavení

Aplikace se považuje za [izolovanou aplikaci](/windows/win32/SbsCs/isolated-applications) , pokud jsou všechny její komponenty [souběžným sestavením](/windows/win32/SbsCs/about-side-by-side-assemblies-). Souběžné sestavení je kolekce prostředků – skupina knihoven DLL, tříd oken, serverů COM, knihoven typů nebo rozhraní – které se nasazují společně a které jsou dostupné spuštěné aplikaci. Souběžné sestavení je zpravidla jedna až několik knihoven DLL.

## <a name="shared-or-private"></a>Sdílené nebo soukromé

Souběžné sestavení může být buď sdílené, nebo soukromé. [Sdílená souběžná sestavení](/windows/win32/sbscs/about-shared-assemblies-) mohou být používána více aplikacemi, které v jejich manifestech určují závislost na sestavení. Několik verzí souběžného sestavení může být sdíleno různými aplikacemi, které běží současně. [Soukromé sestavení](/windows/win32/SbsCs/about-private-assemblies-) je sestavení, které je nasazeno společně s aplikací pro výhradní použití této aplikace. Soukromá sestavení se instalují do složky, která obsahuje spustitelný soubor aplikace nebo některou z jejích podsložek.

## <a name="manifests-and-search-order"></a>Manifesty a pořadí hledání

Izolované aplikace i souběžná sestavení jsou popsány v [manifestech](/windows/win32/sbscs/manifests). Manifest je dokument XML, který může mít formu externího souboru nebo může být vložen do aplikace nebo sestavení jako prostředek. Soubor manifestu izolované aplikace slouží ke správě názvů a verzí sdílených souběžných sestavení, na které by aplikace při běhu měla vytvořit vazbu. Manifest souběžného sestavení obsahuje názvy, verze, prostředky a závislá sestavení souběžných sestavení. Manifest sdílených souběžných sestavení se instaluje do složky %WINDIR%\WinSxS\Manifests\. V případě soukromého sestavení doporučujeme jeho manifest zahrnout do knihovny DLL jako prostředek, jehož ID je rovno 1. Soukromé sestavení může mít také stejný název jako knihovna DLL. Další informace naleznete v tématu [o soukromých sestaveních](/windows/win32/SbsCs/about-private-assemblies-).

Při běhu používá systém Windows informace o sestavení z manifestu aplikace k vyhledání a načtení odpovídajícího souběžného sestavení. Pokud je izolovaná aplikace závislá na nějakém sestavení, hledá operační systém toto sestavení nejprve mezi sdílenými sestaveními v mezipaměti nativních sestavení ve složce %WINDIR%\WinSxS\. Není-li požadované sestavení nalezeno, hledá pak operační systém soukromé sestavení ve složce adresářové struktury aplikace. Další informace naleznete v tématu [pořadí vyhledávání sestavení](/windows/win32/SbsCs/assembly-searching-sequence).

## <a name="changing-dependencies"></a>Změna závislostí

Po nasazení aplikace úpravou [konfiguračních souborů vydavatele](/windows/win32/SbsCs/publisher-configuration-files) a [konfiguračních souborů aplikace](/windows/win32/SbsCs/application-configuration-files)můžete změnit závislosti souběžného sestavení. Konfigurační soubor vydavatele, označovaný také jako soubor zásad vydavatele, je soubor XML, který globálně přesměrovává aplikace a sestavení od používání jedné verze souběžného sestavení k používání jiné verze téhož sestavení. Závislost můžete například změnit, pokud je pro souběžné sestavení nasazena oprava chyby nebo zabezpečení, a chcete všechny aplikace přesměrovat tak, aby používaly tuto opravenou verzi. Konfigurační soubor aplikace je soubor XML, který přesměrovává konkrétní aplikaci od používání jedné verze souběžného sestavení k používání jiné verze téhož sestavení. Pomocí konfiguračního souboru aplikace můžete přesměrovat konkrétní aplikaci tak, aby používala jinou verzi souběžného sestavení, než která je definovaná v konfiguračním souboru vydavatele. Další informace najdete v tématu [Konfigurace](/windows/win32/SbsCs/configuration).

## <a name="visual-c-libraries"></a>Knihovny jazyka Visual C++

V sadě Visual Studio 2005 a Visual Studio 2008 byly distribuovatelné knihovny (například ATL, MFC, CRT, Standard C++, OpenMP a MSDIA) nasazeny jako sdílená souběžná sestavení do mezipaměti nativních sestavení. V aktuální verzi používají distribuovatelné knihovny centrální nasazení. Ve výchozím nastavení jsou všechny aplikace sestavené pomocí sady Visual Studio sestaveny s manifestem vloženým v konečném binárním souboru a manifest popisuje závislosti binárního souboru v knihovně Visual C++. Chcete-li pochopit generování manifestu pro aplikace jazyka C++, přečtěte si téma [Princip generování manifestu pro programy C/C++](understanding-manifest-generation-for-c-cpp-programs.md). Manifest se nevyžaduje pro aplikace staticky propojené s knihovnami, které používají, nebo které používají místní nasazení. Další informace o nasazení najdete v tématu [nasazení v Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Viz také

[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
