---
title: "Instalace podpory C++ v sadě Visual Studio | Microsoft Docs"
description: "Nainstalovat Visual Studio – podpora pro Visual C++"
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: get-started-article
ms.technology: devlang-C++
ms.devlang: C++
dev_langs: C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b895569e5535fb05c1e2383df224f149815dd47f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="install-c-support-in-visual-studio"></a>Instalace podpory C++ v sadě Visual Studio

Pokud jste to ještě stáhli a nainstalovali Visual Studio a nástroje Visual C++ ještě, zde je postup Začínáme.

## <a name="prerequisites"></a>Požadavky

- Širokopásmové připojení k Internetu. Několik GB dat můžete stáhnout instalační program sady Visual Studio.

- Počítače se systémem Microsoft Windows 7 nebo novější verze. Pro dosažení co nejlepších výsledků vývoj doporučujeme Windows 10. Ujistěte se, že nejnovější aktualizace se použijí k vašemu systému, před instalací sady Visual Studio.

- Dostatek volného místa na disku. Visual Studio vyžaduje alespoň 7GB místa na disku a může trvat 50GB nebo více, pokud jsou nainstalovány mnoho běžných možností. Doporučujeme, abyste že ho nainstalujete na jednotce C:.

Podrobnosti na místo na disku a požadavky na operační systém najdete v tématu [2017 požadavky sady Visual Studio](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs). Instalační program sestavy, kolik místa na disku je vyžadován pro možnosti, které vyberete.

## <a name="installation"></a>Instalace

1. Stáhněte si nejnovější verzi instalačního programu Visual Studio 2017 pro systém Windows.

   > [!div class="nextstepaction"]
   > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&utm_source=docs&utm_medium=clickbutton">Nainstalovat Visual Studio 2017 Community</a>

   >[!Tip]
   > Community edition je pro jednotlivé vývojáři, učebny learning, academic výzkum a vývoj s otevřeným zdrojem. Pro jiné účely, nainstalujte <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&utm_source=docs&utm_medium=clickbutton">Visual Studio 2017 Professional</a> nebo <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&utm_source=docs&utm_medium=clickbutton">Visual Studio 2017 Enterprise</a>.

1. Najít soubor instalačního programu můžete stáhnout a spustit ho. Může se zobrazit v prohlížeči nebo může být ve složce pro stahování. Instalační program potřebuje správce oprávnění ke spouštění. Může se zobrazit **řízení uživatelských účtů** dialogové okno s výzvou, abyste udělit oprávnění, aby instalační program provést změny v systému; zvolte **Ano**. Pokud máte potíže, najít stažený soubor v Průzkumníku souborů, klikněte pravým tlačítkem myši na ikonu instalační program a vybrat **spustit jako správce** v místní nabídce.

   ![Spusťte instalační program Visual Studio 2017](../build/media/vscpp-concierge-run-installer.gif "spusťte instalační program sady Visual Studio")

1. Instalační program nabídne seznam úloh, které jsou skupiny související možnosti jsou pro vývoj pro konkrétní oblasti. Podpora pro jazyk C++ je teď součástí volitelné úlohy, které nejsou ve výchozím nastavení nainstalovaná.

   ![Vývoj aplikací s jazykem C++](../build/media/desktop-development-with-cpp.png "vývoj aplikací s C++")

    Pro jazyk C++, vyberte **vývoj aplikací s jazykem C++** zatížení a potom zvolte **nainstalovat**.

   ![Nainstalujte vývoj aplikací C++ zatížení](../build/media/vscpp-concierge-choose-workload.gif "nainstalovat vývoj aplikací C++ zatížení")

1. Po dokončení instalace, vyberte **spusťte** tlačítko ke spuštění sady Visual Studio.

   Při prvním spuštění Visual Studio, budete vyzváni k přihlášení pomocí Account Microsoft. Pokud nemáte, můžete jeden vytvořit zdarma. Musíte také zvolit jen motiv. Nemusíte si dělat starosti, pokud chcete ho můžete změnit později. 

   Visual Studio to trvat několik minut na získat připravený k použití poprvé, můžete ji spustit. Zde je, jak vypadá v nějakou rychlou časové závislosti:

   ![Visual Studio 2017 přihlásit](../build/media/vscpp-quickstart-first-run.gif "přihlášení Visual Studio 2017")

   Visual Studio se mnohem rychleji spustí, když znovu spusťte.

1. Když Visual Studio otevře, zkontrolujte, pokud je označený na ikonu příznaku v záhlaví:

   ![Příznak oznámení Visual Studio 2017](../build/media/vscpp-first-start-page-flag.png "příznak oznámení Visual Studio 2017")

   Pokud zvýrazní, vyberte ho otevřete **oznámení** okno. Pokud žádné aktualizace nejsou k dispozici pro sadu Visual Studio, doporučujeme, abyste že je teď nainstalujete. Po dokončení instalace restartujte Visual Studio.

Po spuštění sady Visual Studio, jste připraveni pokračovat k dalšímu kroku.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Vytvoření projektu jazyka C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
