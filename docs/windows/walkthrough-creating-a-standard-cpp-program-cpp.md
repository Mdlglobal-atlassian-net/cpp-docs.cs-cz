---
title: 'Návod: Vytvoření programu ve standardním C++ (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 105ac62131b45afdea2a445b5888a344f1e4d46c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370224"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Návod: Vytvoření programu ve standardním C++ (C++)

Pomocí sady Visual Studio můžete vytvářet standardní programy jazyka C++. Podle kroků v tomto návodu můžete vytvořit projekt, přidat nový soubor do projektu, upravit soubor pro přidání kódu jazyka C++ a potom zkompilovat a spustit program pomocí sady Visual Studio.

Můžete zadat vlastní program jazyka C++ nebo použít jeden z ukázkových programů. Ukázkový program v tomto návodu je konzolová aplikace. Tato aplikace `set` používá kontejner ve standardní knihovně Jazyka C++.

> [!NOTE]
> Pokud je vyžadována shoda s konkrétní verzí jazykového standardu Jazyka C++ (tj. C++ `/std:c++14` 14 nebo C++17), použijte možnost nebo `/std:c++17` kompilátor. (Visual Studio 2017 a novější.)

## <a name="prerequisites"></a>Požadavky

Předpokladem práce s tímto návodem je znalost základů jazyka C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Vytvoření projektu a přidání zdrojového souboru

Následující kroky se liší v závislosti na verzi sady Visual Studio, kterou používáte. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Vytvoření projektu C++ ve Visual Studiu 2019

1. V hlavní nabídce zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno Vytvořit **nový projekt.**

1. V horní části dialogového okna nastavte **jazyk** na **C++**, nastavte **platformu** na **Systém Windows**a **typ projektu** na **Console**.

1. Z filtrovaného seznamu typů projektů zvolte **Konzolová aplikace** a pak zvolte **Další**. Na další stránce zadejte název projektu a v případě potřeby zadejte umístění projektu.

1. Chcete-li vytvořit projekt, zvolte tlačítko **Vytvořit.**

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Vytvoření projektu C++ ve Visual Studiu 2017

1. Vytvořte projekt tak, že v nabídce **Soubor** přepnete na **Nový** a potom kliknete na **Projekt**.

1. V podokně typů projektů **visual c++** klepněte na **položku Plocha systému Windows**a potom klepněte na **položku Aplikace konzoly systému Windows**.

1. Zadejte název projektu. Ve výchozím nastavení má řešení, které obsahuje projekt, stejný název jako projekt, ale můžete zadat jiný název. Můžete také zadat jiné umístění projektu.

1. Kliknutím na tlačítko **OK** vytvořte projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Vytvoření projektu C++ ve Visual Studiu 2015

1. Vytvořte projekt tak, že v nabídce **Soubor** přepnete na **Nový** a potom kliknete na **Projekt**.

1. V podokně typů projektů **visual c++** klepněte na **položku Plocha systému Windows**a potom klepněte na **položku Aplikace konzoly systému Windows**.

1. V dialogovém okně **Nový projekt** rozbalte**položku** >  **Nainstalované** > šablony**Visual C++** a pak vyberte **Win32**. V prostředním podokně vyberte **možnost Win32 Console Application**.

1. Zadejte název projektu. Ve výchozím nastavení má řešení, které obsahuje projekt, stejný název jako projekt, ale můžete zadat jiný název. Můžete také zadat jiné umístění projektu.

1. Kliknutím na tlačítko **OK** vytvořte projekt.

1. Dokončete **Průvodce aplikací win32**.

1. Klepněte na tlačítko **Další**, zkontrolujte, zda je vybraná **možnost Konzolová aplikace,** a zrušte zaškrtnutí **políčka Předkompilované záhlaví.**

1. Klikněte na **Finish** (Dokončit).

::: moniker-end

## <a name="add-a-new-source-file"></a>Přidání nového zdrojového souboru

1. Pokud **se Průzkumník řešení** nezobrazí, klikněte v nabídce **Zobrazení** na Průzkumník **řešení**.

1. Přidejte do projektu nový zdrojový soubor následujícím způsobem.

   1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na složku **Zdrojové soubory** , přejděte na **Přidat**a potom klepněte na příkaz Nová **položka**.

   1. V uzlu **Kód** klikněte na **Soubor C++ (.cpp),** zadejte název souboru a potom klikněte na **Přidat**.

   Soubor CPP se zobrazí ve složce **Zdrojové soubory** v **Průzkumníku řešení**a soubor se otevře v editoru sady Visual Studio.

1. Do souboru v editoru zadejte platný program jazyka C++, který používá standardní knihovnu jazyka C++, nebo zkopírujte jeden z ukázkových programů a vložte jej do souboru.

1. Uložte soubor.

1. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

   Okno **Výstup** zobrazuje informace o průběhu kompilace, například umístění protokolu sestavení a zprávu, která označuje stav sestavení.

1. V nabídce **Ladění** klepněte na tlačítko **Start bez ladění**.

   Pokud jste použili ukázkový program, zobrazí se příkazové okno a zobrazí se, zda jsou v sadě nalezena určitá celá čísla.

## <a name="next-steps"></a>Další kroky

**Předchozí:** [Konzolové aplikace v jazyce Visual C++](../windows/console-applications-in-visual-cpp.md)<br/>
**Další:** [Návod: Kompilace nativního programu Jazyka C++ na příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Viz také

[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
