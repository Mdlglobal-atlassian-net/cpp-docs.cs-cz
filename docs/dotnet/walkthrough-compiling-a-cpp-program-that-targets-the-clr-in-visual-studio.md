---
title: Kompilovat C++vyhodnocovací programu CLR
description: Použijte Microsoft C++ k vytvoření programů a knihoven, které se můžete připojit nativní C++ kódu a programy .NET.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 8462b2b031bdcdebf65d58974c521d80e57d856d
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221804"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Návod: Kompilovat C++vyhodnocovací programu CLR v sadě Visual Studio

S použitím C++/rozhraní příkazového řádku můžete vytvářet C++ programy, které používají třídy rozhraní .NET, stejně jako nativní C++ typy. C++/ CLI je určena pro použití v konzolových aplikací a knihoven DLL, které balí nativní C++ kódu a zpřístupněte ho z aplikací .NET. Chcete-li vytvořit uživatelské rozhraní Windows založené na rozhraní .NET, použijte C# nebo Visual Basic. 

Tento postup můžete zadat vlastní program C++ nebo použijte jednu z ukázkových programů. Ukázkový program, který používáme v tomto postupu vytváří textový soubor s názvem textfile.txt a uloží jej do adresáře projektu.

## <a name="prerequisites"></a>Požadavky

- Porozumění základům jazyka C++.
- V sadě Visual Studio 2017 nebo novější C++/podpora rozhraní příkazového řádku je jako volitelná součást. Chcete-li ji nainstalovat, otevřete **instalační program sady Visual Studio** v nabídce Windows Start. Ujistěte se, že **vývoj desktopových aplikací pomocí C++**  dlaždice je zaškrtnuto a **volitelné** sekci součásti také zkontrolujte,  **C++podpora rozhraní příkazového řádku**.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Následující postup se liší v závislosti na tom, kterou verzi sady Visual Studio, kterou používáte. Ujistěte se, že se že volič verze v levé horní části této stránky jsou správně nastavena.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>Chcete-li vytvořit C++vyhodnocovací projektu v aplikaci Visual Studio 2019

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na horní části otevřete **vytvořte nový projekt** dialogové okno.

1. V horní části dialogového okna zadejte **CLR** do vyhledávacího pole a klikněte na tlačítko **prázdný projekt CLR** ze seznamu výsledků. 

1. Zvolte **vytvořit** tlačítko pro vytvoření projektu.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>Chcete-li vytvořit C++vyhodnocovací projektu v sadě Visual Studio 2017

1. Vytvořte nový projekt. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.

1. Typy projektů jazyka Visual C++, klikněte na **CLR**a potom klikněte na tlačítko **prázdný projekt CLR**.

1. Zadejte název projektu. Ve výchozím nastavení řešení, které obsahuje projekt má stejný název jako nový projekt, ale můžete zadat jiný název. Pokud chcete, můžete zadat jiné umístění pro projekt.

1. Klikněte na tlačítko **OK** k vytvoření nového projektu.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>Chcete-li vytvořit C++vyhodnocovací projektu v sadě Visual Studio 2015

1. Vytvořte nový projekt. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.

1. Typy projektů jazyka Visual C++, klikněte na **CLR**a potom klikněte na tlačítko **prázdný projekt CLR**.

1. Zadejte název projektu. Ve výchozím nastavení řešení, které obsahuje projekt má stejný název jako nový projekt, ale můžete zadat jiný název. Pokud chcete, můžete zadat jiné umístění pro projekt.

1. Klikněte na tlačítko **OK** k vytvoření nového projektu.

::: moniker-end

## <a name="add-a-source-file"></a>Přidání zdrojového souboru

1. Pokud **Průzkumníka řešení** nezobrazuje, klikněte na tlačítko **Průzkumníka řešení** na **zobrazení** nabídky.

1. Přidání nového zdrojového souboru do projektu:

   - Klikněte pravým tlačítkem na **zdrojové soubory** složky **Průzkumníku řešení**, přejděte na **přidat**a klikněte na tlačítko **nová položka**.

   - Klikněte na tlačítko **soubor C++ (.cpp)** a zadejte název souboru a pak klikněte na tlačítko **přidat**.

   **.Cpp** souboru se zobrazí v **zdrojové soubory** složky **Průzkumníka řešení** a zobrazí se okno s kartami, kde zadejte kód chcete v tomto souboru.

1. Klikněte na kartě nově vytvořené v sadě Visual Studio a zadejte platný program Visual C++, nebo zkopírujte a vložte jednu z ukázkových programů.

   Například můžete použít [jak: Zápis do textového souboru (C++vyhodnocovací)](how-to-write-a-text-file-cpp-cli.md) ukázkový program (v **zpracování souborů a vstupně-výstupních operací** uzel Programming Guide).

   Pokud použijete ukázkový program, Všimněte si, že používáte `gcnew` – klíčové slovo místo `new` při vytváření objektů .NET a že `gcnew` vrátí popisovač (`^`) namísto ukazatel (`*`):

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Další informace o C++vyhodnocovací syntaxe, naleznete v tématu [přípony komponent pro platformy běhového prostředí](../extensions/component-extensions-for-runtime-platforms.md).

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
