---
title: "Nasazení nativních aplikací klasické pracovní plochy (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
caps.latest.revision: "28"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7a8dcf4a49813ae108edb23b50676e751db5e2f1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="deploying-native-desktop-applications-visual-c"></a>Nasazení nativních aplikací klasické pracovní plochy (Visual C++)
Nasazení je proces, pomocí kterého distribuujete dokončenou aplikaci nebo součásti k instalaci na jiných počítačích. Plánování nasazení spustí, když aplikace je vytvořena na počítači pro vývojáře. Nasazení končí, když je aplikace nainstalované a připravené ke spuštění v počítači uživatele.  
  
 Visual Studio poskytuje různé technologie pro nasazení aplikace systému Windows. Ty zahrnují nasazení ClickOnce a instalační služba systému Windows.  
  
-   ClickOnce lze použít k nasazení aplikací C++, které cílí common language runtime (CLR) – smíšené, čisté a ověřitelné sestavení. I když instalační služba systému Windows můžete nasadit spravované aplikace, doporučujeme použít ClickOnce, protože ho využívá funkce zabezpečení rozhraní .NET Framework například podepsání manifestu. ClickOnce nepodporuje nasazení nativních aplikací C++. Další informace najdete v tématu [ClickOnce – nasazení pro aplikace Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md).  
  
-   Technologie Instalační služby systému Windows můžete použít k nasazení nativních aplikací C++ nebo aplikací C++ cílených modulu CLR.  
  
 Články v této části dokumentace popisuje zajistit, že na libovolném počítači, který poskytuje podporované cílovou platformu, soubory, které je nutné zahrnout instalační balíček a doporučené způsoby, jak funguje nativní aplikace Visual C++ znovu distribuovat součásti, které vaše aplikace závisí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Nasazení v jazyce Visual C++](../ide/deployment-in-visual-cpp.md)  
  
 [Koncepty nasazení](../ide/deployment-concepts.md)  
  
 [Principy závislostí v aplikaci Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)  
  
 [Určení, které knihovny DLL je třeba redistribuovat](../ide/determining-which-dlls-to-redistribute.md)  
  
 [Volba metody nasazení](../ide/choosing-a-deployment-method.md)  
  
 [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md)  
  
 [Příklady nasazení](../ide/deployment-examples.md)  
  
 [Redistribuce klientských webových aplikací](../ide/redistributing-web-client-applications.md)  
  
 [ClickOnce – nasazení pro aplikace Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md)  
  
 [C++/CLR aplikace spuštěné v předchozí verzi modulu Runtime](../ide/running-a-cpp-clr-application-on-a-previous-runtime-version.md)  
  
## <a name="related-sections"></a>Související oddíly  
 [Sestavení C/C++ izolovaných aplikací a souběžně sdílená sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
  
 [Nasazení](/dotnet/framework/deployment/index)  
  
 [Řešení potíží s C/C++ izolované aplikace a souběžně sdílená sestavení](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)