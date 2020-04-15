---
title: ClickOnce – nasazení pro aplikace Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
ms.openlocfilehash: 4726fda8c5eca70ce7acde19f141a7c096395e95
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316613"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>ClickOnce – nasazení pro aplikace Visual C++

Visual Studio poskytuje dvě různé technologie pro nasazení aplikací systému Windows: Nasazení ClickOnce nebo Nasazení [Instalační služby systému Windows.](/windows/win32/Msi/windows-installer-portal)

## <a name="clickonce-deployment-in-c"></a>ClickOnce Nasazení v jazyce C++

Vývojové prostředí Visual C++ nepodporuje přímo nasazení projektů Visual Studio C++ s ClickOnce, ale nástroje jsou k dispozici pro jeho použití.

> [!NOTE]
> Visual Studio podporuje ClickOnce ve vývojovém prostředí Visual C# a Visual Basic. Pokud váš projekt Visual Studio C++ je závislost projektu Visual C#, můžete publikovat aplikace (včetně jeho závislostí) pomocí ClickOnce nasazení z vývojového prostředí Visual C#.

Chcete-li nasadit aplikaci Visual C++ pomocí ClickOnce, musíte nejprve vytvořit [manifest aplikace ClickOnce](/visualstudio/deployment/clickonce-application-manifest) a [manifest nasazení ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) pomocí [nástroje Mage.exe (Nástroj pro generování a úpravy manifestu)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) nebo jeho verze grafického uživatelského rozhraní (pro informace naleznete [v tématu MageUI.exe (Nástroj pro generování a úpravy manifestu, grafický klient).](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)

Nejprve použijte Mage.exe k vytvoření manifestu aplikace; výsledný soubor bude mít příponu .manifest. Potom použijte Mage.exe k vytvoření manifestu nasazení; výsledný soubor bude mít příponu .application. Pak podepíšete manifesty.

Manifest aplikace musí určit cílový procesor (**x86**, **x64**nebo **ARM**). Informace o těchto možnostech naleznete [v tématu Nasazení požadavků pro 64bitové aplikace.](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications)

Název manifestů aplikace a nasazení se také musí lišit od názvu aplikace jazyka C++. Tím se zabrání konfliktu mezi manifestaplikace vytvořené Mage.exe a externí manifest, který je součástí aplikace C++.

Vaše nasazení bude muset nainstalovat všechny knihovny Visual C++, na kterých závisí vaše aplikace. Chcete-li zjistit závislosti pro konkrétní aplikaci, můžete použít depends.exe nebo nástroj DUMPBIN s parametrem /DEPENDENTS. Další informace o závislostech naleznete [v tématu Principy závislostí aplikace Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md). Možná budete muset spustit Soubor VCRedist.exe. Tento nástroj nainstaluje knihovny Visual C++ do cílového počítače.

Může být také nutné vytvořit zaváděcí nástroj (instalační program požadavků) pro vaši aplikaci k nasazení nezbytných součástí; Informace o zaváděcím nástroji naleznete v [tématu Vytváření balíčků zaváděcího nástroje](/visualstudio/deployment/creating-bootstrapper-packages).

Podrobnější popis této technologie naleznete v [tématu ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment). Podrobný příklad nasazení ClickOnce naleznete [v tématu Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application).

## <a name="see-also"></a>Viz také

[Mage.exe (Nástroj pro generování a úpravy manifestu)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)<br>
[MageUI.exe (Nástroj pro generování a úpravy manifestu, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)<br>
[Makecert.exe (Nástroj pro vytváření certifikátů)](/windows/win32/SecCrypto/makecert)<br>
[Nasazení desktopových aplikací](deploying-native-desktop-applications-visual-cpp.md)<br>
[Nasazení aplikací, služeb a komponent](/visualstudio/deployment/deploying-applications-services-and-components)<br>
[ClickOnce Zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Vytváření balíčků zaváděcího nástroje](/visualstudio/deployment/creating-bootstrapper-packages)<br>
[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br>
[Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)
