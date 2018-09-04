---
title: ClickOnce – nasazení pro aplikace Visual C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82a290eb7695bbcd7c03cda0351445519352e80a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677721"
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
 [Mage.exe (generování manifestu a nástroj pro úpravy)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [MakeCert.exe (nástroj pro vytvoření certifikátu)](https://msdn.microsoft.com/library/windows/desktop/aa386968)   
 [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Nasazení aplikací, služeb a komponent](/visualstudio/deployment/deploying-applications-services-and-components)   
 [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)   
 [Vytváření balíčků Bootstrapperu](/visualstudio/deployment/creating-bootstrapper-packages)   
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)