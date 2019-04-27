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
ms.openlocfilehash: 46ced4ac5f7952a9b7f66418ea037e053b16e9be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346116"
---
# <a name="deploying-native-desktop-applications-visual-c"></a>Nasazení nativních aplikací klasické pracovní plochy (Visual C++)

Nasazení je proces, pomocí kterého můžete distribuovat dokončenou aplikaci nebo součásti nainstalovat na jiných počítačích. Plánování nasazení se spustí při vytvoření aplikace na počítači pro vývojáře. Nasazení končí, když je aplikace nainstalované a připravené ke spuštění v počítači uživatele.

Visual Studio nabízí různé technologie pro nasazení aplikací pro Windows. Patří mezi ně nasazení ClickOnce a nasazení Instalační služby systému Windows.

- ClickOnce umožňuje nasazení aplikací v jazyce C++, které se zaměřují na modul CLR (CLR) – sestavení smíšené, čisté a ověřitelné. I když instalační služby systému Windows můžete použít k nasazení spravované aplikace, doporučujeme použít ClickOnce, protože využívá funkce zabezpečení rozhraní .NET Framework, jako jsou podepsání manifestu. Technologie ClickOnce nepodporuje nasazení aplikací v nativním jazyce C++. Další informace najdete v tématu [ClickOnce – nasazení pro aplikace Visual C++](clickonce-deployment-for-visual-cpp-applications.md).

- Technologie instalačního programu Windows lze použít k nasazení nativních aplikací v jazyce C++ nebo aplikací v jazyce C++, které se zaměřují modulu CLR.

Články v této části dokumentace popíšeme, jak zajistit, že na každém počítači, který poskytuje podporované cílové platformy, které soubory je třeba zahrnout instalačního balíčku a doporučené způsoby, jak funguje nativní aplikace Visual C++ Redistribuce součástí, které vaše aplikace závisí.

## <a name="in-this-section"></a>V tomto oddílu

- [Nasazení ve Visual C++](deployment-in-visual-cpp.md)

- [Koncepty nasazení](deployment-concepts.md)

- [Principy závislostí v aplikacích Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md)

- [Zjištění, které knihovny DLL je třeba redistribuovat](determining-which-dlls-to-redistribute.md)

- [Volba metody nasazení](choosing-a-deployment-method.md)

- [Nasazení Universal CRT](universal-crt-deployment.md).

- [Redistribuce souborů Visual C++](redistributing-visual-cpp-files.md)

- [Příklady nasazení](deployment-examples.md)

- [Redistribuce klientských webových aplikací](redistributing-web-client-applications.md)

- [ClickOnce – nasazení pro aplikace Visual C++](clickonce-deployment-for-visual-cpp-applications.md)

- [Spuštění aplikace C++/CLR v předchozí verzi modulu Runtime](running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>Související oddíly

- [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [Nasazení](/dotnet/framework/deployment/index)

- [Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)