---
title: Instalace podpory jazyka C++ v sadě Visual Studio 2017 | Dokumentace Microsoftu
description: Nainstalovat Visual Studio – podpora pro Visual C++
ms.custom: mvc
ms.date: 09/17/2018
ms.topic: tutorial
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c905df6fb406b9189bd46d20c6f199d3d90a722
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441938"
---
# <a name="install-c-support-in-visual-studio"></a>Instalace podpory jazyka C++ v sadě Visual Studio

Pokud nebyly stáhnout a nainstalovat nástroje Visual C++ a Visual Studio 2017 zatím, tady je postup, abyste mohli začít.

## <a name="prerequisites"></a>Požadavky

- Širokopásmové připojení k Internetu. Několik gigabajtů dat můžete stáhnout instalační program sady Visual Studio.

- Počítač, na kterém běží Microsoft Windows 7 nebo novější verze. Doporučujeme pro nejlepší vývojové prostředí Windows 10. Ujistěte se, že použijí nejnovější aktualizace vašeho systému před instalací sady Visual Studio.

- Dost volného místa na disku. Visual Studio vyžaduje alespoň 7GB místa na disku a může trvat 50GB a více, pokud jsou nainstalovány mnoho běžných možností. Doporučujeme, abyste že ho nainstalujete na jednotce C:.

Podrobnosti o místo na disku a požadavky na operační systém, najdete v části [Visual Studio produktová řada požadavky na systém](/visualstudio/productinfo/vs2017-system-requirements-vs). Instalační program hlásí, kolik místa na disku požadované pro možnosti, které vyberete.

## <a name="visual-studio-2015-installation"></a>Instalace sady Visual Studio 2015

Chcete-li nainstalovat sadu Visual Studio 2015, přejděte na [starší verze sady Visual Studio si můžete stáhnout](https://www.visualstudio.com/vs/older-downloads/). Spusťte instalační program a zvolte **vlastní instalace** a klikněte na tlačítko komponent C++. Chcete-li přidat podporu C++ do existující instalace sady Visual Studio 2015, klikněte na tlačítko Windows Start a typ **přidat nebo odebrat programy**. Otevřete program ze seznamu výsledků a pak v seznamu nainstalovaných programů najít instalaci sady Visual Studio 2015. Poklepejte na něj a pak zvolte **změnit** a vybrat součásti Visual C++ k instalaci.

Obecně platí důrazně doporučujeme použít Visual Studio 2017, i v případě, že budete potřebovat ke kompilaci kódu pomocí kompilátoru Visual Studio 2015. Další informace najdete v tématu [pomocí nativního cílení na více platforem v sadě Visual Studio sestavení starých projektů](../porting/use-native-multi-targeting.md).

## <a name="visual-studio-2017-installation"></a>Instalace sady Visual Studio 2017

1. Stáhněte si nejnovější instalační program sady Visual Studio 2017 pro Windows.

   > [!div class="nextstepaction"]
   > [Nainstalovat sadu Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Edice Community je pro jednotlivé vývojáře, školní výuka, vědecký výzkum a vývoj open source. Pro jiné účely, nainstalujte [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) nebo [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Najdete soubor Instalační program stáhnout a spustit ho. Může se zobrazit v prohlížeči, nebo může být pro vás ve složce stažené soubory. Instalační program potřebuje správce oprávnění ke spuštění. Může se zobrazit **řízení uživatelských účtů** dialogové okno s výzvou, abyste udělili oprávnění, aby instalační program provádět změny systému, zvolte **Ano**. Pokud máte potíže, vyhledejte stažený soubor v Průzkumníku souborů klikněte pravým tlačítkem na ikonu instalační program a zvolte **spustit jako správce** v místní nabídce.

   ![Spusťte instalační program sady Visual Studio 2017](../build/media/vscpp-concierge-run-installer.gif "spusťte instalační program sady Visual Studio")

1. Instalační program vám nabídne seznam úloh, které jsou skupiny související možnosti jsou pro vývoj pro konkrétní oblasti. Podpora jazyka C++ je teď součástí volitelné úlohy, které ve výchozím nastavení nenainstalují.

   ![Vývoj desktopových aplikací pomocí C++](../build/media/desktop-development-with-cpp.png "vývoj desktopových aplikací pomocí C++")

   Pro jazyk C++, vyberte **vývoj desktopových aplikací pomocí C++** úloh a klikněte na tlačítko **nainstalovat**.

   ![Instalace vývoj desktopových aplikací pomocí úlohy pro C++](../build/media/vscpp-concierge-choose-workload.gif "instalace vývoj desktopových aplikací pomocí úlohy pro C++")

1. Po dokončení instalace, zvolte **spuštění** tlačítko pro spuštění sady Visual Studio.

   Při prvním spuštění aplikace Visual Studio, budete vyzváni k přihlášení pomocí pověření Account Microsoft. Pokud ho nemáte, můžete jeden vytvořit zdarma. Musíte také zvolit jen motiv. Nedělejte si starosti, pokud chcete ji můžete změnit později.

   Visual Studio to trvat několik minut, než se připravit k použití při prvním spuštění. Zde je, jak to vypadá v rychlého časové závislosti:

   ![Přihlaste se Visual Studio 2017](../build/media/vscpp-quickstart-first-run.gif "přihlášení Visual Studio 2017")

   Můžete ho spustit znovu spustí aplikace Visual Studio mnohem rychleji.

1. Při otevření sady Visual Studio, zkontrolujte, pokud je zvýrazněn příznak ikona v záhlaví okna:

   ![Příznak oznámení Visual Studio 2017](../build/media/vscpp-first-start-page-flag.png "příznaku oznámení v sadě Visual Studio 2017")

   Pokud je zvýrazněn, vyberte ji a otevřete **oznámení** okna. Pokud nejsou k dispozici pro sadu Visual Studio žádné aktualizace, doporučujeme, abyste že je teď nainstalujete. Po dokončení instalace restartujte Visual Studio.

Když je spuštěná sada Visual Studio, budete chtít pokračovat k dalšímu kroku.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Vytvoření projektu jazyka C++](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
