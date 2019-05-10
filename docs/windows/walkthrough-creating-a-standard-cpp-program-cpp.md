---
title: 'Návod: Vytvoření programu ve standardním C++ (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: ed9c19dad029f8fc9495d38ab6e5c0ba8ad6d529
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877420"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Návod: Vytvoření programu ve standardním C++ (C++)

Visual Studio můžete použít k vytvoření standardní C++ programy. Pomocí následujících kroků v tomto podrobném návodu, můžete vytvořit projekt, přidejte do projektu nový soubor, upravte soubor tak přidáním kódu jazyka C++ a potom zkompilujete a spustíte program pomocí sady Visual Studio.

Můžete zadat vlastní program C++, nebo použijte jednu z ukázkových programů. Ukázkový program v tomto návodu je konzolová aplikace. Tato aplikace používá `set` kontejneru ve standardní knihovně jazyka C++.

> [!NOTE]
> Pokud dodržování předpisů s konkrétní verzí C++ standard jazyka (například C ++ 14 a C ++ 17) je povinný, použijte `/std:C++14` nebo `/std:c++17` – možnost kompilátoru. (Visual Studio 2017 nebo novější.)

## <a name="prerequisites"></a>Požadavky

Předpokladem práce s tímto návodem je znalost základů jazyka C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Vytvoření projektu a přidání zdrojového souboru

Následující postup se liší v závislosti na tom, kterou verzi sady Visual Studio, kterou používáte. Ujistěte se, že se že volič verze v levé horní části této stránky jsou správně nastavena.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Chcete-li vytvořit C++ projektu v aplikaci Visual Studio 2019

1. V hlavní nabídce zvolte **souboru** > **nový** > **projektu** otevřít **vytvořte nový projekt** dialogového okna pole.

1. V horní části dialogového okna, nastavte **jazyk** k **C++**, nastavte **platformy** k **Windows**a nastavte **typprojektu** k **konzoly**. 

1. Filtrované seznamu typů projektů zvolte **konzolovou aplikaci** klikněte na tlačítko **Další**. Na další stránce zadejte název projektu a zadejte umístění projektu, v případě potřeby.

1. Zvolte **vytvořit** tlačítko pro vytvoření projektu.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Chcete-li vytvořit C++ projektu v sadě Visual Studio 2017

1. Vytvořte projekt tak, že označíte **nový** na **souboru** nabídky a pak levým na **projektu**.

1. V **Visual C++** podokně typů projektů, klikněte na tlačítko **Windows Desktop**a potom klikněte na tlačítko **Konzolová aplikace Windows**.

1. Zadejte název projektu. Ve výchozím nastavení řešení, které obsahuje projekt má stejný název jako projekt, ale můžete zadat jiný název. Můžete také zadat jiné umístění pro projekt.

1. Klikněte na tlačítko **OK** pro vytvoření projektu.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Chcete-li vytvořit C++ projektu v sadě Visual Studio 2015

1. Vytvořte projekt tak, že označíte **nový** na **souboru** nabídky a pak levým na **projektu**.

1. V **Visual C++** podokně typů projektů, klikněte na tlačítko **Windows Desktop**a potom klikněte na tlačítko **Konzolová aplikace Windows**.

1. V **nový projekt** dialogového okna rozbalte **nainstalováno** > **šablony** > **Visual C++** , a potom vyberte **Win32**. V prostředním podokně vyberte **Konzolová aplikace Win32**.

1. Zadejte název projektu. Ve výchozím nastavení řešení, které obsahuje projekt má stejný název jako projekt, ale můžete zadat jiný název. Můžete také zadat jiné umístění pro projekt.

1. Klikněte na tlačítko **OK** pro vytvoření projektu.

1. Dokončení **Průvodce aplikací Win32**. 

1. Klikněte na tlačítko **Další**, zkontrolujte, zda **konzolovou aplikaci** je vybraná a zrušte zaškrtnutí políčka **předkompilované hlavičky** pole. 

1. Klikněte na tlačítko **Dokončit**.

::: moniker-end

## <a name="add-a-new-source-file"></a>Přidání nového zdrojového souboru

1. Pokud **Průzkumníka řešení** se nezobrazuje na **zobrazení** nabídky, klikněte na tlačítko **Průzkumníka řešení**.

1. Přidání nového zdrojového souboru do projektu, následujícím způsobem.

   1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **zdrojové soubory** složku, přejděte na příkaz **přidat**a potom klikněte na tlačítko **nová položka**.

   1. V **kód** uzel, klikněte na tlačítko **soubor C++ (.cpp)**, zadejte název souboru a pak klikněte na tlačítko **přidat**.

   Soubor .cpp se zobrazí v **zdrojové soubory** složky **Průzkumníka řešení**, a soubor je otevřen v editoru sady Visual Studio.

1. V souboru v editoru zadejte platný program C++ používající standardní knihovny C++, nebo zkopírujte jeden z ukázkových programů a vložte ho do souboru.

1. Uložte soubor.

1. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

   **Výstup** okně zobrazí informace o průběhu kompilace, například umístění protokolu sestavení a napište zprávu, která označuje stav sestavení.

1. Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.

   Pokud jste použili ukázkový program, zobrazí se okno příkazového řádku a ukazuje, zda jsou určitá celá čísla nalezena v množině.

## <a name="next-steps"></a>Další kroky

**Předchozí:** [Konzolové aplikace v jazyku Visual C++](../windows/console-applications-in-visual-cpp.md)<br/>
**Další:** [Návod: Kompilace nativního programu C++ na příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)<br/>
