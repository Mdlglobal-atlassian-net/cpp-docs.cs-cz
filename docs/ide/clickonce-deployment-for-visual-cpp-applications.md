---
title: ClickOnce – nasazení pro aplikace Visual C++ | Microsoft Docs
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
ms.openlocfilehash: e85ec0dfc011aab4d2b3ac835bbe71782b055000
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33332322"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>ClickOnce – nasazení pro aplikace Visual C++
Visual Studio poskytuje dvě různé technologie pro nasazení aplikace systému Windows: ClickOnce – nasazení nebo [Instalační služby systému Windows](http://msdn.microsoft.com/library/cc185688) nasazení.  
  
## <a name="clickonce-deployment-in-c"></a>ClickOnce – nasazení v jazyce C++  
 Vývojové prostředí Visual C++ nepodporuje přímé nasazení projekty Visual C++ s ClickOnce, ale jsou k dispozici pro použití nástroje.  
  
> [!NOTE]
>  Visual Studio podporují ClickOnce ve vývojovém prostředí Visual C# a Visual Basic. Pokud je název projektu Visual C++ závislost projekt Visual C#, můžete publikovat aplikace (včetně jeho závislé součásti) pomocí nasazení ClickOnce z vývojového prostředí jazyka Visual C#.  
  
 K nasazení aplikace Visual C++ pomocí ClickOnce, je nejprve nutné sestavení [Manifest aplikace ClickOnce](/visualstudio/deployment/clickonce-application-manifest) a [Manifest aplikace ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest) pomocí [Mage.exe (manifestu Generování a nástroj pro úpravy)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) nebo jeho verze grafické uživatelské rozhraní (informace najdete v tématu [MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)).  

  
 Nejdřív použijte Mage.exe k sestavení manifest aplikace; Výsledný soubor bude mít manifest rozšíření. Pak použijte Mage.exe k sestavení manifestu nasazení; Výsledný soubor bude mít příponu .application. Pak se přihlaste manifesty.  
  
 Manifest aplikace musíte zadat cílový procesor (**x86**, **x64**, nebo **ARM**). V tématu [nasazení požadovaných součástí pro 64bitové aplikace](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications) informace o těchto možnostech.  
  
 Navíc musí být název manifestů aplikace a nasazení liší od názvu aplikace jazyka C++. Tím je zabráněno konfliktu mezi manifest aplikace vytvořeným Mage.exe a externí manifestu, který je součástí aplikace C++.  
  
 Vaše nasazení bude muset nainstalovat všechny knihovny jazyka Visual C++, na které závisí aplikace. K určení závislostí pro konkrétní aplikaci, můžete použít depends.exe nebo DUMPBIN – nástroj s DEPENDENTS. Další informace o závislostech najdete v tématu [Principy závislostí aplikace Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Možná budete muset spustit VCRedist.exe; Tento nástroj nainstaluje knihovny jazyka Visual C++ v cílovém počítači.  
  
 Také můžete potřebovat sestavit zaváděcí nástroj (požadavky instalační program) pro vaši aplikaci k nasazení požadovaných součástí; informace týkající se zaváděcího nástroje najdete v tématu [vytváření balíčků zaváděcího nástroje](/visualstudio/deployment/creating-bootstrapper-packages).  
  
 Podrobnější popis technologie najdete v tématu [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment). Podrobný příklad nasazení ClickOnce najdete v tématu [návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application).  
  
## <a name="see-also"></a>Viz také  
 [Mage.exe (generování manifestu a nástroj pro úpravy)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [MakeCert.exe (nástroj pro vytvoření certifikátu)](https://msdn.microsoft.com/library/windows/desktop/aa386968)   
 [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Nasazení aplikací, služeb a komponent](/visualstudio/deployment/deploying-applications-services-and-components)   
 [Instalační služba systému Windows](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)   
 [Vytváření balíčků zaváděcího nástroje](/visualstudio/deployment/creating-bootstrapper-packages)   
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)