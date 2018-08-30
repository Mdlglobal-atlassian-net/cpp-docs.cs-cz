---
title: Koncepty nasazení | Dokumentace Microsoftu
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
ms.openlocfilehash: 16f135011f7b67debdf51f6ddbde00a79d130602
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199688"
---
# <a name="deployment-concepts"></a>Koncepty nasazení

Tato část popisuje hlavní aspekty pro nasazení aplikací v jazyce C++.

## <a name="windows-installer-deployment-in-c"></a>Nasazení Instalační služby systému Windows v jazyce C++

Projekty Visual C++ obvykle používat tradiční instalace Instalační služby systému Windows pro nasazení. Příprava nasazení Instalační služby systému Windows, balíček aplikace do souboru setup.exe a distribuovat tento soubor, společně s balíčkem aplikace Instalační služby (MSI). Uživatelé pak spusťte setup.exe pro instalaci vaší aplikace.

Zabalení aplikace tak, že přidáte do svého řešení; projektu instalace Při sestavování, vytvoří instalační program a instalační program soubory balíčku, které můžete distribuovat uživatelům. Další informace najdete v tématu [volba metody nasazení](../ide/choosing-a-deployment-method.md).

## <a name="library-dependencies"></a>Závislé položky knihoven

Při vytváření aplikace v jazyce C/C++ pomocí funkce poskytované službou knihoven Visual C++, bude závislá na přítomnost tyto knihovny za běhu. V pořadí pro spuštění aplikace je třeba propojit, staticky nebo dynamicky, potřebné knihovny Visual C++. Pokud aplikace dynamicky odkazy na knihovny Visual C++, pak při spuštění této knihovny musí být k dispozici, je možné načíst. Na druhé straně Pokud aplikace staticky odkazuje na knihovny Visual C++, pak nemusí odpovídající knihovny DLL, aby byly v počítači uživatele. Statické propojení, ale má některé negativní důsledky, jako je například zvýšení velikosti souborů aplikace a provádění údržby potenciálně obtížnější. Další informace najdete v tématu [výhody použití knihoven DLL](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls).

## <a name="packaging-and-redistributing"></a>Balení a opětovná distribuce

Knihovny Visual C++ jsou dodávány jako knihovny DLL a nainstalují všechny potřebné knihovny pro aplikace C/C++ pomocí sady Visual Studio na počítači pro vývojáře. Ale při nasazení aplikace pro vaše uživatele, není ale ve většině případů tak, aby vyžadovala je instalace sady Visual Studio, aby bylo možné aplikaci spustit. Je důležité moct dál distribuovat pouze ty části sady Visual C++, které vyžaduje pro správné spuštění vaší aplikace.

Další informace o vytváření balíčků a opětovná distribuce naleznete v následujících tématech:

- [Určení, které knihovny DLL je třeba redistribuovat](../ide/determining-which-dlls-to-redistribute.md).

- [Volba metody nasazení](../ide/choosing-a-deployment-method.md).

- [Nasazení Universal CRT](universal-crt-deployment.md).

Příklady nasazení a návrhy řešení potíží najdete v tématu:

- [Příklady nasazení](../ide/deployment-examples.md).

- [Řešení potíží s C/C++ izolované aplikace a sestavení vedle sebe](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

## <a name="see-also"></a>Viz také:

- [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [Principy závislostí v aplikacích Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)
- [Nasazení Instalační služby systému Windows](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)
