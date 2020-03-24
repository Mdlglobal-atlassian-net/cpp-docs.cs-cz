---
title: Nasazení nativních aplikací klasické pracovní plochy (Visual C++)
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
ms.topic: overview
ms.openlocfilehash: e9ae5db05c0835bb65a65cdccf58ab7f7d1b789f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160187"
---
# <a name="deploying-native-desktop-applications-visual-c"></a>Nasazení nativních aplikací klasické pracovní plochy (Visual C++)

Nasazení je proces, při kterém distribuujete dokončenou aplikaci nebo komponentu k instalaci na jiné počítače. Plánování nasazení začne při vytvoření aplikace v počítači vývojáře. Nasazení skončí při instalaci aplikace a připraveném ke spuštění v počítači uživatele.

Visual Studio poskytuje různé technologie pro nasazování aplikací pro Windows. Patří mezi ně nasazení ClickOnce a nasazení Instalační služba systému Windows.

- ClickOnce lze použít k nasazení C++ aplikací, které cílí na modul CLR (Common Language Runtime) – smíšené, čisté a ověřitelné sestavení. I když můžete použít Instalační služba systému Windows k nasazení spravované aplikace, doporučujeme, abyste používali ClickOnce, protože využívá výhod .NET Framework funkcí zabezpečení, jako je podepisování manifestu. ClickOnce nepodporuje nasazení nativních C++ aplikací. Další informace naleznete v tématu [nasazení ClickOnce pro vizuální C++ aplikace](clickonce-deployment-for-visual-cpp-applications.md).

- Instalační služba systému Windows technologie lze použít k nasazení nativních C++ aplikací nebo C++ aplikací, které cílí na CLR.

Články v této části dokumentace obsahují informace o tom, jak zajistit, aby nativní vizuální C++ aplikace běžela na jakémkoli počítači, který poskytuje podporovanou cílovou platformu, které soubory musíte zahrnout do instalačního balíčku, a doporučené způsoby, jak distribuovat součásti, na kterých vaše aplikace závisí.

## <a name="in-this-section"></a>V tomto oddílu

- [Nasazení ve Visual C++](deployment-in-visual-cpp.md)

- [Koncepty nasazení](deployment-concepts.md)

- [Principy závislostí v aplikacích Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md)

- [Zjištění, které knihovny DLL je třeba redistribuovat](determining-which-dlls-to-redistribute.md)

- [Volba metody nasazení](choosing-a-deployment-method.md)

- [Nasazení univerzálního CRT](universal-crt-deployment.md)

- [Redistribuce souborů Visual C++](redistributing-visual-cpp-files.md)

- [Příklady nasazení](deployment-examples.md)

- [Redistribuce klientských webových aplikací](redistributing-web-client-applications.md)

- [ClickOnce – nasazení pro aplikace Visual C++](clickonce-deployment-for-visual-cpp-applications.md)

- [Spuštění aplikace C++ /CLR v předchozí verzi modulu runtime](running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>Související oddíly

- [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [Nasazení](/dotnet/framework/deployment/index)

- [Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
