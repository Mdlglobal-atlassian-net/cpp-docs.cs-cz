---
title: Portování třetích stran knihovny | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e831f5441d62a4430fe036be70f1bec5ac99c98
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="porting-third-party-libraries"></a>Portování knihovny třetích stran

Při upgradu na projekt na aktuální verzi Visual C++, máte také upgradovat všechny knihovny, které používá projekt, tak, aby knihovny a projekt jsou postavené stejným verze a příchuť kompilátoru. (Další informace najdete v tématu [přehled potenciální problémy upgradu](overview-of-potential-upgrade-issues-visual-cpp.md)). 

## <a name="introducing-vcpkg"></a>Představení vcpkg
V minulosti byl někdy úlohu netriviální hledání a upgrade 3. stran knihovny. Aby bylo snazší získat a znovu sestavte C++ 3. stran opensourcové knihovny týmu Visual C++ vytvořil nástroj příkazového řádku s názvem **VC ++ balení nástroj** nebo **vcpkg**. Vcpkg má katalog mnoha oblíbených open-source knihovny jazyka C++. V katalogu přímo z příkazového řádku vcpkg můžete nainstalovat všechny knihovny. Při instalaci knihovnu Vcpkg vytvoří v adresářovém stromě na váš počítač a přidá .h, .lib a binární soubory v této složce. Můžete použít tuto složku v kompilaci příkazového řádku, nebo ji integrovat do sady Visual Studio 2015 nebo později pomocí vcpkg integrovat instalační příkaz. Po integraci umístění knihovny sady Visual Studio můžete najít a přidat jej do všech nový projekt, který vytvoříte. Pro použití knihovny, právě #include a Visual Studio automaticky přidat cestu .lib nastavení projektu a zkopírujte do složky řešení knihovnu dll. Další informace najdete v tématu [vcpkg: Správce balíčků pro C++](../vcpkg.md).


## <a name="reporting-issues"></a>Hlášení problémů
Pokud vaše knihovna se nenachází v vcpkg katalogu, můžete otevřít problém na [úložiště GitHub](https://github.com/Microsoft/vcpkg/issues) kde komunita a týmu Visual C++ můžete zobrazovat a potenciálně vytvořit soubor portu pro tuto knihovnu.

Pro chráněné 3. stran knihovny (není otevřený zdroj) doporučujeme obrátit se zprostředkovateli knihovny. Ale jsme zajímá vědět o všechny vlastní knihovny používáte a můžete blokovat, dejte nám vědět, které z nich závisí na (kontaktujte nás na adrese vcupgrade@microsoft.com).

  
## <a name="see-also"></a>Viz také  
 [Průvodce přenosem a upgradem Visual C++](visual-cpp-porting-and-upgrading-guide.md)
