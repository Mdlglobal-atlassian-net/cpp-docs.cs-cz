---
title: Vytvoření projektu aplikace konzoly C++
description: Vytvoření konzolové aplikace Hello World a kalkulačky ve Visual C++
ms.custom: mvc
ms.date: 08/19/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 27522a6960546dc935ea3d9bce974eb36789c0aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "80079293"
---
# <a name="create-a-c-console-app-project"></a>Vytvoření projektu aplikace konzoly C++

::: moniker range=">=vs-2019"

Obvyklým výchozím bodem pro programátor c++ je "Hello, world!" aplikace, která běží na příkazovém řádku. To je to, co vytvoříte v Sadě Visual Studio v tomto článku a pak přejdeme k něčemu náročnějšímu: aplikaci kalkulačky.

## <a name="prerequisites"></a>Požadavky

- Mít Visual Studio s **desktopvývoj s c++** úlohy nainstalované a spuštěné v počítači. Pokud ještě není nainstalovaná, přečtěte si informace [o instalaci podpory C++ v sadě Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Vytvoření projektu aplikace

Visual Studio používá *projekty* k uspořádání kódu pro aplikaci a *řešení* pro uspořádání projektů. Projekt obsahuje všechny možnosti, konfigurace a pravidla používaná k vytváření aplikací. Spravuje také vztah mezi všemi soubory projektu a všechny externí soubory. Chcete-li vytvořit aplikaci, nejprve vytvoříte nový projekt a řešení.

1. Pokud jste právě spustili Visual Studio, zobrazí se dialogové okno Visual Studio 2019. **Chcete-li začít, zvolte Vytvořit nový projekt.**

   ![Úvodní dialogové okno Visual Studia 2019](./media/calc-vs2019-initial-dialog.png "Úvodní dialogové okno Visual Studia 2019")

   V opačném případě na panelu nabídek v sadě Visual Studio zvolte **Soubor** > **nový** > **projekt**. Otevře se okno **Vytvořit nový projekt.**

1. V seznamu šablon projektů zvolte **Konzolová aplikace**a pak zvolte **Další**.

   ![Volba šablony konzolové aplikace](./media/calc-vs2019-choose-console-app.png "Volba šablony konzolové aplikace")

   > [!Important]
   > Ujistěte se, že jste zvolili verzi c++ šablony **konzolové aplikace.** Má **c++**, **Windows**a **konzolové** značky a ikona má "++" v rohu.

1. V dialogovém okně **Konfigurovat nový projekt** vyberte pole Pro **úpravu názvu projektu,** pojmenujte nový projekt *CalculatorTutorial*a pak zvolte **Vytvořit**.

   ![Pojmenování projektu v dialogovém okně Konfigurovat nový projekt](./media/calc-vs2019-name-your-project.png "Pojmenování projektu v dialogovém okně Konfigurovat nový projekt")

   Vytvoří se prázdná aplikace konzoly Windows jazyka C++. Konzolové aplikace používají okno konzoly systému Windows k zobrazení výstupu a přijetí uživatelského vstupu. V sadě Visual Studio se otevře okno editoru a zobrazí generovaný kód:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n";
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>Ověření, že se vaše nová aplikace staví a spouští

Šablona pro novou konzolovou aplikaci systému Windows vytvoří jednoduchou aplikaci "Hello World" pro Jazyk C++. V tomto okamžiku uvidíte, jak Visual Studio sestavuje a spouští aplikace, které vytvoříte přímo z ide.

1. Chcete-li vytvořit projekt, zvolte **sestavení řešení** z nabídky **sestavení.** Okno **Výstup** zobrazuje výsledky procesu sestavení.

   ![Sestavení projektu](./media/calc-vs2019-build-your-project.png "Sestavení projektu")

1. Chcete-li kód spustit, zvolte na řádku nabídek možnost **Ladění**, **Spustit bez ladění**.

   ![Zahájení projektu](./media/calc-vs2019-hello-world-console.png "Zahájení projektu")

   Otevře se okno konzoly a potom spustí aplikaci. Když spustíte konzolovou aplikaci v sadě Visual Studio, spustí váš kód a vytiskne "Stisknutím libovolné klávesy zavřete toto okno . . ." abyste měli možnost vidět výstup. Blahopřejeme! Vytvořil jsi svůj první "Ahoj, světe!" konzolové aplikace v sadě Visual Studio!

1. Stisknutím klávesy zavřete okno konzoly a vraťte se do sady Visual Studio.

Nyní máte nástroje pro sestavení a spuštění aplikace po každé změně, abyste ověřili, že kód stále funguje podle očekávání. Později vám ukážeme, jak ji ladit, pokud se tak nestane.

## <a name="edit-the-code"></a>Úprava kódu

Nyní změníme kód v této šabloně na aplikaci kalkulačky.

1. V souboru *CalculatorTutorial.cpp* upravte kód tak, aby odpovídal tomuto příkladu:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > Principy kódu:
   >
   > - Příkazy `#include` umožňují odkazovat na kód umístěný v jiných souborech. Někdy se může zobrazit název souboru obklopený**\<** úhlovými závorkami ( ); jindy je obklopena uvozovkami (**" "**). Obecně platí, že úhlové závorky se používají při odkazování na standardní knihovnu jazyka C++, zatímco uvozovky se používají pro jiné soubory.
   > - Řádek `using namespace std;` říká kompilátoru očekávat, že soubory ze standardní knihovny C++ budou použity v tomto souboru. Bez tohoto řádku by muselo být každému klíčovému `std::`slovu z knihovny předchází písmeno a, které označuje jeho obor. Například bez tohoto řádku by `cout` každý odkaz na `std::cout`muset být zapsánjako . Příkaz `using` je přidán, aby kód vypadat čistější.
   > - Klíčové `cout` slovo se používá k tisku na standardní výstup v jazyce C++. Operátor ** \< ** říká kompilátoru odeslat vše, co je na pravo z něj na standardní výstup.
   > - Klíčové slovo **endl** je jako klávesa Enter; ukončí čáru a přesune kurzor na další řádek. Je lepší praxe, aby `\n` uvnitř řetězce (obsažené "") provést totéž, `endl` jako vždy vyprázdní vyrovnávací paměti a může poškodit výkon programu, ale protože se jedná o velmi malou aplikaci, `endl` se používá místo pro lepší čitelnost.
   > - Všechny příkazy Jazyka C++ musí končit středníky a `main()` všechny aplikace jazyka C++ musí obsahovat funkci. Tato funkce je to, co program běží na začátku. Aby mohl být `main()` použit, musí být přístupný z celého kódu.

1. Chcete-li soubor uložit, zadejte **Ctrl+S**nebo zvolte ikonu **Uložit** v horní části prostředí IDE, ikonu diskety na panelu nástrojů pod panelem nabídek.

1. Chcete-li aplikaci spustit, stiskněte **kombinaci kláves Ctrl+F5** nebo přejděte do nabídky **Ladění** a zvolte **Spustit bez ladění**. Mělo by se zobrazit okno konzoly, které zobrazuje text zadaný v kódu.

1. Až budete hotovi, zavřete okno konzoly.

## <a name="add-code-to-do-some-math"></a>Přidání kódu pro nějakou matematiku

Je čas přidat nějakou matematickou logiku.

### <a name="to-add-a-calculator-class"></a>Přidání třídy Kalkulačka

1. Přejděte do nabídky **Projekt** a zvolte **Přidat třídu**. Do textového pole **Název třídy** zadejte *Kalkulačka*. Vyberte **OK**. Do projektu se přidají dva nové soubory. Chcete-li uložit všechny změněné soubory najednou, stiskněte **kombinaci kláves Ctrl+Shift+S**. Je to klávesová zkratka pro **soubor** > **uložit vše**. K dispozici je také tlačítko panelu nástrojů pro **Uložit vše**, ikona dvou disket, které se nacházejí vedle tlačítka **Uložit.** Obecně platí, že je vhodné často **ukládat vše,** takže při ukládání nezmeškáte žádné soubory.

   ![Vytvoření třídy Kalkulačka](./media/calc-vs2019-create-calculator-class.png "Vytvoření třídy Kalkulačka")

   Třída je jako plán pro objekt, který něco dělá. V tomto případě definujeme kalkulačku a jak by měla fungovat. Průvodce **přidáním třídy,** který jste použili výše, vytvořil soubory .h a CPP, které mají stejný název jako třída. Úplný seznam souborů projektu můžete zobrazit v okně **Průzkumník řešení,** které je viditelné na straně rozhraní IDE. Pokud okno není viditelné, můžete ho otevřít z řádku nabídek: zvolte **Zobrazit** > **Průzkumník řešení**.

   ![Průzkumník řešení](./media/calc-vs2019-solution-explorer.png "Průzkumník řešení")

   Nyní byste měli mít tři karty otevřené v editoru: *CalculatorTutorial.cpp*, *Calculator.h*a *Calculator.cpp*. Pokud jednu z nich omylem zavřete, můžete ji znovu otevřít poklepáním v okně **Průzkumník řešení.**

1. V **Calculator.h**, `Calculator();` `~Calculator();` odstraňte a řádky, které byly generovány, protože nebudete potřebovat zde. Dále přidejte následující řádek kódu, aby soubor nyní vypadal takto:

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > Vysvětlení kódu
   >
   > - Řádek, který jste přidali `Calculate`deklaruje novou funkci s názvem , kterou použijeme ke spuštění matematických operací pro sčítání, odčítání, násobení a dělení.
   > - Kód C++ je uspořádán do *souborů záhlaví* (.h) a *zdrojových* (.cpp). Několik dalších přípon souborů jsou podporovány různými kompilátory, ale to jsou hlavní, o kterých je třeba vědět. Funkce a proměnné jsou obvykle *deklarovány*, to znamená, že je uveden název a typ, v souborech hlaviček a *implementovány*, nebo jsou uvedeny definice ve zdrojových souborech. Chcete-li získat přístup ke kódu `#include "filename.h"`definovanému v jiném souboru, můžete použít soubor , kde název souboru .h je název souboru, který deklaruje proměnné nebo funkce, které chcete použít.
   > - Dva řádky, které jste odstranili deklaroval *konstruktor* a *destruktor* pro třídu. Pro jednoduchou třídu, jako je tato, kompilátor je vytvoří pro vás a jejich použití jsou nad rámec tohoto kurzu.
   > - Je vhodné uspořádat kód do různých souborů na základě toho, co dělá, takže je snadné najít kód, který potřebujete později. V `Calculator` našem případě definujeme třídu odděleně od `main()` souboru obsahujícího funkci, ale plánujeme odkazovat na třídu `Calculator` v `main()`.

1. Pod ním se zobrazí zelená `Calculate`vlnovka. Je to proto, že jsme `Calculate` nedefinovali funkci v souboru CPP. Najeďte nad slovo, klikněte na žárovku (v tomto případě šroubovák), který se objeví, a zvolte **Vytvořit definici 'Vypočítat' v Calculator.cpp**.

   ![Vytvořit definici výpočtu](./media/calc-vs2019-create-definition.png "Vytvořit definici výpočtu")

   Zobrazí se vyskakovací okno, které vám umožní nahlédnout do změny kódu, která byla provedena v jiném souboru. Kód byl přidán do *souboru Calculator.cpp*.

   ![Automaticky otevírané okno s definicí vypočítat](./media/calc-vs2019-pop-up-definition.png "Automaticky otevírané okno s definicí vypočítat")

   V současné době se vrátí pouze 0,0. To teď změníme. Stisknutím **klávesy Esc** zavřete automaticky otevírané okno.

1. Přepněte do souboru *Calculator.cpp* v okně editoru. Odeberte oddíly `Calculator()` a `~Calculator()` (stejně jako v souboru `Calculate()`H) a přidejte do něj následující kód :

    ```cpp
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > Vysvětlení kódu
   >
   > - Funkce `Calculate` spotřebovává číslo, operátor a druhé číslo, pak provede požadovanou operaci na čísla.
   > - Příkaz switch zkontroluje, který operátor byl poskytnut, a provede pouze případ odpovídající této operaci. Výchozí: case je záložní v případě, že uživatel zadá operátor, který není přijat, takže program není přerušit. Obecně platí, že je nejlepší zpracovat neplatný vstup uživatele elegantnějším způsobem, ale to je nad rámec tohoto kurzu.
   > - Klíčové `double` slovo označuje typ čísla, který podporuje desetinná místa. Tímto způsobem kalkulačka zvládne desetinné matematické a celé číslo matematiky. Funkce `Calculate` je nutné vždy vrátit takové číslo `double` z důvodu na samém začátku kódu (to znamená návratový typ funkce), což je důvod, proč jsme se vrátit 0,0 i ve výchozím případě.
   > - Soubor .h deklaruje *prototyp*funkce , který compileru předem sděluje, jaké parametry vyžaduje a jaký návratový typ od něj lze očekávat. Soubor CPP obsahuje všechny podrobnosti implementace funkce.

Pokud vytvoříte a spustíte kód znovu v tomto okamžiku, bude stále ukončit po dotazem, které operace provést. Dále upravíte funkci `main` tak, aby dělala některé výpočty.

### <a name="to-call-the-calculator-class-member-functions"></a>Volání členských funkcí třídy Kalkulačka

1. Nyní pojďme aktualizovat `main` funkci v *CalculatorTutorial.cpp*:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > Vysvětlení kódu
   >
   > - Vzhledem k tomu, že `main()` programy jazyka C++ vždy začínají na `#include` funkci, musíme volat náš další kód odtud, takže je potřeba prohlášení.
   > - Některé počáteční `x`proměnné `y` `oper`, `result` , a jsou deklarovány pro uložení prvního čísla, druhého čísla, operátoru a konečného výsledku. Je vždy vhodné dát jim některé počáteční hodnoty, aby se zabránilo nedefinované chování, což je to, co se zde děje.
   > - Řádek `Calculator c;` deklaruje objekt s názvem 'c' jako instancizici třídy. `Calculator` Samotná třída je jen plán, jak fungují kalkulačky; objekt je konkrétní kalkulačka, která provádí matematiku.
   > - Příkaz `while (true)` je smyčka. Kód uvnitř smyčky pokračuje v provádění znovu a znovu tak `()` dlouho, dokud podmínka uvnitř platí. Vzhledem k tomu, `true`podmínka je jednoduše uveden jako , je to vždy pravda, takže smyčka běží navždy. Chcete-li program ukončit, musí uživatel okno konzoly zavřít ručně. V opačném případě program vždy čeká na nový vstup.
   > - Klíčové `cin` slovo se používá k přijetí vstupu od uživatele. Tento vstupní datový proud je dostatečně chytrý, aby zpracoval řádek textu zadaný v okně konzoly a umístil jej do každé z uvedených proměnných v pořadí za předpokladu, že vstup uživatele odpovídá požadované specifikaci. Tento řádek můžete upravit tak, aby přijímal různé typy vstupů, například více než dvě čísla, ale `Calculate()` funkce by také musela být aktualizována, aby to bylo možné zpracovat.
   > - Výraz `c.Calculate(x, oper, y);` volá `Calculate` dříve definovanou funkci a poskytuje zadané vstupní hodnoty. Funkce pak vrátí číslo, které `result`se uloží do aplikace .
   > - Nakonec `result` je vytištěn na konzoli, takže uživatel vidí výsledek výpočtu.

### <a name="build-and-test-the-code-again"></a>Sestavení a testování kódu znovu

Nyní je čas otestovat program znovu, aby se ujistil, vše funguje správně.

1. Stisknutím **kláves Ctrl+F5** aplikaci znovu sestavíte a spustíte.

1. Zadejte `5 + 5`a stiskněte **Enter**. Ověřte, zda je výsledek 10.

   ![Výsledek 5 + 5](./media/calc-vs2019-five-plus-five.png "Výsledek 5 + 5")

## <a name="debug-the-app"></a>Ladění aplikace

Vzhledem k tomu, že uživatel může zadat cokoli do okna konzoly, ujistěte se, že kalkulačka zpracovává některé vstupy podle očekávání. Místo spuštění programu, pojďme ladit místo toho, takže můžeme zkontrolovat, co to dělá v detailu, krok-za-krokem.

### <a name="to-run-the-app-in-the-debugger"></a>Spuštění aplikace v ladicím programu

1. Nastavte zarážku `result = c.Calculate(x, oper, y);` na řádku, těsně poté, co byl uživatel požádán o vstup. Chcete-li nastavit zarážku, klepněte vedle čáry v šedém svislém pruhu podél levého okraje okna editoru. Zobrazí se červená tečka.

   ![Nastavení zarážky](./media/calc-vs2019-set-breakpoint.png "Nastavení zarážky")

   Nyní, když jsme ladění programu, vždy pozastaví provádění na tomto řádku. Již máme hrubou představu, že program funguje pro jednoduché případy. Vzhledem k tomu, že nechceme pozastavit provádění pokaždé, udělejme zarážku podmíněnou.

1. Klepněte pravým tlačítkem myši na červenou tečku, která představuje zarážku, a zvolte **Podmínky**. Do textového pole podmínky `(y == 0) && (oper == '/')`zadejte . Až budete hotovi, zvolte tlačítko **Zavřít.** Podmínka se uloží automaticky.

   ![Nastavení podmíněné zarážky](./media/calc-vs2019-conditional-breakpoint.png "Nastavení podmíněné zarážky")

   Nyní pozastavíme provádění na zarážky konkrétně pokud dojde k pokusu o dělení 0.

1. Chcete-li program ladit, stiskněte **klávesu F5**nebo zvolte tlačítko panelu nástrojů **místního ladicího programu systému Windows** se zelenou šipkou. Pokud v konzolové aplikaci zadáte něco jako "5 - 0", program se chová normálně a běží. Pokud však zadáte "10 / 0", pozastaví se na zarážky. Můžete dokonce umístit libovolný počet mezer mezi `cin` operátorem a čísly: je dostatečně chytrý, aby správně analyzovat vstup.

   ![Pozastavení podmíněné zarážky](./media/calc-vs2019-debug-breakpoint.png "Pozastavení podmíněné zarážky")

### <a name="useful-windows-in-the-debugger"></a>Užitečná okna v ladicím programu

Při každém ladění kódu si můžete všimnout, že se zobrazí některá nová okna. Tato okna mohou pomoci s laděním. Podívejte se na okno **Autos.** Okno **Autos** zobrazuje aktuální hodnoty proměnných použitých alespoň tři řádky před a až na aktuální řádek. Chcete-li zobrazit všechny proměnné z této funkce, přepněte do okna **Locals.** Můžete skutečně upravit hodnoty těchto proměnných při ladění, chcete-li zjistit, jaký vliv by měly na program. V tomto případě je necháme na pokoji.

   ![Okno Místní](./media/calc-vs2019-debug-locals.png "Okno Místní")

Můžete také jenom najet přes proměnné v samotném kódu, abyste viděli jejich aktuální hodnoty, kde je aktuálně pozastaveno spuštění. Ujistěte se, že okno editoru je v centru pozornosti kliknutím na něj první.

   ![Chcete-li zobrazit aktuální hodnoty proměnných, najeďte na něj.](./media/calc-vs2019-hover-tooltip.png "Chcete-li zobrazit aktuální hodnoty proměnných, najeďte na něj.")

### <a name="to-continue-debugging"></a>Chcete-li pokračovat v ladění

1. Žlutá čára vlevo zobrazuje aktuální bod provedení. Aktuální volání `Calculate`linky , takže stisknutím **klávesy F11** krok **do** funkce. Ocitnete se v těle `Calculate` funkce. Buďte opatrní s **krokem do**; Pokud to uděláte příliš mnoho, můžete ztrácet spoustu času. Přejde do libovolného kódu, který používáte na řádku, na které se nacházíte, včetně standardních funkcí knihovny.

1. Nyní, když je bod spuštění na `Calculate` začátku funkce, stisknutím **klávesy F10** přejděte na další řádek v provádění programu. **F10** je také známý jako **Krok přes**. **Pomocí funkce Krok přes** krok můžete přejít z řádku na řádek, aniž byste se ponořili do podrobností o tom, co se děje v každé části řádku. Obecně byste měli použít **Krok přes** místo **Krok do**, pokud chcete ponořit hlouběji do kódu, který je `Calculate`volán odjinud (stejně jako jste se dostat k tělu).

1. Pokračujte v používání **f10** krok **přes** každý `main()` řádek, dokud se nevrátíte `cout` k funkci v druhém souboru a zastavte na řádku.

   Vypadá to, že program dělá to, co se očekává: bere první číslo a rozděluje ho druhým. Na `cout` řádku najeďte `result` na proměnnou nebo `result` se podívejte v okně **Autos.** Uvidíte, že jeho hodnota je uvedena jako "inf", což nevypadá správně, takže to opravíme. Linka `cout` pouze výstupy bez ohledu `result`na hodnotu je uložena v , takže když krok ještě jednu čáru vpřed pomocí **F10**, okno konzoly zobrazí:

   ![Výsledek dělení nulou](./media/calc-vs2019-divide-by-zero-fail.png "Výsledek dělení nulou")

   K tomuto výsledku dochází, protože dělení nulou není definováno, takže program nemá číselnou odpověď na požadovanou operaci.

### <a name="to-fix-the-divide-by-zero-error"></a>Oprava chyby "dělení nulou"

Pojďme zpracovat dělení nulou více elegantně, takže uživatel může pochopit problém.

1. Proveďte následující změny v *CalculatorTutorial.cpp*. (Můžete nechat program spuštěný při úpravách, a to díky funkci ladicího programu s názvem **Upravit a pokračovat):**

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. Nyní stiskněte **f5** jednou. Provádění programu pokračuje celou cestu, dokud má pozastavit požádat o vstup uživatele. Zadejte `10 / 0` znovu. Nyní je vytištěna užitečnější zpráva. Uživatel je požádán o další vstup a program pokračuje v normálním provádění.

   ![Konečný výsledek po změnách](./media/calc-vs2019-final-verification.png "Konečný výsledek po změnách")

   > [!Note]
   > Při úpravě kódu v režimu ladění existuje riziko, že kód bude zastaralý. K tomu dochází, když ladicí program stále běží váš starý kód a ještě jej neaktualizoval se změnami. Ladicí program se objeví dialogové okno, které vás informuje, když k tomu dojde. Někdy může být nutné stisknout **klávesu F5,** abyste aktualizovali spouštěný kód. Zejména pokud provedete změnu uvnitř funkce, zatímco bod spuštění je uvnitř této funkce, budete muset vystoupit z funkce, pak zpět do ní znovu získat aktualizovaný kód. Pokud to z nějakého důvodu nefunguje a zobrazí se chybová zpráva, můžete přestat ladit kliknutím na červený čtverec v panelu nástrojů pod nabídkami v horní části rozhraní IDE a poté znovu začít ladit zadáním **klávesy F5** nebo výběrem zelené šipky "play" vedle tlačítka stop na panelu nástrojů.

   > Principy klávesových zkratek Spustit a ladění
   >
   > - **F5** (nebo **Ladění** > **Start Ladění**) spustí relaci ladění, pokud jeden ještě není aktivní a spustí program, dokud je přístupná zarážka nebo program potřebuje vstup uživatele. Pokud není potřeba žádný vstup uživatele a není k dispozici žádná zarážka pro přístup, program se ukončí a okno konzoly se po dokončení programu zavře samo. Pokud máte něco jako "Hello World" program ke spuštění, použijte **Ctrl + F5** nebo nastavit zarážku před zadáním **F5,** aby okno otevřené.
   > - **Ctrl+F5** (nebo **Ladění** > **Start bez ladění)** spustí aplikaci bez přepnutí do režimu ladění. To je o něco rychlejší než ladění a okno konzoly zůstane otevřené po dokončení provádění programu.
   > - **F10** (známé jako **Krok přes)** umožňuje iteraci prostřednictvím kódu, řádek po řádku a vizualizovat, jak je kód spuštěn a jaké hodnoty proměnných jsou v každém kroku provádění.
   > - **F11** (známý jako **Krok do**) funguje podobně jako **Krok přes**, s výjimkou kroků do všech funkcí volaných na řádku provádění. Pokud například spuštěná linka volá funkci, stisknutím **klávesy F11** přesunete ukazatel do těla funkce, takže můžete sledovat kód funkce, který se spouští, než se vrátíte na linku, na které jste začali. Stisknutím **klávesy F10** přes volání funkce a jen přesune na další řádek; volání funkce stále probíhá, ale program se nezastaví, aby vám ukázal, co dělá.

### <a name="close-the-app"></a>Zavření aplikace

- Pokud je stále spuštěná, zavřete okno konzoly pro aplikaci kalkulačky.

## <a name="the-finished-app"></a>Dokončená aplikace

Blahopřejeme! Dokončili jste kód pro aplikaci kalkulačky a vytvořili a ladili ho v sadě Visual Studio.

## <a name="next-steps"></a>Další kroky

[Další informace o Visual Studiu pro C++](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end

::: moniker range="<vs-2019"

Obvyklým výchozím bodem pro programátor c++ je "Hello, world!" aplikace, která běží na příkazovém řádku. To je to, co vytvoříte v Sadě Visual Studio v tomto článku a pak přejdeme k něčemu náročnějšímu: aplikaci kalkulačky.

## <a name="prerequisites"></a>Požadavky

- Mít Visual Studio s **desktopvývoj s c++** úlohy nainstalované a spuštěné v počítači. Pokud ještě není nainstalovaná, přečtěte si informace [o instalaci podpory C++ v sadě Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Vytvoření projektu aplikace

Visual Studio používá *projekty* k uspořádání kódu pro aplikaci a *řešení* pro uspořádání projektů. Projekt obsahuje všechny možnosti, konfigurace a pravidla používaná k vytváření aplikací. Spravuje také vztah mezi všemi soubory projektu a všechny externí soubory. Chcete-li vytvořit aplikaci, nejprve vytvoříte nový projekt a řešení.

1. Na panelu nabídek v sadě Visual Studio zvolte **Soubor** > **nového** > **projektu**. Otevře se okno **Nový projekt.**

2. Na levém postranním panelu zkontrolujte, zda je **vybránvisual c++.** Ve středu zvolte **Aplikace konzoly systému Windows**.

3. V poli **Name** edit v dolní části pojmenujte nový projekt *CalculatorTutorial*a pak zvolte **OK**.

   ![Dialogové okno Nový projekt](./media/calculator-new-project-dialog.png "Dialogové okno Nový projekt")

   Vytvoří se prázdná aplikace konzoly Windows jazyka C++. Konzolové aplikace používají okno konzoly systému Windows k zobrazení výstupu a přijetí uživatelského vstupu. V sadě Visual Studio se otevře okno editoru a zobrazí generovaný kód:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n";
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>Ověření, že se vaše nová aplikace staví a spouští

Šablona pro novou aplikaci konzoly systému Windows vytvoří jednoduchou aplikaci "Hello World" pro Jazyk A++. V tomto okamžiku uvidíte, jak Visual Studio sestavuje a spouští aplikace, které vytvoříte přímo z ide.

1. Chcete-li vytvořit projekt, zvolte **sestavení řešení** z nabídky **sestavení.** Okno **Výstup** zobrazuje výsledky procesu sestavení.

   ![Sestavení projektu](./media/calculator-initial-build-output.png "Sestavení projektu")

1. Chcete-li kód spustit, zvolte na řádku nabídek možnost **Ladění**, **Spustit bez ladění**.

   ![Zahájení projektu](./media/calculator-hello-world-console.png "Zahájení projektu")

   Otevře se okno konzoly a potom spustí aplikaci. Když spustíte konzolovou aplikaci v sadě Visual Studio, spustí váš kód a vytiskne se "Stisknutím libovolné klávesy pokračujte . . ." abyste měli možnost vidět výstup. Blahopřejeme! Vytvořil jsi svůj první "Ahoj, světe!" konzolové aplikace v sadě Visual Studio!

1. Stisknutím klávesy zavřete okno konzoly a vraťte se do sady Visual Studio.

Nyní máte nástroje pro sestavení a spuštění aplikace po každé změně, abyste ověřili, že kód stále funguje podle očekávání. Později vám ukážeme, jak ji ladit, pokud se tak nestane.

## <a name="edit-the-code"></a>Úprava kódu

Nyní změníme kód v této šabloně na aplikaci kalkulačky.

1. V souboru *CalculatorTutorial.cpp* upravte kód tak, aby odpovídal tomuto příkladu:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > Principy kódu:
   >
   > - Příkazy `#include` umožňují odkazovat na kód umístěný v jiných souborech. Někdy se může zobrazit název souboru obklopený**\<** úhlovými závorkami ( ); jindy je obklopena uvozovkami (**" "**). Obecně platí, že úhlové závorky se používají při odkazování na standardní knihovnu jazyka C++, zatímco uvozovky se používají pro jiné soubory.
   > - Řádek `#include "pch.h"` (nebo v sadě Visual Studio `#include "stdafx.h"`2017 a starší) odkazuje na něco, co je známé jako předkompilované záhlaví. Ty jsou často používány profesionálníprogramátory ke zlepšení doby kompilace, ale jsou nad rámec tohoto kurzu.
   > - Řádek `using namespace std;` říká kompilátoru očekávat, že soubory ze standardní knihovny C++ budou použity v tomto souboru. Bez tohoto řádku by muselo být každému klíčovému `std::`slovu z knihovny předchází písmeno a, které označuje jeho obor. Například bez tohoto řádku by `cout` každý odkaz na `std::cout`muset být zapsánjako . Příkaz `using` je přidán, aby kód vypadat čistější.
   > - Klíčové `cout` slovo se používá k tisku na standardní výstup v jazyce C++. Operátor ** \< ** říká kompilátoru odeslat vše, co je na pravo z něj na standardní výstup.
   > - Klíčové slovo **endl** je jako klávesa Enter; ukončí čáru a přesune kurzor na další řádek. Je lepší praxe, aby `\n` uvnitř řetězce (obsažené "") provést totéž, `endl` jako vždy vyprázdní vyrovnávací paměti a může poškodit výkon programu, ale protože se jedná o velmi malou aplikaci, `endl` se používá místo pro lepší čitelnost.
   > - Všechny příkazy Jazyka C++ musí končit středníky a `main()` všechny aplikace jazyka C++ musí obsahovat funkci. Tato funkce je to, co program běží na začátku. Aby mohl být `main()` použit, musí být přístupný z celého kódu.

1. Chcete-li soubor uložit, zadejte **Ctrl+S**nebo zvolte ikonu **Uložit** v horní části prostředí IDE, ikonu diskety na panelu nástrojů pod panelem nabídek.

1. Chcete-li aplikaci spustit, stiskněte **kombinaci kláves Ctrl+F5** nebo přejděte do nabídky **Ladění** a zvolte **Spustit bez ladění**. Pokud se zobrazí vyskakovací okno s prohlášením, že **tento projekt je zastaralý**, můžete vybrat Možnost **Nezobrazovat tento dialog znovu**a potom zvolte **Ano** pro sestavení aplikace. Mělo by se zobrazit okno konzoly, které zobrazuje text zadaný v kódu.

   ![Sestavení a spuštění aplikace](./media/calculator-first-launch.gif "Sestavení a spuštění aplikace")

1. Až budete hotovi, zavřete okno konzoly.

## <a name="add-code-to-do-some-math"></a>Přidání kódu pro nějakou matematiku

Je čas přidat nějakou matematickou logiku.

### <a name="to-add-a-calculator-class"></a>Přidání třídy Kalkulačka

1. Přejděte do nabídky **Projekt** a zvolte **Přidat třídu**. Do textového pole **Název třídy** zadejte *Kalkulačka*. Vyberte **OK**. Do projektu se přidají dva nové soubory. Chcete-li uložit všechny změněné soubory najednou, stiskněte **kombinaci kláves Ctrl+Shift+S**. Je to klávesová zkratka pro **soubor** > **uložit vše**. K dispozici je také tlačítko panelu nástrojů pro **Uložit vše**, ikona dvou disket, které se nacházejí vedle tlačítka **Uložit.** Obecně platí, že je vhodné často **ukládat vše,** takže při ukládání nezmeškáte žádné soubory.

   ![Vytvoření třídy Kalkulačka](./media/calculator-create-class.gif "Vytvoření třídy Kalkulačka")

   Třída je jako plán pro objekt, který něco dělá. V tomto případě definujeme kalkulačku a jak by měla fungovat. Průvodce **přidáním třídy,** který jste použili výše, vytvořil soubory .h a CPP, které mají stejný název jako třída. Úplný seznam souborů projektu můžete zobrazit v okně **Průzkumník řešení,** které je viditelné na straně rozhraní IDE. Pokud okno není viditelné, můžete ho otevřít z řádku nabídek: zvolte **Zobrazit** > **Průzkumník řešení**.

   ![Průzkumník řešení](./media/calculator-solution-explorer.png "Průzkumník řešení")

   Nyní byste měli mít tři karty otevřené v editoru: *CalculatorTutorial.cpp*, *Calculator.h*a *Calculator.cpp*. Pokud jednu z nich omylem zavřete, můžete ji znovu otevřít poklepáním v okně **Průzkumník řešení.**

1. V **Calculator.h**, `Calculator();` `~Calculator();` odstraňte a řádky, které byly generovány, protože nebudete potřebovat zde. Dále přidejte následující řádek kódu, aby soubor nyní vypadal takto:

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > Vysvětlení kódu
   >
   > - Řádek, který jste přidali `Calculate`deklaruje novou funkci s názvem , kterou použijeme ke spuštění matematických operací pro sčítání, odčítání, násobení a dělení.
   > - Kód C++ je uspořádán do *souborů záhlaví* (.h) a *zdrojových* (.cpp). Několik dalších přípon souborů jsou podporovány různými kompilátory, ale to jsou hlavní, o kterých je třeba vědět. Funkce a proměnné jsou obvykle *deklarovány*, to znamená, že je uveden název a typ, v souborech hlaviček a *implementovány*, nebo jsou uvedeny definice ve zdrojových souborech. Chcete-li získat přístup ke kódu `#include "filename.h"`definovanému v jiném souboru, můžete použít soubor , kde název souboru .h je název souboru, který deklaruje proměnné nebo funkce, které chcete použít.
   > - Dva řádky, které jste odstranili deklaroval *konstruktor* a *destruktor* pro třídu. Pro jednoduchou třídu, jako je tato, kompilátor je vytvoří pro vás a jejich použití jsou nad rámec tohoto kurzu.
   > - Je vhodné uspořádat kód do různých souborů na základě toho, co dělá, takže je snadné najít kód, který potřebujete později. V `Calculator` našem případě definujeme třídu odděleně od `main()` souboru obsahujícího funkci, ale plánujeme odkazovat na třídu `Calculator` v `main()`.

1. Pod ním se zobrazí zelená `Calculate`vlnovka. Je to proto, že jsme `Calculate` nedefinovali funkci v souboru CPP. Najeďte nad slovem, klikněte na žárovku, která se objeví, a zvolte **Vytvořit definici 'Vypočítat' v Calculator.cpp**. Zobrazí se vyskakovací okno, které vám umožní nahlédnout do změny kódu, která byla provedena v jiném souboru. Kód byl přidán do *souboru Calculator.cpp*.

   ![Vytvořit definici výpočtu](./media/calculator-create-definition.gif "Vytvořit definici výpočtu")

   V současné době se vrátí pouze 0,0. To teď změníme. Stisknutím **klávesy Esc** zavřete automaticky otevírané okno.

1. Přepněte do souboru *Calculator.cpp* v okně editoru. Odeberte oddíly `Calculator()` a `~Calculator()` (stejně jako v souboru `Calculate()`H) a přidejte do něj následující kód :

    ```cpp
    #include "pch.h"
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > Vysvětlení kódu
   >
   > - Funkce `Calculate` spotřebovává číslo, operátor a druhé číslo, pak provede požadovanou operaci na čísla.
   > - Příkaz switch zkontroluje, který operátor byl poskytnut, a provede pouze případ odpovídající této operaci. Výchozí: case je záložní v případě, že uživatel zadá operátor, který není přijat, takže program není přerušit. Obecně platí, že je nejlepší zpracovat neplatný vstup uživatele elegantnějším způsobem, ale to je nad rámec tohoto kurzu.
   > - Klíčové `double` slovo označuje typ čísla, který podporuje desetinná místa. Tímto způsobem kalkulačka zvládne desetinné matematické a celé číslo matematiky. Funkce `Calculate` je nutné vždy vrátit takové číslo `double` z důvodu na samém začátku kódu (to znamená návratový typ funkce), což je důvod, proč jsme se vrátit 0,0 i ve výchozím případě.
   > - Soubor .h deklaruje *prototyp*funkce , který compileru předem sděluje, jaké parametry vyžaduje a jaký návratový typ od něj lze očekávat. Soubor CPP obsahuje všechny podrobnosti implementace funkce.

Pokud vytvoříte a spustíte kód znovu v tomto okamžiku, bude stále ukončit po dotazem, které operace provést. Dále upravíte funkci `main` tak, aby dělala některé výpočty.

### <a name="to-call-the-calculator-class-member-functions"></a>Volání členských funkcí třídy Kalkulačka

1. Nyní pojďme aktualizovat `main` funkci v *CalculatorTutorial.cpp*:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > Vysvětlení kódu
   >
   > - Vzhledem k tomu, že `main()` programy jazyka C++ vždy začínají na `#include` funkci, musíme volat náš další kód odtud, takže je potřeba prohlášení.
   > - Některé počáteční `x`proměnné `y` `oper`, `result` , a jsou deklarovány pro uložení prvního čísla, druhého čísla, operátoru a konečného výsledku. Je vždy vhodné dát jim některé počáteční hodnoty, aby se zabránilo nedefinované chování, což je to, co se zde děje.
   > - Řádek `Calculator c;` deklaruje objekt s názvem 'c' jako instancizici třídy. `Calculator` Samotná třída je jen plán, jak fungují kalkulačky; objekt je konkrétní kalkulačka, která provádí matematiku.
   > - Příkaz `while (true)` je smyčka. Kód uvnitř smyčky pokračuje v provádění znovu a znovu tak `()` dlouho, dokud podmínka uvnitř platí. Vzhledem k tomu, `true`podmínka je jednoduše uveden jako , je to vždy pravda, takže smyčka běží navždy. Chcete-li program ukončit, musí uživatel okno konzoly zavřít ručně. V opačném případě program vždy čeká na nový vstup.
   > - Klíčové `cin` slovo se používá k přijetí vstupu od uživatele. Tento vstupní datový proud je dostatečně chytrý, aby zpracoval řádek textu zadaný v okně konzoly a umístil jej do každé z uvedených proměnných v pořadí za předpokladu, že vstup uživatele odpovídá požadované specifikaci. Tento řádek můžete upravit tak, aby přijímal různé typy vstupů, například více než dvě čísla, ale `Calculate()` funkce by také musela být aktualizována, aby to bylo možné zpracovat.
   > - Výraz `c.Calculate(x, oper, y);` volá `Calculate` dříve definovanou funkci a poskytuje zadané vstupní hodnoty. Funkce pak vrátí číslo, které `result`se uloží do aplikace .
   > - Nakonec `result` je vytištěn na konzoli, takže uživatel vidí výsledek výpočtu.

### <a name="build-and-test-the-code-again"></a>Sestavení a testování kódu znovu

Nyní je čas otestovat program znovu, aby se ujistil, vše funguje správně.

1. Stisknutím **kláves Ctrl+F5** aplikaci znovu sestavíte a spustíte.

1. Zadejte `5 + 5`a stiskněte **Enter**. Ověřte, zda je výsledek 10.

   ![Výsledek 5 + 5](./media/calculator-five-plus-five.png "Výsledek 5 + 5")

## <a name="debug-the-app"></a>Ladění aplikace

Vzhledem k tomu, že uživatel může zadat cokoli do okna konzoly, ujistěte se, že kalkulačka zpracovává některé vstupy podle očekávání. Místo spuštění programu, pojďme ladit místo toho, takže můžeme zkontrolovat, co to dělá v detailu, krok-za-krokem.

### <a name="to-run-the-app-in-the-debugger"></a>Spuštění aplikace v ladicím programu

1. Nastavte zarážku `result = c.Calculate(x, oper, y);` na řádku, těsně poté, co byl uživatel požádán o vstup. Chcete-li nastavit zarážku, klepněte vedle čáry v šedém svislém pruhu podél levého okraje okna editoru. Zobrazí se červená tečka.

   ![Nastavení zarážky](./media/calculator-set-breakpoint.gif "Nastavení zarážky")

   Nyní, když jsme ladění programu, vždy pozastaví provádění na tomto řádku. Již máme hrubou představu, že program funguje pro jednoduché případy. Vzhledem k tomu, že nechceme pozastavit provádění pokaždé, udělejme zarážku podmíněnou.

1. Klepněte pravým tlačítkem myši na červenou tečku, která představuje zarážku, a zvolte **Podmínky**. Do textového pole podmínky `(y == 0) && (oper == '/')`zadejte . Až budete hotovi, zvolte tlačítko **Zavřít.** Podmínka se uloží automaticky.

   ![Nastavení podmíněné zarážky](./media/calculator-conditional-breakpoint.gif "Nastavení podmíněné zarážky")

   Nyní pozastavíme provádění na zarážky konkrétně pokud dojde k pokusu o dělení 0.

1. Chcete-li program ladit, stiskněte **klávesu F5**nebo zvolte tlačítko panelu nástrojů **místního ladicího programu systému Windows** se zelenou šipkou. Pokud v konzolové aplikaci zadáte něco jako "5 - 0", program se chová normálně a běží. Pokud však zadáte "10 / 0", pozastaví se na zarážky. Můžete dokonce umístit libovolný počet mezer mezi operátorem a čísly; `cin` je dostatečně chytrý, aby správně analyzovat vstup.

   ![Pozastavení podmíněné zarážky](./media/calculator-debug-conditional.gif "Pozastavení podmíněné zarážky")

### <a name="useful-windows-in-the-debugger"></a>Užitečná okna v ladicím programu

Při každém ladění kódu si můžete všimnout, že se zobrazí některá nová okna. Tato okna mohou pomoci s laděním. Podívejte se na okno **Autos.** Okno **Autos** zobrazuje aktuální hodnoty proměnných použitých alespoň tři řádky před a až na aktuální řádek.

   ![Okno Autos](./media/calculator-autos.png "Okno Autos")

Chcete-li zobrazit všechny proměnné z této funkce, přepněte do okna **Locals.** Můžete skutečně upravit hodnoty těchto proměnných při ladění, chcete-li zjistit, jaký vliv by měly na program. V tomto případě je necháme na pokoji.

   ![Okno Místní](./media/calculator-locals.png "Okno Místní")

Můžete také jenom najet přes proměnné v samotném kódu, abyste viděli jejich aktuální hodnoty, kde je aktuálně pozastaveno spuštění. Ujistěte se, že okno editoru je v centru pozornosti kliknutím na něj první.

   ![Chcete-li zobrazit aktuální hodnoty proměnných, najeďte na něj.](./media/calculator-hover-tooltip.gif "Chcete-li zobrazit aktuální hodnoty proměnných, najeďte na něj.")

### <a name="to-continue-debugging"></a>Chcete-li pokračovat v ladění

1. Žlutá čára vlevo zobrazuje aktuální bod provedení. Aktuální volání `Calculate`linky , takže stisknutím **klávesy F11** krok **do** funkce. Ocitnete se v těle `Calculate` funkce. Buďte opatrní s **krokem do**; Pokud to uděláte příliš mnoho, můžete ztrácet spoustu času. Přejde do libovolného kódu, který používáte na řádku, na které se nacházíte, včetně standardních funkcí knihovny.

1. Nyní, když je bod spuštění na `Calculate` začátku funkce, stisknutím **klávesy F10** přejděte na další řádek v provádění programu. **F10** je také známý jako **Krok přes**. **Pomocí funkce Krok přes** krok můžete přejít z řádku na řádek, aniž byste se ponořili do podrobností o tom, co se děje v každé části řádku. Obecně byste měli použít **Krok přes** místo **Krok do**, pokud chcete ponořit hlouběji do kódu, který je `Calculate`volán odjinud (stejně jako jste se dostat k tělu).

1. Pokračujte v používání **f10** krok **přes** každý `main()` řádek, dokud se nevrátíte `cout` k funkci v druhém souboru a zastavte na řádku.

   ![Krok z vypočítat a zkontrolovat výsledek](./media/calculator-undefined-zero.gif "Krok z vypočítat a zkontrolovat výsledek")

   Vypadá to, že program dělá to, co se očekává: bere první číslo a rozděluje ho druhým. Na `cout` řádku najeďte `result` na proměnnou nebo `result` se podívejte v okně **Autos.** Uvidíte, že jeho hodnota je uvedena jako "inf", což nevypadá správně, takže to opravíme. Linka `cout` pouze výstupy bez ohledu `result`na hodnotu je uložena v , takže když krok ještě jednu čáru vpřed pomocí **F10**, okno konzoly zobrazí:

   ![Výsledek dělení nulou](./media/calculator-divide-by-zero-fail.png "Výsledek dělení nulou")

   K tomuto výsledku dochází, protože dělení nulou není definováno, takže program nemá číselnou odpověď na požadovanou operaci.

### <a name="to-fix-the-divide-by-zero-error"></a>Oprava chyby "dělení nulou"

Pojďme zpracovat dělení nulou více elegantně, takže uživatel může pochopit problém.

1. Proveďte následující změny v *CalculatorTutorial.cpp*. (Můžete nechat program spuštěný při úpravách, a to díky funkci ladicího programu s názvem **Upravit a pokračovat):**

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. Nyní stiskněte **f5** jednou. Provádění programu pokračuje celou cestu, dokud má pozastavit požádat o vstup uživatele. Zadejte `10 / 0` znovu. Nyní je vytištěna užitečnější zpráva. Uživatel je požádán o další vstup a program pokračuje v normálním provádění.

   ![Konečný výsledek po změnách](./media/calculator-final-verification.gif "Konečný výsledek po změnách")

   > [!Note]
   > Při úpravě kódu v režimu ladění existuje riziko, že kód bude zastaralý. K tomu dochází, když ladicí program stále běží váš starý kód a ještě jej neaktualizoval se změnami. Ladicí program se objeví dialogové okno, které vás informuje, když k tomu dojde. Někdy může být nutné stisknout **klávesu F5,** abyste aktualizovali spouštěný kód. Zejména pokud provedete změnu uvnitř funkce, zatímco bod spuštění je uvnitř této funkce, budete muset vystoupit z funkce, pak zpět do ní znovu získat aktualizovaný kód. Pokud to z nějakého důvodu nefunguje a zobrazí se chybová zpráva, můžete přestat ladit kliknutím na červený čtverec v panelu nástrojů pod nabídkami v horní části rozhraní IDE a poté znovu začít ladit zadáním **klávesy F5** nebo výběrem zelené šipky "play" vedle tlačítka stop na panelu nástrojů.

   > Principy klávesových zkratek Spustit a ladění
   >
   > - **F5** (nebo **Ladění** > **Start Ladění**) spustí relaci ladění, pokud jeden ještě není aktivní a spustí program, dokud je přístupná zarážka nebo program potřebuje vstup uživatele. Pokud není potřeba žádný vstup uživatele a není k dispozici žádná zarážka pro přístup, program se ukončí a okno konzoly se po dokončení programu zavře samo. Pokud máte něco jako "Hello World" program ke spuštění, použijte **Ctrl + F5** nebo nastavit zarážku před zadáním **F5,** aby okno otevřené.
   > - **Ctrl+F5** (nebo **Ladění** > **Start bez ladění)** spustí aplikaci bez přepnutí do režimu ladění. To je o něco rychlejší než ladění a okno konzoly zůstane otevřené po dokončení provádění programu.
   > - **F10** (známé jako **Krok přes)** umožňuje iteraci prostřednictvím kódu, řádek po řádku a vizualizovat, jak je kód spuštěn a jaké hodnoty proměnných jsou v každém kroku provádění.
   > - **F11** (známý jako **Krok do**) funguje podobně jako **Krok přes**, s výjimkou kroků do všech funkcí volaných na řádku provádění. Pokud například spuštěná linka volá funkci, stisknutím **klávesy F11** přesunete ukazatel do těla funkce, takže můžete sledovat kód funkce, který se spouští, než se vrátíte na linku, na které jste začali. Stisknutím **klávesy F10** přes volání funkce a jen přesune na další řádek; volání funkce stále probíhá, ale program se nezastaví, aby vám ukázal, co dělá.

### <a name="close-the-app"></a>Zavření aplikace

- Pokud je stále spuštěná, zavřete okno konzoly pro aplikaci kalkulačky.

## <a name="the-finished-app"></a>Dokončená aplikace

Blahopřejeme! Dokončili jste kód pro aplikaci kalkulačky a vytvořili a ladili ho v sadě Visual Studio.

## <a name="next-steps"></a>Další kroky

[Další informace o Visual Studiu pro C++](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end
