---
title: Kompilovat C++vyhodnocovací programu CLR
ms.date: 09/17/2018
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: fcac0079185b6ceef981b9acfeb555ef29d464e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384397"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Návod: Kompilovat C++vyhodnocovací programu CLR v sadě Visual Studio

S použitím C++/jazyková rozšíření rozhraní příkazového řádku můžete vytvářet C++ programy, které používají třídy .NET a kompilovat s použitím vývojového prostředí sady Visual Studio.

Tento postup můžete zadat vlastní program C++ nebo použijte jednu z ukázkových programů. Ukázkový program, který používáme v tomto postupu vytváří textový soubor s názvem textfile.txt a uloží jej do adresáře projektu.

## <a name="prerequisites"></a>Požadavky

Tato témata se předpokládá, že chápete základy jazyka C++.

### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Vytvoření nového projektu v sadě Visual Studio a přidání nového zdrojového souboru

1. Vytvořte nový projekt. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.

1. Typy projektů jazyka Visual C++, klikněte na **CLR**a potom klikněte na tlačítko **prázdný projekt CLR**.

   > [!NOTE]
   > Pokud **prázdný projekt CLR** chybí typ (Visual Studio 2017 pouze), vyberte **otevřít instalační program Visual Studio** v levém podokně **nový projekt** dialogové okno. Možnost umístěna ve složce instalace **vývoj desktopových aplikací pomocí C++**  v **volitelné** součástí oddílu s názvem  **C++podpora rozhraní příkazového řádku**.<br/>

1. Zadejte název projektu.

   Ve výchozím nastavení řešení, které obsahuje projekt má stejný název jako nový projekt, ale můžete zadat jiný název. Pokud chcete, můžete zadat jiné umístění pro projekt.

   Klikněte na tlačítko **OK** k vytvoření nového projektu.

1. Pokud **Průzkumníka řešení** nezobrazuje, klikněte na tlačítko **Průzkumníka řešení** na **zobrazení** nabídky.

1. Přidání nového zdrojového souboru do projektu:

   - Klikněte pravým tlačítkem na **zdrojové soubory** složky **Průzkumníku řešení**, přejděte na **přidat**a klikněte na tlačítko **nová položka**.

   - Klikněte na tlačítko **soubor C++ (.cpp)** a zadejte název souboru a pak klikněte na tlačítko **přidat**.

   **.Cpp** souboru se zobrazí v **zdrojové soubory** složky **Průzkumníka řešení** a zobrazí se okno s kartami, kde zadejte kód chcete v tomto souboru.

1. Klikněte na kartě nově vytvořené v sadě Visual Studio a zadejte platný program Visual C++, nebo zkopírujte a vložte jednu z ukázkových programů.

   Například můžete použít [jak: Zápis do textového souboru (C++vyhodnocovací)](how-to-write-a-text-file-cpp-cli.md) ukázkový program (v **zpracování souborů a vstupně-výstupních operací** uzel Programming Guide).

   Pokud použijete ukázkový program, Všimněte si, že používáte `gcnew` – klíčové slovo místo `new` při vytváření objektů .NET a že `gcnew` vrátí popisovač (`^`) namísto ukazatel (`*`):

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Další informace o novou syntaxi jazyka Visual C++, naleznete v tématu [přípony komponent pro platformy běhového prostředí](../extensions/component-extensions-for-runtime-platforms.md).

1. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

   **Výstup** okně zobrazí informace o průběhu kompilace, jako je například umístění protokolu sestavení a napište zprávu, která označuje stav sestavení.

   Pokud provedete změny a spusťte program bez provedení sestavení, dialogové okno může znamenat, že projekt je zastaralý. Zaškrtněte políčko v tomto dialogovém okně před kliknutím na **OK** sady Visual Studio, vždy používali aktuální verze souborů namísto dotazování pokaždé, když chcete-li sestavení aplikace.

1. Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.

1. Pokud jste použili ukázkový program při spuštění programu se zobrazí okno příkazového řádku, která označuje, že se vytvořil textového souboru.

   **Textfile.txt** textový soubor se nyní nachází v adresáři projektu. Tento soubor můžete otevřít pomocí poznámkového bloku.

   > [!NOTE]
   > Výběr prázdný CLR šablonu projektu automaticky nastaví `/clr` – možnost kompilátoru. To pokud chcete ověřit, klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a kliknete na **vlastnosti**a potom zaškrtněte políčko **Common Language Runtime support** možnost  **Obecné** uzlu **vlastnosti konfigurace**.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>
