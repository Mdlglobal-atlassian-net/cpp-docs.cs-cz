---
title: Koncepty nasazení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0960e94acdbe660474efbeeddd0f72fa4f0606f6
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34257059"
---
# <a name="deployment-concepts"></a>Koncepty nasazení

Tato část popisuje hlavní aspekty pro nasazení aplikací C++.

## <a name="windows-installer-deployment-in-c"></a>Instalační služba systému Windows v jazyce C++

Projekty Visual C++ se obvykle používají tradiční nastavení Instalační služby systému Windows pro nasazení. Příprava nasazení Instalační služby systému Windows, balíček aplikace do souboru setup.exe a distribuovat spolu s instalační balíček (.msi). Uživatelé pak spusťte setup.exe pro instalaci aplikace.

Balíček aplikace přidáním projektu instalace do řešení; Když vytvořen, vytvoří instalační program a instalační program soubory balíčku, které můžete distribuovat uživatelům. Další informace najdete v tématu [volba metody nasazení](../ide/choosing-a-deployment-method.md).

## <a name="library-dependencies"></a>Závislosti knihovny

Když aplikace C/C++ je sestaven pomocí funkce poskytované službou knihovny jazyka Visual C++, stane závisí na přítomnost tyto knihovny za běhu. Aby aplikace spuštěna musí s ní staticky nebo dynamicky, nezbytné knihoven Visual C++. Pokud aplikace dynamicky odkazy knihovnu Visual C++, potom při spuštění této knihovny musí být přítomen, mohou být načteny. Na druhé straně Pokud aplikace staticky odkazuje na knihovnu Visual C++, pak nemusí odpovídající knihovny DLL, aby byly v počítači uživatele. Statické propojení, má však některé nepříznivé vlivy, např. zvýšení velikosti souborů aplikace a provádění údržby potenciálně obtížnější. Další informace najdete v tématu [výhody použití knihoven DLL](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls).

## <a name="packaging-and-redistributing"></a>Balení a redistribuce

Knihoven Visual C++ jsou obsaženy jako knihovny DLL a všechny potřebné knihovny pro C/C++ aplikace jsou nainstalované Visual Studio v počítači pro vývojáře. Ale pokud nasazujete aplikaci pro uživatele, není ale ve většině případů vyžadovat, aby instalaci sady Visual Studio, aby bylo možné aplikaci spustit. Je důležité, abyste mohli distribuovat pouze části Visual C++, které vyžaduje správné fungování aplikace.

Další informace o balení a redistribuce najdete v následujících tématech:

- [Určení, které knihovny DLL je třeba redistribuovat](../ide/determining-which-dlls-to-redistribute.md).

- [Volba metody nasazení](../ide/choosing-a-deployment-method.md).

- [Universal CRT nasazení](universal-crt-deployment.md).

Příklady nasazení a návrhy o řešení potíží najdete v tématu:

- [Příklady nasazení](../ide/deployment-examples.md).

- [Řešení potíží s C/C++ izolované aplikace a souběžně sdílená sestavení](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

## <a name="see-also"></a>Viz také:

- [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [Principy závislostí v aplikacích Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)
- [Instalační služba systému Windows](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)
