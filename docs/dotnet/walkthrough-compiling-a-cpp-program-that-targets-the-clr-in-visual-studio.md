---
title: Kompilace programu C++/CLI pro CLR
description: Pomocí aplikace Microsoft C++ můžete vytvářet programy a knihovny, které mohou připojit nativní kód Jazyka C++ a programy .NET.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 0d661d9e77211a0e49f8695ad713b607377a236a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371815"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Návod: Kompilace programu C++/CLI, který cílí na CLR v sadě Visual Studio

Pomocí jazyka C++/CLI můžete vytvářet programy jazyka C++, které používají třídy .NET i nativní typy C++. Rozhraní C++/CLI je určeno pro použití v konzolových aplikacích a v knihovnách DLL, které zalamují nativní kód jazyka C++ a zpřístupňují jej z programů .NET. Chcete-li vytvořit uživatelské rozhraní systému Windows založené na rozhraní .NET, použijte c# nebo visual basic.

Pro tento postup můžete zadat vlastní program jazyka C++ nebo použít jeden z ukázkových programů. Ukázkový program, který použijeme v tomto postupu, vytvoří textový soubor s názvem textfile.txt a uloží jej do adresáře projektu.

## <a name="prerequisites"></a>Požadavky

- Pochopení základů jazyka C++.
- V sadě Visual Studio 2017 a novější je podpora C++/CLI volitelnou součástí. Chcete-li ji nainstalovat, otevřete **instalační službu sady Visual Studio** z nabídky Start systému Windows. Ujistěte se, že je **zaškrtnuto vývoj plochy s c++** dlaždice a v části **Volitelné** komponenty také zkontrolujte **podporu C++/CLI**.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Následující kroky se liší v závislosti na verzi sady Visual Studio, kterou používáte. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>Vytvoření projektu C++/CLI v Sadě Visual Studio 2019

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na hoře a otevřete dialogové okno **Vytvořit nový projekt.**

1. V horní části dialogového okna zadejte **clr** do vyhledávacího pole a pak ze seznamu výsledků zvolte **PRÁZDNÝ projekt CLR.**

1. Chcete-li vytvořit projekt, zvolte tlačítko **Vytvořit.**

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>Vytvoření projektu C++/CLI v Sadě Visual Studio 2017

1. Vytvoření nového projektu V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **položku Project**.

1. V typech projektu Visual C++ klikněte na **CLR**a potom klikněte na **příkaz CLR Prázdný projekt**.

1. Zadejte název projektu. Ve výchozím nastavení má řešení, které obsahuje projekt, stejný název jako nový projekt, ale můžete zadat jiný název. Pokud chcete, můžete pro projekt zadat jiné umístění.

1. Chcete-li vytvořit nový projekt, klepněte na tlačítko **OK.**

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>Vytvoření projektu C++/CLI v Sadě Visual Studio 2015

1. Vytvoření nového projektu V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **položku Project**.

1. V typech projektu Visual C++ klikněte na **CLR**a potom klikněte na **příkaz CLR Prázdný projekt**.

1. Zadejte název projektu. Ve výchozím nastavení má řešení, které obsahuje projekt, stejný název jako nový projekt, ale můžete zadat jiný název. Pokud chcete, můžete pro projekt zadat jiné umístění.

1. Chcete-li vytvořit nový projekt, klepněte na tlačítko **OK.**

::: moniker-end

## <a name="add-a-source-file"></a>Přidání zdrojového souboru

1. Pokud **Průzkumník řešení** není viditelný, klikněte v nabídce **Zobrazení** na **Průzkumník řešení.**

1. Přidejte do projektu nový zdrojový soubor:

   - Klepněte pravým tlačítkem myši na složku **Zdrojové soubory** v **Průzkumníku řešení**, přejděte na **Přidat**a klepněte na příkaz **Nová položka**.

   - Klikněte na **Soubor C++ (.cpp),** zadejte název souboru a potom klikněte na **Přidat**.

   Soubor **CPP** se zobrazí ve složce **Zdrojové soubory** v **Průzkumníku řešení** a zobrazí se okno s kartami, kde do tohoto souboru zadáte požadovaný kód.

1. Klikněte na nově vytvořenou kartu v sadě Visual Studio a zadejte platný program Visual C++ nebo zkopírujte a vložte jeden z ukázkových programů.

   Můžete například použít ukázkový program [Jak: Napište textový soubor (C++/CLI)](how-to-write-a-text-file-cpp-cli.md) (v uzlu **Zpracování souborů a V/O** programovacího průvodce).

   Pokud použijete ukázkový program, všimněte `gcnew` si, že používáte klíčové slovo místo`^``*` `new` při vytváření objektu .NET a vrátí `gcnew` popisovač ( ) spíše než ukazatel ( ):

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Další informace o syntaxi jazyka C++/CLI naleznete [v tématu Rozšíření komponent pro platformy runtime](../extensions/component-extensions-for-runtime-platforms.md).

1. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

   Okno **Výstup** zobrazuje informace o průběhu kompilace, jako je například umístění protokolu sestavení a zpráva, která označuje stav sestavení.

   Pokud provedete změny a spustíte program bez sestavení, dialogové okno může znamenat, že projekt je zastaralý. V tomto dialogovém okně zaškrtněte políčko před klepnutím na **tlačítko OK,** pokud chcete, aby visual studio vždy používalo aktuální verze souborů namísto zobrazení výzvy při každém sestavení aplikace.

1. V nabídce **Ladění** klepněte na tlačítko **Start bez ladění**.

1. Pokud jste použili ukázkový program, při spuštění programu se zobrazí příkazové okno, které označuje, že textový soubor byl vytvořen.

   Textový soubor **textfile.txt** je nyní umístěn v adresáři projektu. Tento soubor můžete otevřít pomocí poznámkového bloku.

   > [!NOTE]
   > Výběr prázdné šablony projektu CLR `/clr` automaticky nastaví možnost kompilátoru. Chcete-li to ověřit, klepněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a klepněte na příkaz **Vlastnosti**a potom zkontrolujte možnost **podpora běžného jazyka runtime** v **obecném** uzlu **Vlastnosti konfigurace**.

## <a name="see-also"></a>Viz také

[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>
