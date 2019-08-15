---
title: ClickOnce – nasazení pro aplikace Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
ms.openlocfilehash: 4408db9d129c03ee5df9b006b03c6586df02afb1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513763"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>ClickOnce – nasazení pro aplikace Visual C++

Visual Studio poskytuje dvě různé technologie pro nasazování aplikací pro Windows: Nasazení ClickOnce nebo nasazení [Instalační služba systému Windows](/windows/win32/Msi/windows-installer-portal) .

## <a name="clickonce-deployment-in-c"></a>Nasazení ClickOnce vC++

Vývojové prostředí C++ ve Visual Studiu přímo nepodporuje nasazení projektů sady Visual Studio C++ s ClickOnce, ale nástroje jsou k dispozici pro jeho použití.

> [!NOTE]
>  Visual Studio podporuje ClickOnce ve vývojových prostředích vizuálů C# a Visual Basic. Pokud je váš projekt C++ sady Visual Studio závislostí vizuálního C# projektu, můžete publikovat aplikaci (včetně jejích závislostí) pomocí nasazení ClickOnce z prostředí Visual C# Development.

Chcete-li nasadit C++ vizuální aplikaci pomocí ClickOnce, musíte nejprve sestavit [manifest aplikace ClickOnce](/visualstudio/deployment/clickonce-application-manifest) a [manifest nasazení ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) pomocí nástroje [Mage. exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) nebo jeho grafického uživatele. verze rozhraní (informace naleznete v tématu [MageUI. exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)).

Nejprve pomocí nástroje Mage. exe sestavíte manifest aplikace; Výsledný soubor bude mít příponu. manifest. Pak pomocí nástroje Mage. exe sestavíte manifest nasazení; Výsledný soubor bude mít příponu. Application. Pak podepisujete manifesty.

Manifest aplikace musí určovat cílový procesor (**x86**, **x64**nebo **ARM**). Informace o těchto možnostech najdete v tématu [nasazení požadavků pro 64 aplikací](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications) .

Také název aplikace a manifesty nasazení musí být odlišný od názvu C++ aplikace. Tím se vyhnete konfliktu mezi manifestem aplikace vytvořeným Mage. exe a externím manifestem, který je C++ součástí aplikace.

Vaše nasazení bude vyžadovat instalaci všech vizuálních C++ knihoven, na kterých vaše aplikace závisí. Chcete-li určit závislosti pro konkrétní aplikaci, můžete použít příkaz depends. exe nebo nástroj DUMPBIN s možností/DEPENDENTS. Další informace o závislostech naleznete v tématu [Principy závislostí vizuální C++ aplikace](understanding-the-dependencies-of-a-visual-cpp-application.md). Je možné, že budete muset spustit VCRedist. exe; Tento nástroj nainstaluje do C++ cílového počítače knihovny vizuálů.

Pro nasazení požadovaných součástí může být také potřeba vytvořit zaváděcí nástroj (instalační program požadavků) pro vaši aplikaci. informace o zaváděcím nástroji najdete v tématu [vytváření balíčků zaváděcího nástroje](/visualstudio/deployment/creating-bootstrapper-packages).

Podrobnější popis technologie najdete v tématu [zabezpečení a nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment). Podrobný příklad nasazení ClickOnce najdete v tématu [Názorný postup: Ruční nasazení aplikace](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)ClickOnce

## <a name="see-also"></a>Viz také:

[Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)<br>
[MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)<br>
[Makecert. exe (Nástroj pro vytvoření certifikátu)](/windows/win32/SecCrypto/makecert)<br>
[Nasazení desktopových aplikací](deploying-native-desktop-applications-visual-cpp.md)<br>
[Nasazení aplikací, služeb a komponent](/visualstudio/deployment/deploying-applications-services-and-components)<br>
[ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Vytváření balíčků bootstrapperu](/visualstudio/deployment/creating-bootstrapper-packages)<br>
[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br>
[Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)
