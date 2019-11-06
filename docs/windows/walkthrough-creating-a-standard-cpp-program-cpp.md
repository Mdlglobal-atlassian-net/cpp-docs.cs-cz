---
title: 'Návod: vytvoření standardního C++ programu ()C++'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 9b2d1f3bf1a229a0590553369e37bc07f35ada33
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627132"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Návod: vytvoření standardního C++ programu ()C++

Pomocí sady Visual Studio můžete vytvářet standardní C++ programy. Podle kroků v tomto návodu můžete vytvořit projekt, přidat do projektu nový soubor, upravit soubor a přidat C++ kód a potom zkompilovat a spustit program pomocí sady Visual Studio.

Můžete zadat vlastní C++ program nebo použít některý z ukázkových programů. Vzorový program v tomto návodu je Konzolová aplikace. Tato aplikace používá kontejner `set` ve C++ standardní knihovně.

> [!NOTE]
> Pokud je vyžadováno dodržování určité verze C++ jazykového standardu (tj. c++ 14 nebo c++ 17), použijte možnost kompilátoru `/std:c++14` nebo `/std:c++17`. (Visual Studio 2017 a novější)

## <a name="prerequisites"></a>Požadavky

Předpokladem práce s tímto návodem je znalost základů jazyka C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Vytvoření projektu a přidání zdrojového souboru

Následující postup se liší v závislosti na verzi sady Visual Studio, kterou používáte. Ujistěte se, že selektor verzí v levém horním rohu této stránky je nastaven správně.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Vytvoření C++ projektu v aplikaci Visual Studio 2019

1. V hlavní nabídce vyberte možnost **soubor** > **Nový** > **projekt** . otevře se dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Console**. 

1. Z filtrovaného seznamu typů projektů zvolte **Konzolová aplikace** a pak zvolte **Další**. Na další stránce zadejte název projektu a v případě potřeby zadejte umístění projektu.

1. Kliknutím na tlačítko **vytvořit** vytvořte projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Vytvoření C++ projektu v aplikaci Visual Studio 2017

1. Vytvořte projekt ukázáním na **Nový** v nabídce **soubor** a potom kliknutím na **projekt**.

1. V podokně typy projektů **vizuálů C++**  klikněte na možnost **plocha systému Windows**a poté klikněte na možnost **Konzolová aplikace systému Windows**.

1. Zadejte název projektu. Ve výchozím nastavení má řešení, které obsahuje projekt, stejný název jako projekt, ale můžete zadat jiný název. Můžete také zadat jiné umístění projektu.

1. Kliknutím na tlačítko **OK** vytvořte projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Vytvoření C++ projektu v aplikaci Visual Studio 2015

1. Vytvořte projekt ukázáním na **Nový** v nabídce **soubor** a potom kliknutím na **projekt**.

1. V podokně typy projektů **vizuálů C++**  klikněte na možnost **plocha systému Windows**a poté klikněte na možnost **Konzolová aplikace systému Windows**.

1. V dialogovém okně **Nový projekt** rozbalte položku **nainstalované** > **šablony** > **vizuál C++** a pak vyberte **Win32**. V prostředním podokně vyberte **Konzolová aplikace Win32**.

1. Zadejte název projektu. Ve výchozím nastavení má řešení, které obsahuje projekt, stejný název jako projekt, ale můžete zadat jiný název. Můžete také zadat jiné umístění projektu.

1. Kliknutím na tlačítko **OK** vytvořte projekt.

1. Dokončete **Průvodce aplikací Win32**. 

1. Klikněte na **Další**, pak se ujistěte, že je vybraná **aplikace konzoly** , a zrušte zaškrtnutí políčka **Předkompilovaná záhlaví** . 

1. Klikněte na tlačítko **Dokončit**.

::: moniker-end

## <a name="add-a-new-source-file"></a>Přidat nový zdrojový soubor

1. Pokud se **Průzkumník řešení** nezobrazí, klikněte v nabídce **zobrazení** na položku **Průzkumník řešení**.

1. Následujícím způsobem přidejte do projektu nový zdrojový soubor.

   1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku **zdrojové soubory** , přejděte na **Přidat**a klikněte na **Nová položka**.

   1. V uzlu **kód** klikněte na  **C++ soubor (. cpp)** , zadejte název souboru a potom klikněte na **Přidat**.

   Soubor. cpp se zobrazí ve složce **zdrojové soubory** v **Průzkumník řešení**a soubor je otevřen v editoru sady Visual Studio.

1. V souboru v editoru zadejte platný C++ program, který používá C++ standardní knihovnu, nebo zkopírujte jeden z ukázkových programů a vložte jej do souboru.

1. Uložte soubor.

1. V nabídce **sestavení** klikněte na **Sestavit řešení**.

   V okně **výstup** se zobrazí informace o průběhu kompilace, například umístění protokolu sestavení a zpráva, která označuje stav sestavení.

1. V nabídce **ladit** klikněte na **Spustit bez ladění**.

   Pokud jste použili vzorový program, zobrazí se okno příkazového řádku, ve kterém se zobrazí, zda jsou v sadě nalezena určitá celá čísla.

## <a name="next-steps"></a>Další kroky

**Předchozí:** [konzolové aplikace v C++ jazyce Visual](../windows/console-applications-in-visual-cpp.md)<br/>
**Další:** [Návod: kompilování nativního C++ programu na příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
