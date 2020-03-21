---
title: 'Návod: Vytvoření a použití statické knihovny (C++)'
description: Použijte C++ k vytvoření statické knihovny (. lib) v aplikaci Visual Studio.
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.author: corob
ms.openlocfilehash: c81ccd970383c8571a7d0d1e77d4b8fe44900bcf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078183"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>Návod: Vytvoření a použití statické knihovny (C++)

V tomto podrobném návodu se dozvíte, jak vytvořit statickou knihovnu (soubor. lib) pro použití s C++ aplikacemi. Použití statické knihovny je skvělým způsobem opakovaného použití kódu. Místo toho, aby byla stejná rutina znovu implementovaná v každé aplikaci, která vyžaduje funkci, je můžete ve statické knihovně napsat jednou a pak na ni odkazovat z aplikací. Kód propojený ze statické knihovny se stal součástí vaší aplikace – nemusíte instalovat jiný soubor pro použití kódu.

Tento názorný postup se zabývá následujícími úlohami:

- [Vytvoření projektu statické knihovny](#CreateLibProject)

- [Přidání třídy do statické knihovny](#AddClassToLib)

- [Vytvoření C++ konzolové aplikace, která odkazuje na statickou knihovnu](#CreateAppToRefTheLib)

- [Používání funkce ze statické knihovny v aplikaci](#UseLibInApp)

- [Spuštění aplikace](#RunApp)

## <a name="prerequisites"></a>Předpoklady

Porozumění základům C++ jazyka.

##  <a name="creating-a-static-library-project"></a><a name="CreateLibProject"></a>Vytvoření projektu statické knihovny

Pokyny k vytvoření projektu se liší v závislosti na tom, zda používáte Visual Studio 2019 nebo starší verzi. Ujistěte se, že máte v levém horním rohu této stránky správnou sadu verzí.

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Vytvoření projektu statické knihovny v aplikaci Visual Studio 2019

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt** . otevře se dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Library**.

1. Z filtrovaného seznamu typů projektů zvolte možnost **Statická knihovna** a pak zvolte možnost **Další**. Na další stránce zadejte do pole **název** *MathFuncsLib* a zadejte název projektu a v případě potřeby určete umístění projektu.

1. Pro vytvoření projektu klienta klikněte na tlačítko **vytvořit** .

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Vytvoření projektu statické knihovny v aplikaci Visual Studio 2017

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte položku **nainstalované** > **vizuál C++** a pak vyberte možnost **desktopová plocha systému Windows**. V prostředním podokně vyberte možnost **Průvodce desktopovou plochou systému Windows**.

1. Do pole **název** zadejte název projektu, například *MathFuncsLib*–. Do pole **název řešení** zadejte název řešení (například *StaticLibrary*). Klikněte na tlačítko **OK** .

1. V části **Typ aplikace**vyberte **Statická knihovna (. lib)** .

1. V části **Další možnosti**zrušte zaškrtávací políčko **Předkompilovaná hlavička** .

1. Kliknutím na **tlačítko OK** vytvořte projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Vytvoření projektu statické knihovny v aplikaci Visual Studio 2015

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt**.

1. V dialogovém okně **Nový projekt** rozbalte položku **nainstalované** > **šablony** > **vizuál C++** a pak vyberte **Win32**. V prostředním podokně vyberte **Konzolová aplikace Win32**.

1. Do pole **název** zadejte název projektu, například *MathFuncsLib*–. Do pole **název řešení** zadejte název řešení (například *StaticLibrary*). Klikněte na tlačítko **OK** .

1. Klikněte na **Další**.

1. V části **Typ aplikace**vyberte **Statická knihovna**. Pak zrušte výběr pole **Předkompilovaná hlavička** a zvolte **Dokončit**.

::: moniker-end

##  <a name="adding-a-class-to-the-static-library"></a><a name="AddClassToLib"></a>Přidání třídy do statické knihovny

### <a name="to-add-a-class-to-the-static-library"></a>Přidání třídy do statické knihovny

1. Chcete-li vytvořit soubor hlaviček pro novou třídu, otevřete místní nabídku projektu **MathFuncsLib** v aplikaci **Průzkumník řešení**a zvolte možnost **Přidat** > **novou položku**. V dialogovém okně **Přidat novou položku** v levém podokně v části **C++vizuál**vyberte **Code (kód**). V prostředním podokně vyberte **hlavičkový soubor (. h)** . Zadejte název hlavičkového souboru, například *MathFuncsLib. h*, a pak klikněte na tlačítko **Přidat** . Zobrazí se prázdný hlavičkový soubor.

1. Přidejte třídu s názvem `MyMathFuncs`, která provede běžné matematické operace, jako například sčítání, odčítání, násobení a dělení. Kód by měl vypadat přibližně takto:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

1. Chcete-li vytvořit zdrojový soubor pro novou třídu, otevřete místní nabídku pro projekt **MathFuncsLib** v **Průzkumník řešení**a zvolte možnost **Přidat** > **novou položku**. V dialogovém okně **Přidat novou položku** v levém podokně v části **C++vizuál**vyberte **Code (kód**). V prostředním podokně vyberte  **C++ soubor (. cpp)** . Zadejte název zdrojového souboru, například *MathFuncsLib. cpp*, a pak klikněte na tlačítko **Přidat** . Zobrazí se prázdný zdrojový soubor.

1. Tento zdrojový soubor použijte k implementaci funkcionality pro **MyMathFuncs**. Kód by měl vypadat přibližně takto:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

1. Zkompilujte statickou knihovnu výběrem možnosti **sestavit** > **Sestavit řešení** na řádku nabídek. Kompilace vytvoří statickou knihovnu, kterou mohou používat jiné programy.

   > [!NOTE]
   > Při sestavování na příkazovém řádku sady Visual Studio je nutné sestavit program ve dvou krocích. Nejprve spusťte `cl /c /EHsc MathFuncsLib.cpp` pro zkompilování kódu a vytvořte soubor objektu s názvem `MathFuncsLib.obj`. (`cl` příkaz vyvolá kompilátor, CL. exe a možnost `/c` určuje kompilaci bez propojení. Další informace naleznete v tématu [/c (kompilace bez propojení)](../build/reference/c-compile-without-linking.md).) Za druhé spusťte `lib MathFuncsLib.obj` k propojení kódu a vytvoření `MathFuncsLib.lib`statické knihovny. (`lib` příkaz vyvolá správce knihovny LIB. exe. Další informace naleznete v tématu [lib reference](../build/reference/lib-reference.md).)

##  <a name="creating-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a>Vytvoření C++ konzolové aplikace, která odkazuje na statickou knihovnu

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Vytvoření C++ konzolové aplikace, která odkazuje na statickou knihovnu v aplikaci Visual Studio 2019

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na nejvyšší uzel řešení a výběrem možnosti **Přidat** > **Nový projekt** otevřete dialogové okno **Přidat nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Console**.

1. Z filtrovaného seznamu typů projektů zvolte **Konzolová aplikace** a pak zvolte **Další**. Na další stránce zadejte do pole **název** *MyExecRefsLib* a zadejte název projektu a v případě potřeby určete umístění projektu.

1. Pro vytvoření projektu klienta klikněte na tlačítko **vytvořit** .

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Vytvoření C++ konzolové aplikace, která odkazuje na statickou knihovnu v aplikaci Visual Studio 2017

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte položku **nainstalované** > **vizuál C++** a pak vyberte možnost **desktopová plocha systému Windows**. V prostředním podokně vyberte možnost **Průvodce desktopovou plochou systému Windows**.

1. Do pole **název** zadejte název projektu, například *MyExecRefsLib*–. V rozevíracím seznamu vedle **řešení**vyberte možnost **Přidat do řešení**. Příkaz přidá nový projekt do řešení, které obsahuje statickou knihovnu. Klikněte na tlačítko **OK** .

1. V části **Typ aplikace**vyberte **Konzolová aplikace (. exe)** .

1. V části **Další možnosti**zrušte zaškrtávací políčko **Předkompilovaná hlavička** .

1. Kliknutím na **tlačítko OK** vytvořte projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Vytvoření C++ konzolové aplikace, která odkazuje na statickou knihovnu v aplikaci Visual Studio 2015

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt**.

1. V dialogovém okně **Nový projekt** rozbalte položku **nainstalované** > **šablony** > **vizuál C++** a pak vyberte **Win32**. V prostředním podokně vyberte **Konzolová aplikace Win32**.

1. Do pole **název** zadejte název projektu, například *MyExecRefsLib*–. V rozevíracím seznamu vedle **řešení**vyberte možnost **Přidat do řešení**. Příkaz přidá nový projekt do řešení, které obsahuje statickou knihovnu. Klikněte na tlačítko **OK** .

1. Klikněte na **Další**.

1. Ujistěte se, že je vybraná **Konzolová aplikace** . Potom zaškrtněte pole **prázdný projekt** a klikněte na tlačítko **Dokončit**.

::: moniker-end

##  <a name="using-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a>Používání funkce ze statické knihovny v aplikaci

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Použití funkce ze statické knihovny v aplikaci

1. Po vytvoření aplikace konzoly se vytvoří prázdný program za vás. Název zdrojového souboru je stejný jako název, který jste zvolili dříve. V tomto příkladu je název `MyExecRefsLib.cpp`.

1. Než budete moci použít matematické rutiny ve statické knihovně, je nutné na ni odkazovat. Otevřete místní nabídku projektu **MyExecRefsLib** v **Průzkumník řešení**a pak zvolte **Přidat** > **odkaz**.

1. Dialogové okno **Přidat odkaz** obsahuje seznam knihoven, které lze odkazovat. Karta **projekty** obsahuje seznam projektů v aktuálním řešení a všechny knihovny, na které odkazují. Na kartě **projekty** zaškrtněte políčko **MathFuncsLib** a poté klikněte na tlačítko **OK** .

1. Chcete-li odkazovat na soubor hlaviček `MathFuncsLib.h`, je nutné upravit cestu k zahrnutým adresářům. V dialogovém okně **stránky vlastností** pro **MyExecRefsLib**rozbalte uzel **Vlastnosti konfigurace** , rozbalte uzel **C++ C/** a pak vyberte **Obecné**. Vedle **Další adresáře zahrnutí**zadejte cestu k adresáři **MathFuncsLib** nebo ji vyhledejte.

   Chcete-li vyhledat cestu k adresáři, otevřete rozevírací seznam hodnota vlastnosti a pak zvolte možnost **Upravit**. V dialogovém okně **Další adresáře k zahrnutí** zadejte do textového pole prázdný řádek a potom zvolte tlačítko se třemi tečkami ( **...** ) na konci řádku. V dialogovém okně **Vybrat adresář** vyberte adresář **MathFuncsLib** a pak zvolte tlačítko **Vybrat složku** pro uložení výběru a zavření dialogového okna. V dialogovém okně **Další vložené adresáře** klikněte na tlačítko **OK** a potom v dialogovém okně **stránky vlastností** klikněte na tlačítko **OK** , čímž uložíte změny projektu.

1. V této aplikaci teď můžete použít třídu `MyMathFuncs` zahrnutím hlavičky `#include "MathFuncsLib.h"` do kódu. Nahraďte obsah `MyExecRefsLib.cpp` tímto kódem:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

1. Sestavte spustitelný soubor tak, že na řádku nabídek kliknete na **sestavit** > **Sestavit řešení** .

##  <a name="running-the-app"></a><a name="RunApp"></a>Spuštění aplikace

### <a name="to-run-the-app"></a>Spuštění aplikace

1. Otevřete místní nabídku pro **MyExecRefsLib** v **Průzkumník řešení**a zvolte možnost **nastavit jako spouštěný projekt**, ujistěte se, že je vybrána možnost **MyExecRefsLib** jako výchozí projekt.

1. Chcete-li spustit projekt, na panelu nabídek vyberte možnost **ladit** > **Spustit bez ladění**. Výstup by měl vypadat přibližně takto:

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Viz také

[Návod: Vytvoření a použití dynamické knihovny DLL (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Desktopové aplikace (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
