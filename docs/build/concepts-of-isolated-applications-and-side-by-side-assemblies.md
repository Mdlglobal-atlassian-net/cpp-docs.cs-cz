---
title: Koncept izolovaných aplikací a souběžných sestavení
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
ms.openlocfilehash: 6453e68b07013bc5f5799b7252ad9a88e73250f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532935"
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>Koncept izolovaných aplikací a souběžných sestavení

Aplikace se považuje za [izolované aplikace](/windows/desktop/SbsCs/isolated-applications) Pokud jsou všechny její součásti [sestavení vedle sebe](/windows/desktop/SbsCs/about-side-by-side-assemblies-). Souběžné sestavení je kolekce prostředků – skupina knihoven DLL, tříd oken, serverů COM, knihoven typů nebo rozhraní – které se nasazují společně a které jsou dostupné spuštěné aplikaci. Souběžné sestavení je zpravidla jedna až několik knihoven DLL.

## <a name="shared-or-private"></a>Sdílené nebo soukromé

Souběžné sestavení může být buď sdílené, nebo soukromé. [Sdílená sestavení vedle sebe](https://msdn.microsoft.com/library/aa375996.aspx) může používat více aplikací, které určují ve svých manifestech závislost na sestavení. Několik verzí souběžného sestavení může být sdíleno různými aplikacemi, které běží současně. A [soukromé sestavení](/windows/desktop/SbsCs/about-private-assemblies-) je sestavení, který je nasazen spolu s aplikací pro výhradní použití této aplikace. Soukromá sestavení se instalují do složky, která obsahuje spustitelný soubor aplikace nebo některou z jejích podsložek.

## <a name="manifests-and-search-order"></a>Manifesty a pořadí hledání

Izolované aplikace a sestavení vedle sebe jsou popsány pomocí [manifesty](https://msdn.microsoft.com/library/aa375365). Manifest je dokument XML, který může mít formu externího souboru nebo může být vložen do aplikace nebo sestavení jako prostředek. Soubor manifestu izolované aplikace slouží ke správě názvů a verzí sdílených souběžných sestavení, na které by aplikace při běhu měla vytvořit vazbu. Manifest souběžného sestavení obsahuje názvy, verze, prostředky a závislá sestavení souběžných sestavení. Manifest sdílených souběžných sestavení se instaluje do složky %WINDIR%\WinSxS\Manifests\. V případě soukromého sestavení doporučujeme jeho manifest zahrnout do knihovny DLL jako prostředek, jehož ID je rovno 1. Soukromé sestavení může mít také stejný název jako knihovna DLL. Další informace najdete v tématu [soukromých sestavení](/windows/desktop/SbsCs/about-private-assemblies-).

Při běhu používá systém Windows informace o sestavení z manifestu aplikace k vyhledání a načtení odpovídajícího souběžného sestavení. Pokud je izolovaná aplikace závislá na nějakém sestavení, hledá operační systém toto sestavení nejprve mezi sdílenými sestaveními v mezipaměti nativních sestavení ve složce %WINDIR%\WinSxS\. Není-li požadované sestavení nalezeno, hledá pak operační systém soukromé sestavení ve složce adresářové struktury aplikace. Další informace najdete v tématu [pořadí hledání sestavení](/windows/desktop/SbsCs/assembly-searching-sequence).

## <a name="changing-dependencies"></a>Změna závislostí

Po nasazení aplikace úpravou můžete změnit závislosti sestavení vedle sebe [konfiguračních souborů vydavatele](/windows/desktop/SbsCs/publisher-configuration-files) a [konfiguračních souborů aplikace](/windows/desktop/SbsCs/application-configuration-files). Konfigurační soubor vydavatele, označovaný také jako soubor zásad vydavatele, je soubor XML, který globálně přesměrovává aplikace a sestavení od používání jedné verze souběžného sestavení k používání jiné verze téhož sestavení. Závislost můžete například změnit, pokud je pro souběžné sestavení nasazena oprava chyby nebo zabezpečení, a chcete všechny aplikace přesměrovat tak, aby používaly tuto opravenou verzi. Konfigurační soubor aplikace je soubor XML, který přesměrovává konkrétní aplikaci od používání jedné verze souběžného sestavení k používání jiné verze téhož sestavení. Pomocí konfiguračního souboru aplikace můžete přesměrovat konkrétní aplikaci tak, aby používala jinou verzi souběžného sestavení, než která je definovaná v konfiguračním souboru vydavatele. Další informace najdete v tématu [konfigurace](/windows/desktop/SbsCs/configuration).

## <a name="visual-c-libraries"></a>Knihovny jazyka Visual C++

V sadě Visual Studio 2005 a Visual Studio 2008 byly distribuovatelné knihovny (například ATL, MFC, CRT, Standard C++, OpenMP a MSDIA) nasazeny jako sdílená souběžná sestavení do mezipaměti nativních sestavení. V aktuální verzi používají distribuovatelné knihovny centrální nasazení. Všechny aplikace vytvořené pomocí jazyka Visual C++ jsou standardně sestaveny s manifestem vloženým do konečného binárního souboru, přičemž tento manifest popisuje závislosti binárního souboru na knihovnách jazyka Visual C++. Principy generování manifestu pro aplikace Visual C++, naleznete v tématu [Principy generování manifestu pro programy C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md). Manifest se nevyžaduje pro aplikace staticky propojené s knihovnami, které používají, nebo které používají místní nasazení. Další informace o nasazení naleznete v tématu [nasazení v jazyce Visual C++](../ide/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Viz také

[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)