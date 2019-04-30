---
title: Koncepty nasazení
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
ms.openlocfilehash: ec472e506e78a57b65186bf6a5b801419fb141fb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346404"
---
# <a name="deployment-concepts"></a>Koncepty nasazení

Tato část popisuje hlavní aspekty pro nasazení aplikací v jazyce C++.

## <a name="windows-installer-deployment-in-c"></a>Nasazení Instalační služby systému Windows v jazyce C++

Projekty Visual C++ obvykle používat tradiční instalace Instalační služby systému Windows pro nasazení. Příprava nasazení Instalační služby systému Windows, balíček aplikace do souboru setup.exe a distribuovat tento soubor, společně s balíčkem aplikace Instalační služby (MSI). Uživatelé pak spusťte setup.exe pro instalaci vaší aplikace.

Zabalení aplikace tak, že přidáte do svého řešení; projektu instalace Při sestavování, vytvoří instalační program a instalační program soubory balíčku, které můžete distribuovat uživatelům. Další informace najdete v tématu [volba metody nasazení](choosing-a-deployment-method.md).

## <a name="library-dependencies"></a>Závislé položky knihoven

Při vytváření aplikace v jazyce C/C++ pomocí funkce poskytované službou knihoven Visual C++, bude závislá na přítomnost tyto knihovny za běhu. V pořadí pro spuštění aplikace je třeba propojit, staticky nebo dynamicky, potřebné knihovny Visual C++. Pokud aplikace dynamicky odkazy na knihovny Visual C++, pak při spuštění této knihovny musí být k dispozici, je možné načíst. Na druhé straně Pokud aplikace staticky odkazuje na knihovny Visual C++, pak nemusí odpovídající knihovny DLL, aby byly v počítači uživatele. Statické propojení, ale má některé negativní důsledky, jako je například zvýšení velikosti souborů aplikace a provádění údržby potenciálně obtížnější. Další informace najdete v tématu [výhody použití knihoven DLL](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls).

## <a name="packaging-and-redistributing"></a>Balení a opětovná distribuce

Knihovny Visual C++ jsou dodávány jako knihovny DLL a nainstalují všechny potřebné knihovny pro aplikace C/C++ pomocí sady Visual Studio na počítači pro vývojáře. Ale při nasazení aplikace pro vaše uživatele, není ale ve většině případů tak, aby vyžadovala je instalace sady Visual Studio, aby bylo možné aplikaci spustit. Je důležité moct dál distribuovat pouze ty části sady Visual C++, které vyžaduje pro správné spuštění vaší aplikace.

Další informace o vytváření balíčků a opětovná distribuce naleznete v následujících tématech:

- [Určení, které knihovny DLL je třeba redistribuovat](determining-which-dlls-to-redistribute.md).

- [Volba metody nasazení](choosing-a-deployment-method.md).

- [Nasazení Universal CRT](universal-crt-deployment.md).

Příklady nasazení a návrhy řešení potíží najdete v tématu:

- [Příklady nasazení](deployment-examples.md).

- [Řešení potíží s C/C++ izolované aplikace a sestavení vedle sebe](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

## <a name="see-also"></a>Viz také:

- [Nasazení aplikací klasické pracovní plochy](deploying-native-desktop-applications-visual-cpp.md)
- [Principy závislostí v aplikacích Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md)
