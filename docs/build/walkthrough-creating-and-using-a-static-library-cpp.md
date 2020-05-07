---
title: 'Návod: vytvoření a použití statické knihovny (C++)'
description: Použijte jazyk C++ k vytvoření statické knihovny (. lib) v aplikaci Visual Studio.
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
# <a name="walkthrough-create-and-use-a-static-library"></a>Návod: vytvoření a použití statické knihovny

V tomto podrobném návodu se dozvíte, jak vytvořit statickou knihovnu (soubor. lib) pro použití s aplikacemi C++. Použití statické knihovny je skvělým způsobem opakovaného použití kódu. Místo toho, aby byla stejná rutina znovu implementovaná v každé aplikaci, která vyžaduje funkci, je můžete ve statické knihovně napsat jednou a pak na ni odkazovat z aplikací. Kód propojený ze statické knihovny se stal součástí vaší aplikace – nemusíte instalovat jiný soubor pro použití kódu.

Tento názorný postup se zabývá následujícími úlohami:

- [Vytvoření projektu statické knihovny](#CreateLibProject)

- [Přidat třídu do statické knihovny](#AddClassToLib)

- [Vytvoření konzolové aplikace C++, která odkazuje na statickou knihovnu](#CreateAppToRefTheLib)

- [Použití funkce ze statické knihovny v aplikaci](#UseLibInApp)

- [Spuštění aplikace](#RunApp)

## <a name="prerequisites"></a>Požadavky

Porozumění základům jazyka C++.

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a>Vytvoření projektu statické knihovny

Pokyny k vytvoření projektu se liší v závislosti na vaší verzi sady Visual Studio. Chcete-li zobrazit dokumentaci k preferované verzi sady Visual Studio, použijte ovládací prvek selektor **verzí** . Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Vytvoření projektu statické knihovny v aplikaci Visual Studio 2019

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt** a otevřete tak dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++**, nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Library**.

1. Z filtrovaného seznamu typů projektů vyberte možnost **Průvodce desktopovou plochou systému Windows**a pak zvolte možnost **Další**.

1. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** *MathLibrary* a zadejte název projektu. Do pole **název řešení** zadejte *StaticMath* . Kliknutím na tlačítko **vytvořit** otevřete okno **projekt aplikace Windows** .

1. V dialogovém okně **Windows desktopový projekt** , v části **Typ aplikace**vyberte **Statická knihovna (. lib)**.

1. V části **Další možnosti**zrušte zaškrtnutí políčka **Předkompilovaná hlavička** , pokud je zaškrtnuto. Zaškrtněte pole **prázdný projekt** .

1. Kliknutím na **tlačítko OK** vytvořte projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Vytvoření projektu statické knihovny v aplikaci Visual Studio 2017

1. Na panelu nabídek vyberte **soubor** > **Nový** > **projekt**.

1. V dialogovém okně **Nový projekt** vyberte možnost **nainstalováno** > **Visual C++** > **plocha systému Windows**. V prostředním podokně vyberte možnost **Průvodce desktopovou plochou systému Windows**.

1. Do pole **název** zadejte název projektu, například *MathLibrary*–. Do pole **název řešení** zadejte název řešení (například *StaticMath*). Klikněte na tlačítko **OK** .

1. V dialogovém okně **Windows desktopový projekt** , v části **Typ aplikace**vyberte **Statická knihovna (. lib)**.

1. V části **Další možnosti**zrušte zaškrtnutí políčka **Předkompilovaná hlavička** , pokud je zaškrtnuto. Zaškrtněte pole **prázdný projekt** .

1. Kliknutím na **tlačítko OK** vytvořte projekt.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Vytvoření projektu statické knihovny v aplikaci Visual Studio 2015

1. Na panelu nabídek vyberte **soubor** > **Nový** > **projekt**.

1. V dialogovém **okně Nový projekt** vyberte možnost **nainstalované** > **šablony** > **Visual C++** > **Win32**. V prostředním podokně vyberte **Konzolová aplikace Win32**.

1. Do pole **název** zadejte název projektu, například *MathLibrary*–. Do pole **název řešení** zadejte název řešení (například *StaticMath*). Klikněte na tlačítko **OK** .

1. V **Průvodci aplikací Win32**klikněte na tlačítko **Další**.

1. Na stránce **nastavení aplikace** klikněte v části **Typ aplikace**na položku **Statická knihovna**. V části **Další možnosti**zrušte zaškrtnutí políčka **Předkompilovaná hlavička** . Kliknutím na tlačítko **Dokončit** vytvořte projekt.

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a>Přidat třídu do statické knihovny

### <a name="to-add-a-class-to-the-static-library"></a>Přidání třídy do statické knihovny

1. Chcete-li vytvořit soubor hlaviček pro novou třídu, klikněte pravým tlačítkem myši a otevřete místní nabídku pro projekt **MathLibrary** v **Průzkumník řešení**a pak zvolte možnost **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **Visual C++** > **kód**. V prostředním podokně vyberte **hlavičkový soubor (. h)**. Zadejte název hlavičkového souboru, například *MathLibrary. h*, a pak klikněte na tlačítko **Přidat** . Zobrazí se skoro prázdný hlavičkový soubor.

1. Přidejte deklaraci pro třídu s názvem `Arithmetic` k provádění běžných matematických operací, jako je sčítání, odčítání, násobení a dělení. Kód by měl vypadat přibližně takto:

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

1. Chcete-li vytvořit zdrojový soubor pro novou třídu, otevřete místní nabídku pro projekt **MathLibrary** v **Průzkumník řešení**a pak zvolte možnost **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** v prostředním podokně vyberte **soubor C++ (. cpp)**. Zadejte název zdrojového souboru, například *MathLibrary. cpp*, a pak klikněte na tlačítko **Přidat** . Zobrazí se prázdný zdrojový soubor.

1. Tento zdrojový soubor použijte k implementaci funkcionality třídy `Arithmetic`. Kód by měl vypadat přibližně takto:

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

1. Chcete-li vytvořit statickou knihovnu, vyberte v řádku nabídek možnost **sestavit** > **sestavení řešení** . Sestavení vytvoří statickou knihovnu *MathLibrary. lib*, kterou mohou používat jiné programy.

   > [!NOTE]
   > Při sestavování na příkazovém řádku sady Visual Studio je nutné sestavit program ve dvou krocích. Nejprve spusťte `cl /c /EHsc MathLibrary.cpp` příkaz pro zkompilování kódu a vytvořte soubor objektu s názvem *MathLibrary. obj*. ( `cl` Příkaz vyvolá kompilátor, CL. exe a možnost určuje, že se `/c` má kompilovat bez propojení. Další informace naleznete v tématu [/c (kompilace bez propojení)](../build/reference/c-compile-without-linking.md).) Za druhé spusťte `lib MathLibrary.obj` propojení kódu a vytvořte statickou knihovnu *MathLibrary. lib*. ( `lib` Příkaz vyvolá správce knihovny LIB. exe. Další informace naleznete v tématu [lib reference](../build/reference/lib-reference.md).)

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a>Vytvoření konzolové aplikace C++, která odkazuje na statickou knihovnu

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Vytvoření konzolové aplikace C++, která odkazuje na statickou knihovnu v aplikaci Visual Studio 2019

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na nejvyšší uzel, **řešení ' StaticMath '** a otevřete místní nabídku. Chcete-li otevřít dialogové okno **Přidat nový projekt** , vyberte možnost **Přidat** > **Nový projekt** .

1. V horní části dialogového okna nastavte filtr **typu projektu** na **Console**.

1. Z filtrovaného seznamu typů projektů zvolte **Konzolová aplikace** a pak zvolte **Další**. Na další stránce zadejte do pole **název** *MathClient* a zadejte název projektu.

1. Pro vytvoření projektu klienta klikněte na tlačítko **vytvořit** .

1. Po vytvoření aplikace konzoly se vytvoří prázdný program za vás. Název zdrojového souboru je stejný jako název, který jste zvolili dříve. V tomto příkladu je název `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Vytvoření konzolové aplikace C++, která odkazuje na statickou knihovnu v aplikaci Visual Studio 2017

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na nejvyšší uzel, **řešení ' StaticMath '** a otevřete místní nabídku. Chcete-li otevřít dialogové okno **Přidat nový projekt** , vyberte možnost **Přidat** > **Nový projekt** .

1. V dialogovém okně **Přidat nový projekt** vyberte možnost **nainstalováno** > **Visual C++** > **plocha systému Windows**. V prostředním podokně vyberte možnost **Průvodce desktopovou plochou systému Windows**.

1. Do pole **název** zadejte název projektu, například *MathClient*–. Klikněte na tlačítko **OK** .

1. V dialogovém okně **pracovní projekt Windows** v části **Typ aplikace**vyberte **Konzolová aplikace (. exe)**.

1. V části **Další možnosti**zrušte zaškrtnutí políčka **Předkompilovaná hlavička** , pokud je zaškrtnuto.

1. Kliknutím na **tlačítko OK** vytvořte projekt.

1. Po vytvoření aplikace konzoly se vytvoří prázdný program za vás. Název zdrojového souboru je stejný jako název, který jste zvolili dříve. V tomto příkladu je název `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Vytvoření konzolové aplikace C++, která odkazuje na statickou knihovnu v aplikaci Visual Studio 2015

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na nejvyšší uzel, **řešení ' StaticMath '** a otevřete místní nabídku. Chcete-li otevřít dialogové okno **Přidat nový projekt** , vyberte možnost **Přidat** > **Nový projekt** .

1. V dialogovém okně **Přidat nový projekt** vyberte možnost **nainstalované** > **Visual C++** > **Win32**. V prostředním podokně vyberte **Konzolová aplikace Win32**.

1. Do pole **název** zadejte název projektu, například *MathClient*–. Klikněte na tlačítko **OK** .

1. V dialogovém okně **Průvodce aplikací Win32** klikněte na tlačítko **Další**.

1. Na stránce **nastavení aplikace** v části **Typ aplikace**se ujistěte, že je vybraná **Konzolová aplikace** . V části **Další možnosti**zrušte zaškrtnutí políčka **Předkompilovaná hlavička**a zaškrtněte políčko **prázdného projektu** . Kliknutím na tlačítko **Dokončit** vytvořte projekt.

1. Chcete-li přidat zdrojový soubor do prázdného projektu, klikněte pravým tlačítkem myši a otevřete místní nabídku pro projekt **MathClient** v **Průzkumník řešení**a pak zvolte možnost **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **Visual C++** > **kód**. V prostředním podokně vyberte **soubor C++ (. cpp)**. Zadejte název zdrojového souboru, například *MathClient. cpp*, a pak klikněte na tlačítko **Přidat** . Zobrazí se prázdný zdrojový soubor.

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a>Použití funkce ze statické knihovny v aplikaci

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Použití funkce ze statické knihovny v aplikaci

1. Než budete moci použít matematické rutiny ve statické knihovně, je nutné na ni odkazovat. Otevřete místní nabídku projektu **MathClient** v **Průzkumník řešení**a pak zvolte **Přidat** > **odkaz**.

1. Dialogové okno **Přidat odkaz** obsahuje seznam knihoven, které lze odkazovat. Karta **projekty** obsahuje seznam projektů v aktuálním řešení a všechny knihovny, na které odkazují. Otevřete kartu **projekty** , zaškrtněte políčko **MathLibrary** a poté klikněte na tlačítko **OK** .

1. Chcete-li `MathLibrary.h` odkazovat na hlavičkový soubor, je nutné upravit cestu k zahrnutým adresářům. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **MathClient** a otevřete místní nabídku. Kliknutím na **vlastnosti** otevřete dialogové okno **stránky vlastností MathClient** .

1. V dialogovém okně **stránky vlastností MathClient** nastavte rozevírací seznam **Konfigurace** na **všechny konfigurace**. Nastavte rozevírací seznam **platforma** na **všechny platformy**.

1. Vyberte **vlastnosti** > konfigurace**Obecné** stránka vlastností**C/C++** > . Do vlastnosti **Další adresáře pro zahrnutí** zadejte cestu k adresáři **MathLibrary** , nebo ji vyhledejte.

   Pro vyhledání cesty k adresáři:

   1. Otevřete rozevírací seznam další hodnota vlastnosti **adresáře pro zahrnutí** a zvolte možnost **Upravit**.

   1. V dialogovém okně **Další adresáře k zahrnutí** dvakrát klikněte na horní část textového pole. Pak zvolte tlačítko se třemi tečkami (**...**) na konci řádku.

   1. V dialogovém okně **Vybrat adresář** přejděte nahoru na úroveň a pak vyberte adresář **MathLibrary** . Pak zvolte tlačítko **Vybrat složku** a uložte výběr.

   1. V dialogovém okně **Další adresáře k zahrnutí** klikněte na tlačítko **OK** .

   1. V dialogovém okně **stránky vlastností** kliknutím na tlačítko **OK** uložte změny projektu.

1. V této aplikaci teď můžete `Arithmetic` použít třídu zahrnutím `#include "MathLibrary.h"` hlavičky do kódu. Nahraďte obsah `MathClient.cpp` tímto kódem:

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

1. Chcete-li sestavit spustitelný soubor, v řádku nabídek vyberte **sestavení** > **řešení** sestavení.

## <a name="run-the-app"></a><a name="RunApp"></a>Spuštění aplikace

### <a name="to-run-the-app"></a>Spuštění aplikace

1. Ujistěte se, že je vybrána možnost **MathClient** jako výchozí projekt. Pokud ho chcete vybrat, klikněte pravým tlačítkem myši a otevřete místní nabídku pro **MathClient** v **Průzkumník řešení**a pak zvolte **nastavit jako spouštěný projekt**.

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
