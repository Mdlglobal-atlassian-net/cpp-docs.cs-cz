---
title: Použití prostředí IDE sady Visual Studio pro vývoj aplikací klasické pracovní plochy v jazyce C++
ms.date: 04/25/2019
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
ms.openlocfilehash: 082aa353d3046d9c9b20669e075e200c96017bce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371754"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>Použití prostředí IDE sady Visual Studio pro vývoj aplikací klasické pracovní plochy v jazyce C++

Integrované vývojové prostředí sady Visual Studio (IDE) nabízí sadu funkcí, které vám pomohou spravovat velké a malé projekty kódu, psát a refaktorovat kód a zjišťovat a opravovat chyby pomocí statické analýzy a výkonných ladicích nástrojů. Tato sada článků je navržena tak, aby vás provedla jednotlivými kroky, které budete potřebovat ke správě projektů, psaní, testování a ladění kódu a jeho následnému nasazení do jiného počítače.

## <a name="prerequisites"></a>Požadavky

Pokud jste visual studio ještě nenainstalovali, je teď čas. Odkazy ke stažení a rychlý návod najdete [v tématu Instalace podpory jazyka C++ v sadě Visual Studio](../build/vscpp-step-0-installation.md). Další informace o tom, jak nainstalovat Visual Studio obecně a tipy pro řešení potíží, pokud se něco pokazí, naleznete v [tématu Instalace sady Visual Studio](/visualstudio/install/install-visual-studio). Nezapomeňte zvolit **vývoj plochy s úlohami Jazyka C++** tak, aby při instalaci sady Visual Studio zahrnovaly kompilátory, nástroje a knihovny jazyka C++, protože nejsou ve výchozím nastavení nainstalovány.

Tyto návody předpokládají, že jste nainstalovali Visual Studio a součásti Jazyka C++ potřebné pro vývoj plochy systému Windows. Také předpokládáme, že rozumíte základům jazyka C++. Pokud se potřebujete naučit C++, existuje mnoho knih a webových zdrojů k dispozici. Jedním z dobrých míst, kde začít, je stránka [Začínáme](https://isocpp.org/get-started) na webu Standard C++ Foundation.

Pokud jste visual studio ještě nenainstalovali, je teď čas. Obecně doporučujeme používat Visual Studio 2019 i v případě, že potřebujete zkompilovat kód pomocí kompilátoru Visual Studio 2017 nebo Visual Studio 2015. Další informace naleznete v [tématu Použití nativního vícenásobného cílení v sadě Visual Studio k vytváření starých projektů](../porting/use-native-multi-targeting.md).

**Instalace Visual Studia 2019**

Chcete-li získat Visual Studio 2019, můžete si jej stáhnout z [visual studia ke stažení](https://www.visualstudio.com/downloads/). Nezapomeňte zahrnout vývojové nástroje jazyka C++ při instalaci sady Visual Studio, protože nejsou nainstalovány ve výchozím nastavení. Další informace o instalaci sady Visual Studio naleznete v [tématu Instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

**Instalace visual studia 2017**

Chcete-li získat Visual Studio 2017, můžete si jej stáhnout z [stáhnout starší verze sady Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Nezapomeňte zahrnout vývojové nástroje jazyka C++ při instalaci sady Visual Studio, protože nejsou nainstalovány ve výchozím nastavení. Další informace o instalaci sady Visual Studio naleznete v [tématu Instalace sady Visual Studio](/visualstudio/install/install-visual-studio). Pokyny pro Visual Studio 2017, nastavte ovládací prvek pro výběr **verze** Visual Studia na Visual Studio 2017. Nachází se v horní části obsahu na stránce.

**Instalace visual studia 2015**

Pokud chcete nainstalovat Visual Studio 2015, přejděte ke [stažení starších verzí sady Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Spusťte instalační program a zvolte **Vlastní instalace** a pak zvolte komponentu C++.

Po dokončení instalace sady Visual Studio jste připraveni pokračovat.

## <a name="get-started"></a>Začínáme

Chcete-li začít používat ide Visual Studio k vytváření aplikací c++, propracujte každé z těchto témat v pořadí. Každý z nich vychází z práce, kterou jste dokončili v předchozích tématech:

- [Návod: Práce s projekty a řešeními (C++)](walkthrough-working-with-projects-and-solutions-cpp.md)

- [Návod: Sestavení projektu (C++)](walkthrough-building-a-project-cpp.md)

- [Návod: Testování projektu (C++)](walkthrough-testing-a-project-cpp.md)

- [Návod: Ladění projektu (C++)](walkthrough-debugging-a-project-cpp.md)

- [Návod: Nasazení programu (C++)](walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>Další kroky

Po dokončení těchto návodů jste připraveni začít vytvářet vlastní projekty. Další informace a prostředky pro vývoj jazyka C++ naleznete [v tématu Visual C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md).

## <a name="see-also"></a>Viz také

[Začínáme s vývojem s Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)
