---
title: Kompilace programu v jazyce C++ pro CLR | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18e9b0c4e23516e763d8dab532e9862cad0177df
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416021"
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>Návod: Kompilace programu C++ pro CLR v aplikaci Visual Studio

Můžete vytvořit programů aplikace Visual C++, které používají třídy rozhraní .NET a kompilovat s použitím vývojového prostředí sady Visual Studio.

Pro tento postup můžete zadat vlastní program Visual C++ nebo použijte jednu z ukázkových programů. Ukázkový program, který používáme v tomto postupu vytváří textový soubor s názvem textfile.txt a uloží jej do adresáře projektu.

## <a name="prerequisites"></a>Požadavky

Tato témata se předpokládá, že chápete základy jazyka C++.

### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Vytvoření nového projektu v sadě Visual Studio a přidání nového zdrojového souboru

1. Vytvořte nový projekt. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.

1. Typy projektů jazyka Visual C++, klikněte na **CLR**a potom klikněte na tlačítko **prázdný projekt CLR**.

1. Zadejte název projektu.

   Ve výchozím nastavení řešení, které obsahuje projekt má stejný název jako nový projekt, ale můžete zadat jiný název. Pokud chcete, můžete zadat jiné umístění pro projekt.

   Klikněte na tlačítko **OK** k vytvoření nového projektu.

1. Pokud se nezobrazí Průzkumník řešení, klikněte na tlačítko **Průzkumníka řešení** na **zobrazení** nabídky.

1. Přidání nového zdrojového souboru do projektu:

   - Klikněte pravým tlačítkem na **zdrojové soubory** složku v Průzkumníku řešení, přejděte na **přidat** a klikněte na tlačítko **nová položka**.

   - Klikněte na tlačítko **soubor C++ (.cpp)** a zadejte název souboru a pak klikněte na tlačítko **přidat**.

   **.Cpp** souboru se zobrazí v **zdrojové soubory** se zobrazí složka v Průzkumníku řešení a okno s kartami, kde zadejte kód chcete v tomto souboru.

1. Klikněte na kartě nově vytvořené v sadě Visual Studio a zadejte platný program Visual C++, nebo zkopírujte a vložte jednu z ukázkových programů.

   Například můžete použít [postupy: zápis do textového souboru (C + +/ CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md) ukázkový program (v **zpracování souborů a vstupně-výstupních operací** uzel Průvodce programováním).

   Pokud použijete ukázkový program, Všimněte si, že používáte `gcnew` – klíčové slovo místo `new` při vytváření objektů .NET a že `gcnew` vrátí popisovač (`^`) namísto ukazatel (`*`):

     `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Další informace o novou syntaxi jazyka Visual C++, naleznete v tématu [přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md).

1. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

   **Výstup** okně zobrazí informace o průběhu kompilace, jako je například umístění protokolu sestavení a napište zprávu, která označuje stav sestavení.

   Pokud provedete změny a spusťte program bez provedení sestavení, dialogové okno může znamenat, že projekt je zastaralý. Zaškrtněte políčko v tomto dialogovém okně před kliknutím na **OK** sady Visual Studio, vždy používali aktuální verze souborů namísto dotazování pokaždé, když chcete-li sestavení aplikace.

1. Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.

9. Pokud jste použili ukázkový program při spuštění programu se zobrazí okno příkazového řádku, která označuje, že se vytvořil textového souboru. Stisknutím jakékoli klávesy zavřete příkazové okno.

   **Textfile.txt** textový soubor se nyní nachází v adresáři projektu. Tento soubor můžete otevřít pomocí poznámkového bloku.

   > [!NOTE]
   >  Výběr prázdný CLR šablonu projektu automaticky nastaví **/CLR** – možnost kompilátoru. To pokud chcete ověřit, klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a kliknete na **vlastnosti**a potom zaškrtněte políčko **Common Language Runtime support** možnost  **Obecné** uzlu **vlastnosti konfigurace**.

## <a name="whats-next"></a>Co se chystá

**Předchozí:** [návod: kompilace nativního programu C++ v příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md) &#124; **Další:**[návod: kompilace programu C na příkazovém řádku](../build/walkthrough-compile-a-c-program-on-the-command-line.md)

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br>
[Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)