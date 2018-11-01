---
title: ClickOnce – nasazení pro aplikace Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
ms.openlocfilehash: 29395e5d7e4ba9e2c582d9e5c081a4f667dcaafa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467806"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>ClickOnce – nasazení pro aplikace Visual C++

Visual Studio poskytuje dvě různé technologie pro nasazení aplikací pro Windows: nasazení ClickOnce nebo [Instalační služby systému Windows](/windows/desktop/Msi/windows-installer-portal) nasazení.

## <a name="clickonce-deployment-in-c"></a>ClickOnce – nasazení v jazyce C++

Vývojové prostředí Visual C++ přímo nepodporuje nasazení projekty Visual C++ pomocí ClickOnce, ale nástroje jsou k dispozici pro použití.

> [!NOTE]
>  Visual Studio podporuje ClickOnce v jazyce Visual C# a Visual Basic vývojových prostředích. Pokud váš projekt Visual C++, představuje závislost projektu jazyka Visual C#, můžete publikovat aplikaci (včetně jejích závislostí) použitím nasazení ClickOnce z vývojového prostředí jazyka Visual C#.

K nasazení aplikace Visual C++ pomocí technologie ClickOnce, je nejprve nutné sestavit [Manifest aplikace ClickOnce](/visualstudio/deployment/clickonce-application-manifest) a [Manifest nasazení ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) pomocí [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) nebo jeho verze s grafickým uživatelským rozhraním (informace najdete v tématu [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)).

Nejprve použijte Mage.exe k sestavení manifestu aplikace Výsledný soubor bude mít příponu .manifest. Poté použijte Mage.exe k sestavení manifestu nasazení; Výsledný soubor bude mít příponu .application. Následně podepište manifesty.

Manifest aplikace musí specifikovat cílový procesor (**x86**, **x64**, nebo **ARM**). Zobrazit [nasazení nezbytných součástí pro 64bitové aplikace](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications) informace o těchto možnostech.

Navíc název manifesty aplikace a nasazení musí být odlišný od názvu aplikace jazyka C++. Tím předejdete konfliktu mezi manifestem aplikace vytvořeným Mage.exe a externím manifestem, který je součástí aplikace jazyka C++.

K nasazení budete potřebovat k instalaci všech knihoven Visual C++, na kterých vaše aplikace závisí. K určení závislostí pro konkrétní aplikaci, můžete použít depends.exe nebo nástroj DUMPBIN s DEPENDENTS. Další informace o závislostech naleznete v tématu [Principy závislostí v aplikacích Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Možná budete muset spustit VCRedist.exe; Tento nástroj nainstaluje knihovny Visual C++ v cílovém počítači.

Také můžete potřebovat sestavit zaváděcí nástroj (Instalační program předpokladů) pro vaši aplikaci k nasazení požadovaných komponent; informace týkající se zaváděcího nástroje naleznete v tématu [vytváření balíčků Bootstrapperu](/visualstudio/deployment/creating-bootstrapper-packages).

Podrobnější popis technologie naleznete v tématu [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment). Podrobný příklad nasazení ClickOnce, naleznete v tématu [návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application).

## <a name="see-also"></a>Viz také

[Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)<br>
[MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)<br>
[MakeCert.exe (nástroj pro vytvoření certifikátu)](https://msdn.microsoft.com/library/windows/desktop/aa386968)<br>
[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)<br>
[Nasazení aplikací, služeb a komponent](/visualstudio/deployment/deploying-applications-services-and-components)<br>
[ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[Vytváření balíčků bootstrapperu](/visualstudio/deployment/creating-bootstrapper-packages)<br>
[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br>
[Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)