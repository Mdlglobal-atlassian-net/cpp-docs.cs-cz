---
title: Nasazení nativních aplikací klasické pracovní plochy (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f4aa355c132b4c94f085cbdf7aa73785357d0f0
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="deploying-native-desktop-applications-visual-c"></a>Nasazení nativních aplikací klasické pracovní plochy (Visual C++)

Nasazení je proces, pomocí kterého distribuujete dokončenou aplikaci nebo součásti k instalaci na jiných počítačích. Plánování nasazení spustí, když aplikace je vytvořena na počítači pro vývojáře. Nasazení končí, když je aplikace nainstalované a připravené ke spuštění v počítači uživatele.

Visual Studio poskytuje různé technologie pro nasazení aplikace systému Windows. Ty zahrnují nasazení ClickOnce a instalační služba systému Windows.

- ClickOnce lze použít k nasazení aplikací C++, které cílí common language runtime (CLR) – smíšené, čisté a ověřitelné sestavení. I když instalační služba systému Windows můžete nasadit spravované aplikace, doporučujeme použít ClickOnce, protože ho využívá funkce zabezpečení rozhraní .NET Framework například podepsání manifestu. ClickOnce nepodporuje nasazení nativních aplikací C++. Další informace najdete v tématu [ClickOnce – nasazení pro aplikace Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md).

- Technologie Instalační služby systému Windows můžete použít k nasazení nativních aplikací C++ nebo aplikací C++ cílených modulu CLR.

Články v této části dokumentace popisuje zajistit, že na libovolném počítači, který poskytuje podporované cílovou platformu, soubory, které je nutné zahrnout instalační balíček a doporučené způsoby, jak funguje nativní aplikace Visual C++ znovu distribuovat součásti, které vaše aplikace závisí.

## <a name="in-this-section"></a>V tomto oddílu

- [Nasazení ve Visual C++](../ide/deployment-in-visual-cpp.md)

- [Koncepty nasazení](../ide/deployment-concepts.md)

- [Principy závislostí v aplikacích Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)

- [Zjištění, které knihovny DLL je třeba redistribuovat](../ide/determining-which-dlls-to-redistribute.md)

- [Volba metody nasazení](../ide/choosing-a-deployment-method.md)

- [Universal CRT nasazení](universal-crt-deployment.md).

- [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md)

- [Příklady nasazení](../ide/deployment-examples.md)

- [Redistribuce klientských webových aplikací](../ide/redistributing-web-client-applications.md)

- [ClickOnce – nasazení pro aplikace Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md)

- [C++/CLR aplikace spuštěné v předchozí verzi modulu Runtime](../ide/running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>Související oddíly

- [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [Nasazení](/dotnet/framework/deployment/index)

- [Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)