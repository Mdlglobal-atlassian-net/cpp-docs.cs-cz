---
title: Použití prostředí IDE sady Visual Studio pro vývoj aplikací klasické pracovní plochy v jazyce C++
ms.date: 04/25/2019
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
ms.openlocfilehash: 2cf2844fd4247c3c69648823302a6ad56ff5fd45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171773"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>Použití prostředí IDE sady Visual Studio pro vývoj aplikací klasické pracovní plochy v jazyce C++

Integrované vývojové prostředí (IDE) sady Visual Studio nabízí sadu funkcí, které vám pomůžou se správou velkých a malých kódových projektů, psaní a refaktorování kódu a detekce a opravy chyb pomocí statické analýzy a výkonných nástrojů pro ladění. Tato sada článků je navržena tak, aby vás provedla jednotlivými kroky, budete muset spravovat projekty, zapisovat, testovat a ladit kód a pak ho nasadit na jiný počítač.

## <a name="prerequisites"></a>Požadavky

Pokud jste ještě nenainstalovali Visual Studio, teď je to čas. Odkazy ke stažení a rychlý návod najdete v tématu [instalace C++ podpory v aplikaci Visual Studio](../build/vscpp-step-0-installation.md). Další informace o tom, jak nainstalovat Visual Studio obecně, a tipy pro řešení potíží, pokud se něco nepovede, najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio). Nezapomeňte při instalaci sady Visual Studio zvolit **desktopový vývoj s C++**  úlohou, který zahrnuje C++ kompilátory, nástroje a knihovny, protože nejsou nainstalované ve výchozím nastavení.

V C++ těchto návodech se předpokládá, že máte nainstalovanou aplikaci Visual Studio a součásti potřebné pro vývoj desktopových aplikací pro Windows. Předpokládáme také, že rozumíte základům tohoto C++ jazyka. Pokud se potřebujete naučit C++, máte k dispozici mnoho knih a webových prostředků. První dobrým místem, kde začít [je stránka Začínáme](https://isocpp.org/get-started) na webu standard C++ Foundation.

Pokud jste ještě nenainstalovali Visual Studio, teď je to čas. Obecně doporučujeme, abyste používali Visual Studio 2019 i v případě, že potřebujete zkompilovat kód pomocí kompilátoru Visual Studio 2017 nebo Visual Studio 2015. Další informace naleznete v tématu [použití nativního cílení na více platforem v aplikaci Visual Studio k sestavení starých projektů](../porting/use-native-multi-targeting.md).

**Instalace sady Visual Studio 2019**

Pokud chcete získat Visual Studio 2019, můžete si ho stáhnout ze [souborů ke stažení pro Visual Studio](https://www.visualstudio.com/downloads/). Nezapomeňte zahrnout vývojové nástroje při C++ instalaci sady Visual Studio, protože nejsou ve výchozím nastavení nainstalovány. Další informace o tom, jak nainstalovat Visual Studio, najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio).

**Instalace sady Visual Studio 2017**

Chcete-li získat sadu Visual Studio 2017, můžete si ji stáhnout ze složky [Stáhnout starší verze sady Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Nezapomeňte zahrnout vývojové nástroje při C++ instalaci sady Visual Studio, protože nejsou ve výchozím nastavení nainstalovány. Další informace o tom, jak nainstalovat sadu Visual Studio, najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio) a nastavení výběru verzí na stránce na sadu **Visual Studio 2017**.

**Instalace sady Visual Studio 2015**

Pokud chcete nainstalovat sadu Visual Studio 2015, Projděte si [část stažení starších verzí sady Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Spusťte instalační program a zvolte možnost **vlastní instalace** a pak zvolte C++ součást.

Po dokončení instalace sady Visual Studio budete připraveni pokračovat.

## <a name="get-started"></a>Začínáme

Chcete-li začít používat integrované vývojové prostředí (IDE C++ ) sady Visual Studio k vytváření aplikací, pracujte prostřednictvím každé z těchto témat v daném pořadí. Každé sestavení na práci, kterou jste dokončili v předchozích tématech:

- [Návod: Práce s projekty a řešeními (C++)](walkthrough-working-with-projects-and-solutions-cpp.md)

- [Návod: Sestavení projektu (C++)](walkthrough-building-a-project-cpp.md)

- [Návod: Testování projektu (C++)](walkthrough-testing-a-project-cpp.md)

- [Návod: Ladění projektu (C++)](walkthrough-debugging-a-project-cpp.md)

- [Návod: Nasazení programu (C++)](walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>Další kroky

Po dokončení těchto návodů jste připraveni začít vytvářet vlastní projekty. Další informace a materiály pro C++ vývoj najdete v tématu [Visual C++ v aplikaci Visual Studio](../overview/visual-cpp-in-visual-studio.md).

## <a name="see-also"></a>Viz také

[Začínáme s vývojem pomocí sady Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)
