---
title: 'Návod: Vytvoření programu ve standardním C++ (C++)'
ms.custom: get-started-article
ms.date: 09/18/2018
f1_keywords:
- vcfirstapp
- vccreatefirst
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: d58d23e757a97402985ef60badf551523c0a275e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387796"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Návod: Vytvoření programu ve standardním C++ (C++)

Visual C++ v sadě Visual Studio integrované vývojové prostředí (IDE) slouží k vytvoření standardního programu C++. Pomocí následujících kroků v tomto podrobném návodu, můžete vytvořit projekt, přidejte do projektu nový soubor, upravte soubor tak přidáním kódu jazyka C++ a potom zkompilujete a spustíte program pomocí sady Visual Studio.

Můžete zadat vlastní program C++, nebo použijte jednu z ukázkových programů. Ukázkový program v tomto návodu je konzolová aplikace. Tato aplikace používá `set` kontejneru ve standardní knihovně jazyka C++.

Následuje Visual C++ 2003 C++ Standard, s následujícími hlavními výjimkami: vyhledávání dvoufázová názvu, specifikace výjimek a export. Kromě toho Visual C++ podporuje několik funkcí C ++ 0 x, například: výrazy lambda, auto, static_assert, odkazy rvalue a externí šablony.

> [!NOTE]
> Pokud dodržování standardu je potřeba použít `/Za` – možnost kompilátoru zakázat rozšíření Microsoft pro standardní. Další informace najdete v tématu [/Za, /Ze (zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md).

## <a name="prerequisites"></a>Požadavky

Předpokladem práce s tímto návodem je znalost základů jazyka C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Vytvoření projektu a přidání zdrojového souboru

1. Vytvořte projekt tak, že označíte **nový** na **souboru** nabídky a pak levým na **projektu**.

1. V **Visual C++** podokně typů projektů, klikněte na tlačítko **Windows Desktop**a potom klikněte na tlačítko **Konzolová aplikace Windows**.

   > [!NOTE]
   > Pro verze starší než 2017, Visual Studio v **nový projekt** dialogového okna rozbalte **nainstalováno** > **šablony**  >  **Visual C++** a pak vyberte **Win32**. V prostředním podokně vyberte **Konzolová aplikace Win32**.

   Zadejte název projektu.

   Ve výchozím nastavení řešení, které obsahuje projekt má stejný název jako projekt, ale můžete zadat jiný název. Můžete také zadat jiné umístění pro projekt.

   Klikněte na tlačítko **OK** pro vytvoření projektu.

   > [!NOTE]
   > Verze sady Visual Studio starší než 2017, dokončete **Průvodce aplikací Win32**. Klikněte na tlačítko **Další**, zkontrolujte, zda **konzolovou aplikaci** je vybraná a zrušte zaškrtnutí políčka **předkompilované hlavičky** pole. Klikněte na tlačítko **Dokončit**.

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
