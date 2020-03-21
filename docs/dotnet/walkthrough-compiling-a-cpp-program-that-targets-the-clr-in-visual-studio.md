---
title: Zkompilovat program C++/CLI, který cílí na CLR
description: Použijte Microsoft C++ k vytváření programů a knihoven, které mohou připojit C++ nativní kód a programy .NET.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 36c41856dfcdb5c5f50ba59205b4c73c5fde5963
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080021"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Návod: zkompilujte program C++/CLI, který cílí na CLR v aplikaci Visual Studio.

Pomocí C++/CLI můžete vytvořit C++ programy, které používají třídy .NET, i nativní C++ typy. C++/CLI je určený pro použití v konzolových aplikacích a v knihovnách DLL C++ , které zabalí nativní kód a zpřístupní ho z programů .NET. Chcete-li vytvořit uživatelské rozhraní systému Windows založené na rozhraní C# .NET, použijte nebo Visual Basic.

Pro tento postup můžete zadat vlastní C++ program nebo použít jeden z ukázkových programů. Vzorový program, který používáme v tomto postupu, vytvoří textový soubor s názvem textfile. txt a uloží ho do adresáře projektu.

## <a name="prerequisites"></a>Předpoklady

- Porozumění základům C++ jazyka.
- V aplikaci Visual Studio 2017 nebo novější C++je podpora/CLI volitelnou komponentou. Pokud ho chcete nainstalovat, otevřete **instalační program pro Visual Studio** v nabídce Start systému Windows. Ujistěte se, že je zaškrtnutá možnost **vývoj desktopových aplikací C++**  v dlaždici, a v části **volitelné** komponenty také zkontrolujte  **C++podporu/CLI**.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Následující postup se liší v závislosti na verzi sady Visual Studio, kterou používáte. Ujistěte se, že selektor verzí v levém horním rohu této stránky je nastaven správně.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>Vytvoření projektu C++/CLI v aplikaci Visual Studio 2019

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na horním panelu a otevřete dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna zadejte do vyhledávacího pole **CLR** a pak v seznamu výsledků zvolte **prázdný projekt CLR** .

1. Kliknutím na tlačítko **vytvořit** vytvořte projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>Vytvoření projektu C++/CLI v aplikaci Visual Studio 2017

1. Vytvoření nového projektu V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

1. Z typů projektu C++ vizuálu klikněte na **CLR**a pak klikněte na **prázdný projekt CLR**.

1. Zadejte název projektu. Ve výchozím nastavení má řešení, které obsahuje projekt, stejný název jako nový projekt, ale můžete zadat jiný název. Pokud chcete, můžete zadat jiné umístění projektu.

1. Kliknutím na tlačítko **OK** vytvořte nový projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>Vytvoření projektu C++/CLI v aplikaci Visual Studio 2015

1. Vytvoření nového projektu V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

1. Z typů projektu C++ vizuálu klikněte na **CLR**a pak klikněte na **prázdný projekt CLR**.

1. Zadejte název projektu. Ve výchozím nastavení má řešení, které obsahuje projekt, stejný název jako nový projekt, ale můžete zadat jiný název. Pokud chcete, můžete zadat jiné umístění projektu.

1. Kliknutím na tlačítko **OK** vytvořte nový projekt.

::: moniker-end

## <a name="add-a-source-file"></a>Přidat zdrojový soubor

1. Pokud **Průzkumník řešení** není vidět, klikněte na **Průzkumník řešení** v nabídce **zobrazení** .

1. Přidejte do projektu nový zdrojový soubor:

   - Klikněte pravým tlačítkem na složku **zdrojové soubory** v **Průzkumník řešení**, přejděte na **Přidat**a klikněte na **Nová položka**.

   - Klikněte na  **C++ soubor (. cpp)** , zadejte název souboru a potom klikněte na **Přidat**.

   Soubor **. cpp** se zobrazí ve složce **zdrojové soubory** v **Průzkumník řešení** a zobrazí se okno s kartami, kde zadáte kód, který chcete v tomto souboru.

1. Klikněte na kartu nově vytvořeno v aplikaci Visual Studio a zadejte platný vizuální C++ program nebo zkopírujte a vložte jeden z ukázkových programů.

   Můžete například použít ukázkový program [pro zápis textový souborC++(/CLI)](how-to-write-a-text-file-cpp-cli.md) (v uzlu **zpracování souborů a v/v** Průvodce programováním).

   Použijete-li ukázkový program, Všimněte si, že při vytváření objektu .NET použijete klíčové slovo `gcnew` namísto `new` a `gcnew` vrátí popisovač (`^`) místo ukazatele (`*`):

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Další informace o C++syntaxi/CLI najdete v tématu [rozšíření komponent pro platformy běhového prostředí](../extensions/component-extensions-for-runtime-platforms.md).

1. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

   V okně **výstup** se zobrazí informace o průběhu kompilace, jako je například umístění protokolu sestavení a zpráva, která označuje stav sestavení.

   Pokud provedete změny a spustíte program bez sestavení, může dialogové okno značit, že projekt je zastaralý. Zaškrtněte políčko v tomto dialogovém okně před kliknutím na tlačítko **OK** , pokud chcete, aby aplikace Visual Studio vždy používala aktuální verze souborů místo zobrazení výzvy pokaždé, když aplikace sestaví.

1. V nabídce **ladit** klikněte na **Spustit bez ladění**.

1. Pokud jste použili vzorový program, zobrazí se při spuštění programu okno příkazového řádku, které indikuje, že byl vytvořen textový soubor.

   Textový soubor **textfile. txt** se teď nachází v adresáři projektu. Tento soubor můžete otevřít pomocí poznámkového bloku.

   > [!NOTE]
   > Zvolením prázdné šablony projektu CLR se automaticky nastaví možnost kompilátoru `/clr`. Chcete-li to ověřit, klikněte pravým tlačítkem myši na projekt v **Průzkumník řešení** a klikněte na příkaz **vlastnosti**a poté zaškrtněte možnost **Podpora modulu Common Language Runtime** v uzlu **Obecné** v části **Vlastnosti konfigurace**.

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>
