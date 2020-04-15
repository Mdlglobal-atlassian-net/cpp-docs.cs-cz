---
title: 'Návod: Vytvoření a použití statické knihovny (C++)'
description: Pomocí jazyka C++ vytvořte statickou knihovnu (.lib) v sadě Visual Studio.
ms.custom: get-started-article
ms.date: 04/13/2020
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.openlocfilehash: 7148cc1de7c06ae57d61560311b342a1fc9dda1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335141"
---
# <a name="walkthrough-create-and-use-a-static-library"></a>Návod: Vytvoření a použití statické knihovny

Tento podrobný návod ukazuje, jak vytvořit statickou knihovnu (soubor lib) pro použití s aplikacemi c++. Použití statické knihovny je skvělý způsob, jak znovu použít kód. Místo opětovného implementace stejné rutiny v každé aplikaci, která vyžaduje funkce, napište je jednou ve statické knihovně a potom odkazovat z aplikací. Kód propojený ze statické knihovny se stane součástí vaší aplikace – nemusíte instalovat jiný soubor, abyste mohli kód používat.

Tento návod zahrnuje tyto úkoly:

- [Vytvoření projektu statické knihovny](#CreateLibProject)

- [Přidání třídy do statické knihovny](#AddClassToLib)

- [Vytvoření konzolové aplikace Jazyka C++, která odkazuje na statickou knihovnu](#CreateAppToRefTheLib)

- [Použití funkcí ze statické knihovny v aplikaci](#UseLibInApp)

- [Spuštění aplikace](#RunApp)

## <a name="prerequisites"></a>Požadavky

Pochopení základů jazyka C++.

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a>Vytvoření projektu statické knihovny

Pokyny pro vytvoření projektu se liší v závislosti na verzi sady Visual Studio. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Vytvoření projektu statické knihovny v sadě Visual Studio 2019

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno Vytvořit **nový projekt.**

1. V horní části dialogového okna nastavte **jazyk** na **C++**, nastavte **platformu** na **Windows**a typ **projektu** na **Knihovnu**.

1. Ve filtrovaném seznamu typů projektů vyberte **Průvodce plochu systému Windows**a pak zvolte **Další**.

1. Na stránce **Konfigurace nového projektu** zadejte Do pole Název projektu *Knihovnu* **Matematika** a zadejte název projektu. Do pole **Název řešení** zadejte *StaticMath.* Zvolte tlačítko **Vytvořit,** chcete-li otevřít dialogové okno **Projekt plochy systému Windows.**

1. V dialogovém okně **Projekt plochy systému Windows** vyberte v části Typ **aplikace** **položku Statická knihovna (.lib).**

1. V části **Další možnosti**zaškrtněte **políčko Předkompilované záhlaví,** pokud je zaškrtnuto. Zaškrtněte políčko **Prázdný projekt.**

1. Chcete-li vytvořit projekt, zvolte **OK.**

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Vytvoření projektu statické knihovny v sadě Visual Studio 2017

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

1. V dialogovém okně **Nový projekt** vyberte **Nainstalovaný** > **Visual C++** > **Windows Desktop**. V prostředním podokně vyberte **Průvodce plochu systému Windows**.

1. Zadejte název projektu – například *MathLibrary*– do pole **Název.** Zadejte název řešení – například *StaticMath*– do pole **Název řešení.** Zvolte tlačítko **OK.**

1. V dialogovém okně **Projekt plochy systému Windows** vyberte v části Typ **aplikace** **položku Statická knihovna (.lib).**

1. V části **Další možnosti**zaškrtněte **políčko Předkompilované záhlaví,** pokud je zaškrtnuto. Zaškrtněte políčko **Prázdný projekt.**

1. Chcete-li vytvořit projekt, zvolte **OK.**

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Vytvoření projektu statické knihovny v sadě Visual Studio 2015

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

1. V dialogovém okně **Nový projekt** vyberte **Nainstalované** > **šablony** > **Visual C++** > **Win32**. V prostředním podokně vyberte **možnost Win32 Console Application**.

1. Zadejte název projektu – například *MathLibrary*– do pole **Název.** Zadejte název řešení – například *StaticMath*– do pole **Název řešení.** Zvolte tlačítko **OK.**

1. V **Průvodci aplikací win32**zvolte **Další**.

1. Na stránce **Nastavení aplikace** vyberte v části **Typ aplikace** **možnost Statická knihovna**. V části **Další možnosti**zaškrtněte **políčko Předkompilované záhlaví.** Chcete-li vytvořit projekt, zvolte **Dokončit.**

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a>Přidání třídy do statické knihovny

### <a name="to-add-a-class-to-the-static-library"></a>Přidání třídy do statické knihovny

1. Chcete-li vytvořit soubor záhlaví pro novou třídu, klepnutím pravým tlačítkem myši otevřete místní nabídku pro projekt **MathLibrary** v **Průzkumníku řešení**a pak zvolte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **Visual C++** > **Code**. V prostředním podokně vyberte **Soubor záhlaví (.h)**. Zadejte název souboru záhlaví – například *MathLibrary.h*– a pak zvolte tlačítko **Přidat.** Zobrazí se téměř prázdný soubor záhlaví.

1. Přidejte deklaraci třídy s názvem `Arithmetic` k běžným matematickým operacím, jako je sčítání, odčítání, násobení a dělení. Kód by se měl podobat:

    ```cpp
    // MathLibrary.h
    #pragma once

    namespace MathLibrary
    {
        class Arithmetic
        {
        public:
            // Returns a + b
            static double Add(double a, double b);

            // Returns a - b
            static double Subtract(double a, double b);

            // Returns a * b
            static double Multiply(double a, double b);

            // Returns a / b
            static double Divide(double a, double b);
        };
    }
    ```

1. Chcete-li vytvořit zdrojový soubor pro novou třídu, otevřete místní nabídku projektu **MathLibrary** v **Průzkumníku řešení**a pak zvolte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte v prostředním podokně **soubor C++ (.cpp).** Zadejte název zdrojového souboru – například *MathLibrary.cpp*– a pak zvolte tlačítko **Přidat.** Zobrazí se prázdný zdrojový soubor.

1. Tento zdrojový soubor slouží k implementaci `Arithmetic`funkce pro třídu . Kód by se měl podobat:

    ```cpp
    // MathLibrary.cpp
    // compile with: cl /c /EHsc MathLibrary.cpp
    // post-build command: lib MathLibrary.obj

    #include "MathLibrary.h"

    namespace MathLibrary
    {
        double Arithmetic::Add(double a, double b)
        {
            return a + b;
        }

        double Arithmetic::Subtract(double a, double b)
        {
            return a - b;
        }

        double Arithmetic::Multiply(double a, double b)
        {
            return a * b;
        }

        double Arithmetic::Divide(double a, double b)
        {
            return a / b;
        }
    }
    ```

1. Chcete-li vytvořit statickou knihovnu, vyberte na řádku nabídek vyberte **Sestavit** > **řešení sestavení.** Sestavení vytvoří statickou knihovnu *MathLibrary.lib*, kterou mohou používat jiné programy.

   > [!NOTE]
   > Při sestavení na příkazovém řádku sady Visual Studio je nutné vytvořit program ve dvou krocích. Nejprve `cl /c /EHsc MathLibrary.cpp` spusťte kompilaci kódu a vytvořte soubor objektu s názvem *MathLibrary.obj*. (Příkaz `cl` vyvolá kompilátor Cl.exe a `/c` možnost určuje kompilaci bez propojení. Další informace naleznete v tématu [/c (Kompilace bez propojení)](../build/reference/c-compile-without-linking.md).) Za druhé, spusťte `lib MathLibrary.obj` propojit kód a vytvořit statickou knihovnu *MathLibrary.lib*. (Příkaz `lib` vyvolá správce knihovny Lib.exe. Další informace naleznete v tématu [LIB Reference](../build/reference/lib-reference.md).)

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a>Vytvoření konzolové aplikace Jazyka C++, která odkazuje na statickou knihovnu

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Vytvoření konzolové aplikace Pro C++, která odkazuje na statickou knihovnu ve Visual Studiu 2019

1. V **Průzkumníku řešení**otevřete místní nabídku klepnutím pravým tlačítkem myši na horní uzel **Řešení StaticMath.** Zvolte **Přidat** > **nový projekt,** **chcete-li** otevřít dialogové okno Přidat nový projekt.

1. V horní části dialogového okna nastavte filtr **Typ projektu** na **Console**.

1. Z filtrovaného seznamu typů projektů zvolte **Konzolová aplikace** a pak zvolte **Další**. Na další stránce zadejte *MathClient* do pole **Název** a zadejte název projektu.

1. Zvolte tlačítko **Vytvořit** pro vytvoření klientského projektu.

1. Po vytvoření konzolové aplikace se pro vás vytvoří prázdný program. Název zdrojového souboru je stejný jako název, který jste zvolili dříve. V příkladu je pojmenována `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Vytvoření konzolové aplikace Pro C++, která odkazuje na statickou knihovnu ve Visual Studiu 2017

1. V **Průzkumníku řešení**otevřete místní nabídku klepnutím pravým tlačítkem myši na horní uzel **Řešení StaticMath.** Zvolte **Přidat** > **nový projekt,** **chcete-li** otevřít dialogové okno Přidat nový projekt.

1. V dialogovém okně **Přidat nový projekt** vyberte **Nainstalovaný** > **Visual C++** > **Windows Desktop**. V prostředním podokně vyberte **Průvodce plochu systému Windows**.

1. Zadejte název projektu – například *MathClient*– do pole **Název.** Zvolte tlačítko **OK.**

1. V dialogovém okně **Projekt plochy systému Windows** vyberte v části Typ **aplikace** **položku Konzolová aplikace (.exe).**

1. V části **Další možnosti**zaškrtněte **políčko Předkompilované záhlaví,** pokud je zaškrtnuto.

1. Chcete-li vytvořit projekt, zvolte **OK.**

1. Po vytvoření konzolové aplikace se pro vás vytvoří prázdný program. Název zdrojového souboru je stejný jako název, který jste zvolili dříve. V příkladu je pojmenována `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Vytvoření konzolové aplikace Pro C++, která odkazuje na statickou knihovnu ve Visual Studiu 2015

1. V **Průzkumníku řešení**otevřete místní nabídku klepnutím pravým tlačítkem myši na horní uzel **Řešení StaticMath.** Zvolte **Přidat** > **nový projekt,** **chcete-li** otevřít dialogové okno Přidat nový projekt.

1. V dialogovém okně **Přidat nový projekt** vyberte **Nainstalovaný** > **Visual C++** > **Win32**. V prostředním podokně vyberte **možnost Win32 Console Application**.

1. Zadejte název projektu – například *MathClient*– do pole **Název.** Zvolte tlačítko **OK.**

1. V dialogovém okně **Průvodce aplikací win32** zvolte **Další**.

1. Na stránce **Nastavení aplikace** v části **Typ aplikace**zkontrolujte, zda je vybraná **aplikace Konzola.** V části **Další možnosti**odškrtnete **políčko Předkompilované záhlaví**a zaškrtněte políčko **Prázdný projekt.** Chcete-li vytvořit projekt, zvolte **Dokončit.**

1. Chcete-li přidat zdrojový soubor do prázdného projektu, klepnutím pravým tlačítkem myši otevřete místní nabídku projektu **MathClient** v **Průzkumníku řešení**a pak zvolte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **Visual C++** > **Code**. V prostředním podokně vyberte **soubor C++ (.cpp)**. Zadejte název zdrojového souboru – například *MathClient.cpp*– a pak zvolte tlačítko **Přidat.** Zobrazí se prázdný zdrojový soubor.

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a>Použití funkcí ze statické knihovny v aplikaci

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Použití funkcí ze statické knihovny v aplikaci

1. Před použitím matematické rutiny ve statické knihovně, musíte odkazovat. Otevřete místní nabídku projektu **MathClient** v **Průzkumníku řešení**a pak zvolte **Přidat** > **odkaz**.

1. V dialogovém okně **Přidat odkaz** jsou uvedeny knihovny, na které můžete odkazovat. Na kartě **Projekty** jsou uvedeny projekty v aktuálním řešení a všechny knihovny, na které odkazují. Otevřete kartu **Projekty,** zaškrtněte políčko **MathLibrary** a pak zvolte tlačítko **OK.**

1. Chcete-li `MathLibrary.h` odkazovat na soubor záhlaví, musíte upravit zahrnutou cestu k adresářům. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na **položku MathClient** a otevřete místní nabídku. Zvolte **Vlastnosti,** chcete-li otevřít dialogové okno **MathClient Property Pages.**

1. V dialogovém okně **Stránky vlastností MathClient** nastavte rozevírací **seznam Konfigurace** na Všechny **konfigurace**. Nastavte rozbalovací **soubor Platformy** na **Všechny platformy**.

1. Vyberte stránku **vlastností Vlastnosti** > **C/C++** > **obecné** konfigurace. Ve vlastnosti **Další zahrnutí adresářů** zadejte cestu k **adresáři MathLibrary** nebo ji vyhledejte.

   Chcete-li vyhledat cestu k adresáři:

   1. Otevřete rozevírací seznam Hodnota **vlastnosti Další zahrnutí adresářů** a pak zvolte **Upravit**.

   1. V dialogovém okně **Další zahrnutí adresářů** poklepejte v horní části textového pole. Pak zvolte tlačítko tři tečky (**...**) na konci řádku.

   1. V dialogovém okně **Vybrat adresář** přejděte o úroveň výš a vyberte adresář **MathLibrary.** Pak zvolte tlačítko **Vybrat složku,** chcete-li výběr uložit.

   1. V dialogovém okně **Další zahrnutí adresářů** zvolte tlačítko **OK.**

   1. V dialogovém okně **Stránky vlastností** zvolte tlačítko **OK** pro uložení změn do projektu.

1. Nyní můžete třídu `Arithmetic` v této aplikaci použít zahrnutím `#include "MathLibrary.h"` záhlaví do kódu. Nahraďte `MathClient.cpp` obsah tohoto kódu:

    ```cpp
    // MathClient.cpp
    // compile with: cl /EHsc MathClient.cpp /link MathLibrary.lib

    #include <iostream>
    #include "MathLibrary.h"

    int main()
    {
        double a = 7.4;
        int b = 99;

        std::cout << "a + b = " <<
            MathLibrary::Arithmetic::Add(a, b) << std::endl;
        std::cout << "a - b = " <<
            MathLibrary::Arithmetic::Subtract(a, b) << std::endl;
        std::cout << "a * b = " <<
            MathLibrary::Arithmetic::Multiply(a, b) << std::endl;
        std::cout << "a / b = " <<
            MathLibrary::Arithmetic::Divide(a, b) << std::endl;

        return 0;
    }
    ```

1. Chcete-li vytvořit spustitelný soubor, zvolte **sestavení** > **sestavení řešení** na řádku nabídek.

## <a name="run-the-app"></a><a name="RunApp"></a>Spuštění aplikace

### <a name="to-run-the-app"></a>Spuštění aplikace

1. Ujistěte se, že **MathClient** je vybrán jako výchozí projekt. Chcete-li ji vybrat, klepnutím pravým tlačítkem myši otevřete místní nabídku **pro MathClient** v **Průzkumníku řešení**a pak zvolte **Nastavit jako počáteční projekt**.

1. Chcete-li projekt spustit, zvolte na řádku nabídek možnost **Ladění** > **startu bez ladění**. Výstup by se měl podobat:

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Viz také

[Návod: Vytvoření a použití dynamické knihovny DLL (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Desktopové aplikace (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
