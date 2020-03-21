---
title: Vytvoření projektu aplikace konzoly C++
description: Vytvoření aplikace konzoly pro Hello World a aplikace kalkulačky v vizuáluC++
ms.custom: mvc
ms.date: 08/19/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 27522a6960546dc935ea3d9bce974eb36789c0aa
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079293"
---
# <a name="create-a-c-console-app-project"></a>Vytvoření projektu aplikace konzoly C++

::: moniker range=">=vs-2019"

Obvyklým výchozím bodem C++ programátora je "Hello, World!" aplikace, která běží na příkazovém řádku. To je to, co vytvoříte v aplikaci Visual Studio v tomto článku, a pak budeme pokračovat na něco náročnějšího: aplikace kalkulačky.

## <a name="prerequisites"></a>Předpoklady

- Aplikace Visual Studio s  **C++ vývojem pro stolní počítače** je nainstalovaná a spuštěná v počítači. Pokud ještě není nainstalován, přečtěte si [téma C++ instalace podpory v aplikaci Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Vytvoření projektu aplikace

Visual Studio používá *projekty* k uspořádání kódu pro aplikaci a *řešení* pro uspořádání vašich projektů. Projekt obsahuje všechny možnosti, konfigurace a pravidla používaná k vytváření aplikací. Spravuje také vztah mezi všechny projektové soubory a soubory s externí. Chcete-li vytvořit aplikaci, nejprve vytvořte nový projekt a řešení.

1. Pokud jste právě spustili aplikaci Visual Studio, zobrazí se dialogové okno Visual Studio 2019. Začněte tím, že kliknete na **vytvořit nový projekt** .

   ![Úvodní dialogové okno sady Visual Studio 2019](./media/calc-vs2019-initial-dialog.png "Úvodní dialogové okno sady Visual Studio 2019")

   V opačném případě na panelu nabídek v aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt**. Otevře se okno **vytvořit nový projekt** .

1. V seznamu šablon projektu zvolte možnost **aplikace konzoly**a pak klikněte na tlačítko **Další**.

   ![Zvolit šablonu konzolové aplikace](./media/calc-vs2019-choose-console-app.png "Zvolit šablonu konzolové aplikace")

   > [!Important]
   > Ujistěte se, že jste C++ zvolili verzi šablony **aplikace konzoly** . Má značky **C++** , **Windows**a **Console** a ikona obsahuje "+ +" v rohu.

1. V dialogovém okně **Konfigurovat nový projekt** vyberte pole **název projektu** upravit, pojmenujte nový projekt *CalculatorTutorial*a pak zvolte **vytvořit**.

   ![Pojmenujte projekt v dialogu Konfigurovat nový projekt.](./media/calc-vs2019-name-your-project.png "Pojmenujte projekt v dialogu Konfigurovat nový projekt.")

   Vytvoří se C++ prázdná Konzolová aplikace pro Windows. Konzolové aplikace používají okno konzoly systému Windows k zobrazení výstupu a přijetí vstupu uživatele. V aplikaci Visual Studio se otevře okno editoru a zobrazí se generovaný kód:

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

## <a name="verify-that-your-new-app-builds-and-runs"></a>Ověřte, že se nová aplikace sestavuje a spustí.

Šablona pro novou konzolovou aplikaci pro Windows vytvoří jednoduchou C++ aplikaci "Hello World". V tomto okamžiku vidíte, jak aplikace Visual Studio sestavuje a spouští aplikace, které vytvoříte přímo z rozhraní IDE.

1. Chcete-li sestavit projekt, v nabídce **sestavení** klikněte na příkaz **Sestavit řešení** . V okně **výstup** se zobrazí výsledky procesu sestavení.

   ![Sestavení projektu](./media/calc-vs2019-build-your-project.png "Sestavení projektu")

1. Chcete-li spustit kód, na panelu nabídek vyberte možnost **ladit**, **Spustit bez ladění**.

   ![Spustit projekt](./media/calc-vs2019-hello-world-console.png "Spustit projekt")

   Otevře se okno konzoly a pak se spustí vaše aplikace. Když spustíte konzolovou aplikaci v aplikaci Visual Studio, spustí váš kód a pak vytiskne "stisknutím libovolné klávesy zavřete toto okno. . . abyste měli možnost zobrazit výstup. Blahopřejeme! Vytvořili jste první "Hello, World!" Konzolová aplikace v aplikaci Visual Studio!

1. Stisknutím klávesy zavřete okno konzoly a vraťte se do sady Visual Studio.

Teď máte nástroje pro sestavení a spuštění vaší aplikace po každé změně, abyste ověřili, že kód pořád funguje podle očekávání. Později vám ukážeme, jak ji ladit, pokud ne.

## <a name="edit-the-code"></a>Upravit kód

Teď kód v této šabloně převeďte do aplikace kalkulačky.

1. V souboru *CalculatorTutorial. cpp* upravte kód tak, aby odpovídal následujícímu příkladu:

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

   > Princip kódu:
   >
   > - Příkazy `#include` umožňují odkazování na kód nacházející se v jiných souborech. V některých případech se může zobrazit název souboru uzavřený lomenými závorkami ( **\<\>** ). jindy je tato možnost obklopena uvozovkami (" **"** ). Obecně platí, že při odkazování na C++ standardní knihovnu se používají lomené závorky, zatímco se používají uvozovky pro jiné soubory.
   > - `using namespace std;` řádek instruuje kompilátor, aby čekal na použití C++ standardní knihovny v tomto souboru. Bez tohoto řádku by mělo být každé klíčové slovo z knihovny před `std::`, aby se poznamenal jeho obor. Například bez tohoto řádku by se měly všechny odkazy na `cout` zapsat jako `std::cout`. Příkaz `using` je přidán, aby byl kód lépe čistý.
   > - Klíčové slovo `cout` slouží k tisku do standardního výstupu v C++. Operátor **\<\<** instruuje kompilátor, aby odesílal jakékoli informace na standardní výstup.
   > - Klíčové slovo **endl** je jako klávesa ENTER. ukončí řádek a přesune kurzor na další řádek. Je vhodnější umístit `\n` do řetězce (obsaženého ""), aby to provedlo stejnou věc, protože `endl` vždy vyprázdní vyrovnávací paměť a může snížit výkon programu, ale vzhledem k tomu, že se jedná o velmi malou aplikaci, `endl` místo toho použít pro lepší čitelnost.
   > - Všechny C++ příkazy musí končit středníkem a všechny C++ aplikace musí obsahovat funkci `main()`. Tato funkce je to, co program spouští na začátku. Veškerý kód musí být přístupný z `main()`, aby jej bylo možné použít.

1. Soubor uložíte tak, že zadáte **CTRL + S**nebo v horní části rozhraní IDE kliknete na ikonu **Uložit** , na panelu nástrojů pod řádkem nabídek.

1. Chcete-li spustit aplikaci, stiskněte klávesy **CTRL + F5** nebo přejděte do nabídky **ladění** a zvolte možnost **Spustit bez ladění**. Mělo by se zobrazit okno konzoly, které zobrazuje text zadaný v kódu.

1. Až skončíte, zavřete okno konzoly.

## <a name="add-code-to-do-some-math"></a>Přidejte kód, abyste mohli provádět některé matematické

Je čas přidat nějakou matematickou logiku.

### <a name="to-add-a-calculator-class"></a>Přidání třídy kalkulačky

1. Přejděte do nabídky **projekt** a vyberte možnost **Přidat třídu**. V poli **název třídy** upravte zadejte *Kalkulačka*. Zvolte **OK**. Do projektu se přidají dva nové soubory. Chcete-li uložit všechny změněné soubory najednou, stiskněte klávesy **CTRL + SHIFT + S**. Jedná se o klávesovou zkratku pro **soubor** > **Uložit vše**. K dispozici je také tlačítko panelu nástrojů pro možnost **Uložit vše**– ikona dvou disket, která se nachází vedle tlačítka **Uložit** . Obecně platí, že dobrým zvykem je **ukládat všechny** často, takže při ukládání nenajdete žádné soubory.

   ![Vytvoření třídy kalkulačky](./media/calc-vs2019-create-calculator-class.png "Vytvoření třídy kalkulačky")

   Třída je jako podrobný plán pro objekt, který něco dělá. V tomto případě definujeme kalkulačku a to, jak má fungovat. Průvodce **přidáním třídy** , který jste použili nad vytvořenými soubory. h a. cpp, které mají stejný název jako třída. Úplný seznam souborů projektu můžete zobrazit v okně **Průzkumník řešení** , které je viditelné na straně integrovaného vývojového prostředí (IDE). Pokud okno není viditelné, můžete ho otevřít z řádku nabídek: zvolit **zobrazení** > **Průzkumník řešení**.

   ![Průzkumník řešení](./media/calc-vs2019-solution-explorer.png "Průzkumník řešení")

   Nyní byste měli mít v editoru otevřené tři karty: *CalculatorTutorial. cpp*, *Kalkulačka. h*a *Kalkulačka. cpp*. Pokud jeden z nich omylem zavřete, můžete ho znovu otevřít dvojitým kliknutím v okně **Průzkumník řešení** .

1. V programu **Kalkulačka. h**odeberte `Calculator();` a `~Calculator();` vygenerované řádky, protože je nebudete potřebovat. Dále přidejte následující řádek kódu, aby soubor byl nyní vypadat takto:

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
   > - Řádek, který jste přidali, deklaruje novou funkci nazvanou `Calculate`, kterou použijeme ke spouštění matematických operací pro sčítání, odčítání, násobení a dělení.
   > - C++kód je uspořádán do souborů *hlaviček* (. h) a *zdrojových* souborů (. cpp). Několik dalších přípon souborů je podporováno různými kompilátory, ale jedná se o ty, kterých se dozvíte. Funkce a proměnné jsou obvykle *deklarovány*, to znamená, že jsou zadány název a typ, v hlavičkových souborech a *implementovány*nebo předány definici ve zdrojových souborech. Chcete-li získat přístup ke kódu definovanému v jiném souboru, můžete použít `#include "filename.h"`, kde ' filename. h ' je název souboru, který deklaruje proměnné nebo funkce, které chcete použít.
   > - Dva řádky, které jste odstranili, byly deklarovány jako *konstruktor* a *destruktor* pro třídu. Pro jednoduchou třídu, jako je tato, ji kompilátor vytvoří za vás, přičemž jejich použití jsou nad rámec tohoto kurzu.
   > - Je vhodné organizovat kód do různých souborů na základě toho, co dělá, takže je snadné najít kód, který potřebujete později. V našem případě jsme definovali třídu `Calculator` odděleně od souboru obsahujícího funkci `main()`, ale v `main()`plánujeme odkazovat na třídu `Calculator`.

1. V části `Calculate`se zobrazí zelená vlnovka. Je to proto, že jsme v souboru. cpp nedefinovali funkci `Calculate`. Najeďte myší na slovo, klikněte na žárovky (v tomto případě Screwdriver), který se zobrazí, a **v kalkulačce. cpp vyberte vytvořit definici pro ' vypočítat '** .

   ![Vytvořit definici výpočtu](./media/calc-vs2019-create-definition.png "Vytvořit definici výpočtu")

   Zobrazí se automaticky otevírané okno, které vám nabídne náhled změny kódu provedené v jiném souboru. Kód byl přidán do *kalkulačky. cpp*.

   ![Místní okno s definicí vypočítat](./media/calc-vs2019-pop-up-definition.png "Místní okno s definicí vypočítat")

   V současné době pouze vrátí 0,0. To teď změníme. Stisknutím klávesy **ESC** zavřete automaticky otevírané okno.

1. V okně editoru přepněte na soubor *kalkulačky. cpp* . Odeberte oddíly `Calculator()` a `~Calculator()` (stejně jako v souboru. h) a přidejte následující kód do `Calculate()`:

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
   > - Funkce `Calculate` spotřebovává číslo, operátor a druhé číslo a poté provede požadovanou operaci s čísly.
   > - Příkaz switch ověří, který operátor byl zadán a provede pouze případ odpovídající této operaci. Výchozí: Case je záložní pro případ, že uživatel zadá operátor, který není přijat, takže program nebude přerušen. Obecně je nejlepší zpracovávat neplatný vstup uživatele efektivněji, ale toto je nad rámec tohoto kurzu.
   > - Klíčové slovo `double` označuje typ čísla, který podporuje desetinná místa. Kalkulačka tak může zpracovat desítkové matematické i celočíselné matematické hodnoty. Funkce `Calculate` je vyžadována, aby vždy vracela takové číslo z důvodu `double` na začátku kódu (označuje návratový typ funkce), což je důvod, proč vracíme 0,0 i ve výchozím případu.
   > - Soubor. h deklaruje *prototyp*funkce, který instruuje kompilátor dopředu, jaké parametry vyžaduje a jaký návratový typ, který má z něj očekávat. Soubor. cpp obsahuje všechny podrobnosti o implementaci funkce.

Pokud v tomto okamžiku sestavíte a znovu spustíte kód, bude i nadále ukončen po žádosti o operaci, která má být provedena. V dalším kroku upravíte funkci `main`, aby se provede několik výpočtů.

### <a name="to-call-the-calculator-class-member-functions"></a>Volání funkcí členů třídy kalkulačky

1. Teď aktualizujeme funkci `main` v *CalculatorTutorial. cpp*:

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
   > - Vzhledem C++ k tomu, že se programy vždy spouštějí ve funkci `main()`, musíme odtud zavolat náš další kód, takže je potřeba `#include` příkaz.
   > - Některé počáteční proměnné `x`, `y`, `oper`a `result` jsou deklarovány pro uložení prvního čísla, druhého čísla, operátoru a konečného výsledku v uvedeném pořadí. Je vždy vhodné jim poskytnout některé počáteční hodnoty, aby nedocházelo k nedefinovanému chování, což znamená to, co se děje.
   > - `Calculator c;` řádek deklaruje objekt nazvaný "c" jako instanci `Calculator` třídy. Samotná třída je jenom podrobný plán, jak fungují kalkulačky. objekt je konkrétní kalkulačka, která je matematické.
   > - Příkaz `while (true)` je smyčka. Kód uvnitř smyčky pokračuje v provádění a znovu, dokud podmínka uvnitř `()` drží hodnotu true. Vzhledem k tomu, že je tato podmínka jednoduše uvedená jako `true`, je vždycky true, takže se smyčka spouští trvale. Chcete-li program ukončit, uživatel musí ručně zavřít okno konzoly. V opačném případě bude program vždycky čekat na nový vstup.
   > - Klíčové slovo `cin` slouží k přijetí vstupu od uživatele. Tento vstupní datový proud je dostatečně automatický pro zpracování řádku textu zadaného v okně konzoly a jeho umístění do každé z uvedených proměnných, v pořadí, za předpokladu, že vstup uživatele odpovídá požadované specifikaci. Tento řádek lze upravit tak, aby přijímal různé typy vstupu, například více než dvě čísla, i když by mohla být funkce `Calculate()` také aktualizována, aby bylo možné tuto funkci zpracovat.
   > - Výraz `c.Calculate(x, oper, y);` volá dříve definovanou funkci `Calculate` a zadá zadané vstupní hodnoty. Funkce pak vrátí číslo, které je uloženo v `result`.
   > - Nakonec se `result` vytiskne do konzoly, takže se uživateli zobrazí výsledek výpočtu.

### <a name="build-and-test-the-code-again"></a>Sestavit a otestovat kód znovu

Nyní je čas otestovat program znovu, abyste se ujistili, že vše funguje správně.

1. Stisknutím **kombinace kláves CTRL + F5** znovu sestavte a spusťte aplikaci.

1. Zadejte `5 + 5`a stiskněte klávesu **ENTER**. Ověřte, že je výsledek 10.

   ![Výsledek 5 + 5](./media/calc-vs2019-five-plus-five.png "Výsledek 5 + 5")

## <a name="debug-the-app"></a>Ladění aplikace

Vzhledem k tomu, že uživatel je zdarma psát do okna konzoly, je nutné se ujistit, že kalkulačka zpracovává určitý vstup podle očekávání. Místo spuštění programu je možné ho místo toho ladit, takže můžeme zkontrolovat, co podrobně dělá, a krok za krokem.

### <a name="to-run-the-app-in-the-debugger"></a>Spuštění aplikace v ladicím programu

1. Nastavte zarážku na `result = c.Calculate(x, oper, y);`ovém řádku hned po výzvě k zadání vstupu uživatele. Chcete-li nastavit zarážku, klikněte na tlačítko vedle čáry v šedém svislém pruhu podél levého okraje okna editoru. Zobrazí se červená tečka.

   ![Nastavit zarážku](./media/calc-vs2019-set-breakpoint.png "Nastavení zarážky")

   Nyní když program ladíme, vždy pozastaví provádění na daném řádku. Již máme hrubý nápad, který program funguje pro jednoduché případy. Vzhledem k tomu, že nechcete pokaždé pozastavit běh pokaždé, provedeme podmíněný zarážku.

1. Pravým tlačítkem myši klikněte na červenou tečku, která představuje zarážku, a vyberte **podmínky**. Do pole pro úpravy podmínky zadejte `(y == 0) && (oper == '/')`. Až budete hotovi, klikněte na tlačítko **Zavřít** . Podmínka se uloží automaticky.

   ![Nastavení podmíněné zarážky](./media/calc-vs2019-conditional-breakpoint.png "Nastavení podmíněné zarážky")

   Nyní pozastavíme provádění na zarážce konkrétně v případě, že došlo k pokusu o dělení 0.

1. Chcete-li ladit program, stiskněte klávesu **F5**nebo zvolte tlačítko **místní ladicí program systému Windows** , které má ikonu zelené šipky. Pokud v aplikaci konzoly zadáte něco jako "5-0", program se chová normálně a zůstane spuštěný. Pokud však zadáte "10/0", pozastaví se na zarážce. Mezi operátor a čísla můžete dokonce vložit libovolný počet mezer: `cin` je dostatečně inteligentní, aby bylo možné správně analyzovat vstup.

   ![Pozastavit na podmíněné zarážce](./media/calc-vs2019-debug-breakpoint.png "Pozastavit na podmíněné zarážce")

### <a name="useful-windows-in-the-debugger"></a>Užitečná okna v ladicím programu

Kdykoli budete ladit kód, můžete si všimnout, že se zobrazí některá nová okna. Tato okna můžou pomáhat s vaším prostředím pro ladění. Podívejte se na okno **Automatické** hodnoty. Okno **Automatické** hodnoty zobrazuje aktuální hodnoty proměnných, které byly použity alespoň na tři řádky před a až do aktuálního řádku. Chcete-li zobrazit všechny proměnné z této funkce, přepněte do okna **místní** hodnoty. Hodnoty těchto proměnných můžete v průběhu ladění skutečně upravovat, abyste viděli, jaký má vliv na program. V takovém případě je zadáte samostatně.

   ![Okno místních hodnot](./media/calc-vs2019-debug-locals.png "Okno místních hodnot")

Můžete také umístit ukazatel myši na proměnné v samotném kódu, abyste viděli jejich aktuální hodnoty, kde je provádění aktuálně pozastaveno. Ujistěte se, že je okno editoru aktivní, a to tak, že na něj kliknete nejdřív.

   ![Najetím myší zobrazíte aktuální hodnoty proměnných.](./media/calc-vs2019-hover-tooltip.png "Najetím myší zobrazíte aktuální hodnoty proměnných.")

### <a name="to-continue-debugging"></a>Pokračování v ladění

1. Žlutý řádek na levé straně znázorňuje aktuální bod provádění. Aktuální řádek zavolá `Calculate`, takže stisknutím klávesy **F11** se **zajděte do** funkce. V těle funkce `Calculate` zjistíte sami sebe. Buďte opatrní při **krokování**; Pokud to uděláte příliš daleko, může dorazit spoustu času. Přejde do libovolného kódu, který použijete na řádku, na kterém se nacházíte, včetně standardních funkcí knihovny.

1. Teď, když je bod spuštění na začátku `Calculate` funkce, stisknutím klávesy **F10** přejdete na další řádek v provádění programu. **F10** se také označuje jako **krok za krokem**. Můžete použít **Krok** nahoru pro přechod mezi řádky a spojnici, aniž byste museli zobrazit podrobnosti o tom, co se v každé části řádku objevuje. Obecně byste měli místo **kroku into**použít **Krok** , pokud nechcete podrobně do kódu, který je volán jinam (jako při přístupu k textu `Calculate`).

1. Pokračujte v používání **klávesy F10** , abyste mohli **Krokovat** s každým řádkem, dokud se nevrátíte do funkce `main()` v druhém souboru a zastavte se na řádku `cout`.

   Vypadá to, že program dělá, co je očekávané: přijímá první číslo a rozděluje ho druhým. Na `cout` řádku najeďte myší na proměnnou `result` nebo se podívejte na `result` v okně **Automatické** hodnoty. Uvidíte, že jeho hodnota je uvedena jako "INF", což nevypadá správně, takže ji Opravme. `cout` řádek právě vypisuje libovolnou hodnotu, která je uložena v `result`, takže když postupně provedete další **řádek, zobrazí se okno**konzoly:

   ![Výsledek dělení nulou](./media/calc-vs2019-divide-by-zero-fail.png "Výsledek dělení nulou")

   K tomuto výsledku dochází, protože dělení nulou není definováno, takže program nemá číselnou odpověď na požadovanou operaci.

### <a name="to-fix-the-divide-by-zero-error"></a>Oprava chyby "dělení nulou"

Podíváme se, aby dělení nulou bez problémů, takže uživatel může pochopit problém.

1. Proveďte následující změny v *CalculatorTutorial. cpp*. (Program můžete nechat spuštěný při úpravách, a to díky funkci ladicího programu s názvem **Upravit a pokračovat**):

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

1. Nyní stiskněte klávesu **F5** . Provádění programu pokračuje všemi způsoby, dokud se nemusíte pozastavit, aby pomohlo zadání uživatele. Zadejte `10 / 0` znovu. Nyní je vytištěna užitečnější zpráva. Uživatel je vyzván k zadání dalšího vstupu a program pokračuje v normálním provádění.

   ![Konečný výsledek po změně](./media/calc-vs2019-final-verification.png "Konečný výsledek po změně")

   > [!Note]
   > Při úpravách kódu v režimu ladění existuje riziko, že se kód stane zastaralým. K tomu dojde v případě, že ladicí program stále používá starý kód a ještě neaktualizoval se změnami. Ladicí program zobrazí dialogové okno s informací o tom, kdy k tomu dojde. Někdy může být nutné stisknout klávesu **F5** pro aktualizaci spouštěného kódu. Zejména pokud provedete změnu uvnitř funkce, zatímco je bod provádění uvnitř této funkce, budete muset krok převzít z funkce a následně zpátky do ní získat aktualizovaný kód. Pokud to z nějakého důvodu nefunguje a zobrazí se chybová zpráva, můžete ladění zastavit kliknutím na červené čtverce na panelu nástrojů v nabídce v horní části rozhraní IDE a pak znovu spustit ladění, a to tak, že zadáte **F5** nebo kliknutím na zelenou šipku "Play" vedle tlačítka zastavit na panelu nástrojů.

   > Principy klávesových zkratek Run a Debug
   >
   > - **F5** (nebo **ladění** > **Spustit ladění**) spustí ladicí relaci, pokud již jedna není aktivní, a spustí program, dokud nebude dosaženo zarážky nebo když program potřebuje vstup uživatele. Pokud není nutný žádný vstup uživatele a není k dispozici žádná zarážka, program se ukončí a okno konzoly se po dokončení programu zavře. Pokud máte něco podobného jako spuštění programu "Hello World", použijte **CTRL + F5** nebo nastavte zarážku před zadáním klávesy **F5** , aby okno zůstalo otevřené.
   > - **CTRL + F5** (nebo **ladění** > **Spustit bez ladění**) spustí aplikaci bez přechodu do režimu ladění. Toto je mírně rychlejší než ladění a okno konzoly zůstane otevřené, i když program dokončí provádění.
   > - **F10** (označované jako **Krokovat**s přečtením) umožňuje iterovat kód, řádek po řádku a vizualizovat, jak se kód spouští a jaké hodnoty proměnných jsou v každém kroku provádění.
   > - Klávesa **F11** (označovaná jako **Krok do**) funguje podobně jako při **prvním kroku**, s výjimkou kroků na jakékoli funkce, které jsou volány na řádku provádění. Například pokud je řádek spouštěn voláním funkce, stisknutí klávesy **F11** přesune ukazatel na tělo funkce, aby bylo možné sledovat spouštěný kód funkce před návratem k řádku, na kterém jste začali. Stisknutí klávesy **F10** nad voláním funkce a pouhým přechodem na další řádek; k volání funkce stále dochází, ale program se nezastaví, aby vám ukázal, co dělá.

### <a name="close-the-app"></a>Zavřít aplikaci

- Pokud je pořád spuštěný, zavřete okno konzoly pro aplikaci kalkulačky.

## <a name="the-finished-app"></a>Dokončená aplikace

Blahopřejeme! Dokončili jste kód pro aplikaci kalkulačky a vytvořili jste ho a rozpnuli ho v aplikaci Visual Studio.

## <a name="next-steps"></a>Další kroky

[Další informace o aplikaci Visual Studio proC++](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end

::: moniker range="<vs-2019"

Obvyklým výchozím bodem C++ programátora je "Hello, World!" aplikace, která běží na příkazovém řádku. To je to, co vytvoříte v aplikaci Visual Studio v tomto článku, a pak budeme pokračovat na něco náročnějšího: aplikace kalkulačky.

## <a name="prerequisites"></a>Předpoklady

- Aplikace Visual Studio s  **C++ vývojem pro stolní počítače** je nainstalovaná a spuštěná v počítači. Pokud ještě není nainstalován, přečtěte si [téma C++ instalace podpory v aplikaci Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Vytvoření projektu aplikace

Visual Studio používá *projekty* k uspořádání kódu pro aplikaci a *řešení* pro uspořádání vašich projektů. Projekt obsahuje všechny možnosti, konfigurace a pravidla používaná k vytváření aplikací. Spravuje také vztah mezi všechny projektové soubory a soubory s externí. Chcete-li vytvořit aplikaci, nejprve vytvořte nový projekt a řešení.

1. Na panelu nabídek v aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt**. Otevře se okno **Nový projekt** .

2. Na levém bočním panelu se ujistěte, že je vybraná možnost **Visual C++**  . V centru vyberte **Konzolová aplikace systému Windows**.

3. V dolní části **název** zadejte název nového projektu *CalculatorTutorial*a pak zvolte **OK**.

   ![Dialogové okno Nový projekt](./media/calculator-new-project-dialog.png "Dialogové okno Nový projekt")

   Vytvoří se C++ prázdná Konzolová aplikace pro Windows. Konzolové aplikace používají okno konzoly systému Windows k zobrazení výstupu a přijetí vstupu uživatele. V aplikaci Visual Studio se otevře okno editoru a zobrazí se generovaný kód:

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

## <a name="verify-that-your-new-app-builds-and-runs"></a>Ověřte, že se nová aplikace sestavuje a spustí.

Šablona pro novou konzolovou aplikaci pro Windows vytvoří jednoduchou C++ aplikaci "Hello World". V tomto okamžiku vidíte, jak aplikace Visual Studio sestavuje a spouští aplikace, které vytvoříte přímo z rozhraní IDE.

1. Chcete-li sestavit projekt, v nabídce **sestavení** klikněte na příkaz **Sestavit řešení** . V okně **výstup** se zobrazí výsledky procesu sestavení.

   ![Sestavení projektu](./media/calculator-initial-build-output.png "Sestavení projektu")

1. Chcete-li spustit kód, na panelu nabídek vyberte možnost **ladit**, **Spustit bez ladění**.

   ![Spustit projekt](./media/calculator-hello-world-console.png "Spustit projekt")

   Otevře se okno konzoly a pak se spustí vaše aplikace. Když spustíte konzolovou aplikaci v aplikaci Visual Studio, spustí se váš kód a potom se zobrazí zpráva pro pokračování stiskněte libovolnou klávesu. . . abyste měli možnost zobrazit výstup. Blahopřejeme! Vytvořili jste první "Hello, World!" Konzolová aplikace v aplikaci Visual Studio!

1. Stisknutím klávesy zavřete okno konzoly a vraťte se do sady Visual Studio.

Teď máte nástroje pro sestavení a spuštění vaší aplikace po každé změně, abyste ověřili, že kód pořád funguje podle očekávání. Později vám ukážeme, jak ji ladit, pokud ne.

## <a name="edit-the-code"></a>Upravit kód

Teď kód v této šabloně převeďte do aplikace kalkulačky.

1. V souboru *CalculatorTutorial. cpp* upravte kód tak, aby odpovídal následujícímu příkladu:

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

   > Princip kódu:
   >
   > - Příkazy `#include` umožňují odkazování na kód nacházející se v jiných souborech. V některých případech se může zobrazit název souboru uzavřený lomenými závorkami ( **\<\>** ). jindy je tato možnost obklopena uvozovkami (" **"** ). Obecně platí, že při odkazování na C++ standardní knihovnu se používají lomené závorky, zatímco se používají uvozovky pro jiné soubory.
   > - `#include "pch.h"` (nebo v rámci sady Visual Studio 2017 a starší, `#include "stdafx.h"`) odkazuje na něco známého jako Předkompilovaná hlavička. Ty jsou často používány profesionálními programátory ke zlepšení časů kompilace, ale překračují rozsah tohoto kurzu.
   > - `using namespace std;` řádek instruuje kompilátor, aby čekal na použití C++ standardní knihovny v tomto souboru. Bez tohoto řádku by mělo být každé klíčové slovo z knihovny před `std::`, aby se poznamenal jeho obor. Například bez tohoto řádku by se měly všechny odkazy na `cout` zapsat jako `std::cout`. Příkaz `using` je přidán, aby byl kód lépe čistý.
   > - Klíčové slovo `cout` slouží k tisku do standardního výstupu v C++. Operátor **\<\<** instruuje kompilátor, aby odesílal jakékoli informace na standardní výstup.
   > - Klíčové slovo **endl** je jako klávesa ENTER. ukončí řádek a přesune kurzor na další řádek. Je vhodnější umístit `\n` do řetězce (obsaženého ""), aby to provedlo stejnou věc, protože `endl` vždy vyprázdní vyrovnávací paměť a může snížit výkon programu, ale vzhledem k tomu, že se jedná o velmi malou aplikaci, `endl` místo toho použít pro lepší čitelnost.
   > - Všechny C++ příkazy musí končit středníkem a všechny C++ aplikace musí obsahovat funkci `main()`. Tato funkce je to, co program spouští na začátku. Veškerý kód musí být přístupný z `main()`, aby jej bylo možné použít.

1. Soubor uložíte tak, že zadáte **CTRL + S**nebo v horní části rozhraní IDE kliknete na ikonu **Uložit** , na panelu nástrojů pod řádkem nabídek.

1. Chcete-li spustit aplikaci, stiskněte klávesy **CTRL + F5** nebo přejděte do nabídky **ladění** a zvolte možnost **Spustit bez ladění**. Pokud se zobrazí automaticky otevírané okno s oznámením, že **Tento projekt je zastaralý**, můžete zvolit možnost **znovu nezobrazovat toto dialogové okno**a potom kliknutím na **tlačítko Ano** sestavit aplikaci. Mělo by se zobrazit okno konzoly, které zobrazuje text zadaný v kódu.

   ![Sestavení a spuštění aplikace](./media/calculator-first-launch.gif "Sestavení a spuštění aplikace")

1. Až skončíte, zavřete okno konzoly.

## <a name="add-code-to-do-some-math"></a>Přidejte kód, abyste mohli provádět některé matematické

Je čas přidat nějakou matematickou logiku.

### <a name="to-add-a-calculator-class"></a>Přidání třídy kalkulačky

1. Přejděte do nabídky **projekt** a vyberte možnost **Přidat třídu**. V poli **název třídy** upravte zadejte *Kalkulačka*. Zvolte **OK**. Do projektu se přidají dva nové soubory. Chcete-li uložit všechny změněné soubory najednou, stiskněte klávesy **CTRL + SHIFT + S**. Jedná se o klávesovou zkratku pro **soubor** > **Uložit vše**. K dispozici je také tlačítko panelu nástrojů pro možnost **Uložit vše**– ikona dvou disket, která se nachází vedle tlačítka **Uložit** . Obecně platí, že dobrým zvykem je **ukládat všechny** často, takže při ukládání nenajdete žádné soubory.

   ![Vytvoření třídy kalkulačky](./media/calculator-create-class.gif "Vytvoření třídy kalkulačky")

   Třída je jako podrobný plán pro objekt, který něco dělá. V tomto případě definujeme kalkulačku a to, jak má fungovat. Průvodce **přidáním třídy** , který jste použili nad vytvořenými soubory. h a. cpp, které mají stejný název jako třída. Úplný seznam souborů projektu můžete zobrazit v okně **Průzkumník řešení** , které je viditelné na straně integrovaného vývojového prostředí (IDE). Pokud okno není viditelné, můžete ho otevřít z řádku nabídek: zvolit **zobrazení** > **Průzkumník řešení**.

   ![Průzkumník řešení](./media/calculator-solution-explorer.png "Průzkumník řešení")

   Nyní byste měli mít v editoru otevřené tři karty: *CalculatorTutorial. cpp*, *Kalkulačka. h*a *Kalkulačka. cpp*. Pokud jeden z nich omylem zavřete, můžete ho znovu otevřít dvojitým kliknutím v okně **Průzkumník řešení** .

1. V programu **Kalkulačka. h**odeberte `Calculator();` a `~Calculator();` vygenerované řádky, protože je nebudete potřebovat. Dále přidejte následující řádek kódu, aby soubor byl nyní vypadat takto:

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
   > - Řádek, který jste přidali, deklaruje novou funkci nazvanou `Calculate`, kterou použijeme ke spouštění matematických operací pro sčítání, odčítání, násobení a dělení.
   > - C++kód je uspořádán do souborů *hlaviček* (. h) a *zdrojových* souborů (. cpp). Několik dalších přípon souborů je podporováno různými kompilátory, ale jedná se o ty, kterých se dozvíte. Funkce a proměnné jsou obvykle *deklarovány*, to znamená, že jsou zadány název a typ, v hlavičkových souborech a *implementovány*nebo předány definici ve zdrojových souborech. Chcete-li získat přístup ke kódu definovanému v jiném souboru, můžete použít `#include "filename.h"`, kde ' filename. h ' je název souboru, který deklaruje proměnné nebo funkce, které chcete použít.
   > - Dva řádky, které jste odstranili, byly deklarovány jako *konstruktor* a *destruktor* pro třídu. Pro jednoduchou třídu, jako je tato, ji kompilátor vytvoří za vás, přičemž jejich použití jsou nad rámec tohoto kurzu.
   > - Je vhodné organizovat kód do různých souborů na základě toho, co dělá, takže je snadné najít kód, který potřebujete později. V našem případě jsme definovali třídu `Calculator` odděleně od souboru obsahujícího funkci `main()`, ale v `main()`plánujeme odkazovat na třídu `Calculator`.

1. V části `Calculate`se zobrazí zelená vlnovka. Je to proto, že jsme v souboru. cpp nedefinovali funkci `Calculate`. Najeďte myší na slovo, klikněte na žárovky, který se zobrazí, a **v kalkulačce. cpp vyberte vytvořit definici pro ' vypočítat '** . Zobrazí se automaticky otevírané okno, které vám nabídne náhled změny kódu provedené v jiném souboru. Kód byl přidán do *kalkulačky. cpp*.

   ![Vytvořit definici výpočtu](./media/calculator-create-definition.gif "Vytvořit definici výpočtu")

   V současné době pouze vrátí 0,0. To teď změníme. Stisknutím klávesy **ESC** zavřete automaticky otevírané okno.

1. V okně editoru přepněte na soubor *kalkulačky. cpp* . Odeberte oddíly `Calculator()` a `~Calculator()` (stejně jako v souboru. h) a přidejte následující kód do `Calculate()`:

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
   > - Funkce `Calculate` spotřebovává číslo, operátor a druhé číslo a poté provede požadovanou operaci s čísly.
   > - Příkaz switch ověří, který operátor byl zadán a provede pouze případ odpovídající této operaci. Výchozí: Case je záložní pro případ, že uživatel zadá operátor, který není přijat, takže program nebude přerušen. Obecně je nejlepší zpracovávat neplatný vstup uživatele efektivněji, ale toto je nad rámec tohoto kurzu.
   > - Klíčové slovo `double` označuje typ čísla, který podporuje desetinná místa. Kalkulačka tak může zpracovat desítkové matematické i celočíselné matematické hodnoty. Funkce `Calculate` je vyžadována, aby vždy vracela takové číslo z důvodu `double` na začátku kódu (označuje návratový typ funkce), což je důvod, proč vracíme 0,0 i ve výchozím případu.
   > - Soubor. h deklaruje *prototyp*funkce, který instruuje kompilátor dopředu, jaké parametry vyžaduje a jaký návratový typ, který má z něj očekávat. Soubor. cpp obsahuje všechny podrobnosti o implementaci funkce.

Pokud v tomto okamžiku sestavíte a znovu spustíte kód, bude i nadále ukončen po žádosti o operaci, která má být provedena. V dalším kroku upravíte funkci `main`, aby se provede několik výpočtů.

### <a name="to-call-the-calculator-class-member-functions"></a>Volání funkcí členů třídy kalkulačky

1. Teď aktualizujeme funkci `main` v *CalculatorTutorial. cpp*:

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
   > - Vzhledem C++ k tomu, že se programy vždy spouštějí ve funkci `main()`, musíme odtud zavolat náš další kód, takže je potřeba `#include` příkaz.
   > - Některé počáteční proměnné `x`, `y`, `oper`a `result` jsou deklarovány pro uložení prvního čísla, druhého čísla, operátoru a konečného výsledku v uvedeném pořadí. Je vždy vhodné jim poskytnout některé počáteční hodnoty, aby nedocházelo k nedefinovanému chování, což znamená to, co se děje.
   > - `Calculator c;` řádek deklaruje objekt nazvaný "c" jako instanci `Calculator` třídy. Samotná třída je jenom podrobný plán, jak fungují kalkulačky. objekt je konkrétní kalkulačka, která je matematické.
   > - Příkaz `while (true)` je smyčka. Kód uvnitř smyčky pokračuje v provádění a znovu, dokud podmínka uvnitř `()` drží hodnotu true. Vzhledem k tomu, že je tato podmínka jednoduše uvedená jako `true`, je vždycky true, takže se smyčka spouští trvale. Chcete-li program ukončit, uživatel musí ručně zavřít okno konzoly. V opačném případě bude program vždycky čekat na nový vstup.
   > - Klíčové slovo `cin` slouží k přijetí vstupu od uživatele. Tento vstupní datový proud je dostatečně automatický pro zpracování řádku textu zadaného v okně konzoly a jeho umístění do každé z uvedených proměnných, v pořadí, za předpokladu, že vstup uživatele odpovídá požadované specifikaci. Tento řádek lze upravit tak, aby přijímal různé typy vstupu, například více než dvě čísla, i když by mohla být funkce `Calculate()` také aktualizována, aby bylo možné tuto funkci zpracovat.
   > - Výraz `c.Calculate(x, oper, y);` volá dříve definovanou funkci `Calculate` a zadá zadané vstupní hodnoty. Funkce pak vrátí číslo, které je uloženo v `result`.
   > - Nakonec se `result` vytiskne do konzoly, takže se uživateli zobrazí výsledek výpočtu.

### <a name="build-and-test-the-code-again"></a>Sestavit a otestovat kód znovu

Nyní je čas otestovat program znovu, abyste se ujistili, že vše funguje správně.

1. Stisknutím **kombinace kláves CTRL + F5** znovu sestavte a spusťte aplikaci.

1. Zadejte `5 + 5`a stiskněte klávesu **ENTER**. Ověřte, že je výsledek 10.

   ![Výsledek 5 + 5](./media/calculator-five-plus-five.png "Výsledek 5 + 5")

## <a name="debug-the-app"></a>Ladění aplikace

Vzhledem k tomu, že uživatel je zdarma psát do okna konzoly, je nutné se ujistit, že kalkulačka zpracovává určitý vstup podle očekávání. Místo spuštění programu je možné ho místo toho ladit, takže můžeme zkontrolovat, co podrobně dělá, a krok za krokem.

### <a name="to-run-the-app-in-the-debugger"></a>Spuštění aplikace v ladicím programu

1. Nastavte zarážku na `result = c.Calculate(x, oper, y);`ovém řádku hned po výzvě k zadání vstupu uživatele. Chcete-li nastavit zarážku, klikněte na tlačítko vedle čáry v šedém svislém pruhu podél levého okraje okna editoru. Zobrazí se červená tečka.

   ![Nastavit zarážku](./media/calculator-set-breakpoint.gif "Nastavení zarážky")

   Nyní když program ladíme, vždy pozastaví provádění na daném řádku. Již máme hrubý nápad, který program funguje pro jednoduché případy. Vzhledem k tomu, že nechcete pokaždé pozastavit běh pokaždé, provedeme podmíněný zarážku.

1. Pravým tlačítkem myši klikněte na červenou tečku, která představuje zarážku, a vyberte **podmínky**. Do pole pro úpravy podmínky zadejte `(y == 0) && (oper == '/')`. Až budete hotovi, klikněte na tlačítko **Zavřít** . Podmínka se uloží automaticky.

   ![Nastavení podmíněné zarážky](./media/calculator-conditional-breakpoint.gif "Nastavení podmíněné zarážky")

   Nyní pozastavíme provádění na zarážce konkrétně v případě, že došlo k pokusu o dělení 0.

1. Chcete-li ladit program, stiskněte klávesu **F5**nebo zvolte tlačítko **místní ladicí program systému Windows** , které má ikonu zelené šipky. Pokud v aplikaci konzoly zadáte něco jako "5-0", program se chová normálně a zůstane spuštěný. Pokud však zadáte "10/0", pozastaví se na zarážce. Mezi operátor a čísla můžete dokonce vložit libovolný počet mezer. `cin` je dostatečně inteligentní, aby bylo možné správně analyzovat vstup.

   ![Pozastavit na podmíněné zarážce](./media/calculator-debug-conditional.gif "Pozastavit na podmíněné zarážce")

### <a name="useful-windows-in-the-debugger"></a>Užitečná okna v ladicím programu

Kdykoli budete ladit kód, můžete si všimnout, že se zobrazí některá nová okna. Tato okna můžou pomáhat s vaším prostředím pro ladění. Podívejte se na okno **Automatické** hodnoty. Okno **Automatické** hodnoty zobrazuje aktuální hodnoty proměnných, které byly použity alespoň na tři řádky před a až do aktuálního řádku.

   ![Okno Automatické hodnoty](./media/calculator-autos.png "Okno Automatické hodnoty")

Chcete-li zobrazit všechny proměnné z této funkce, přepněte do okna **místní** hodnoty. Hodnoty těchto proměnných můžete v průběhu ladění skutečně upravovat, abyste viděli, jaký má vliv na program. V takovém případě je zadáte samostatně.

   ![Okno místních hodnot](./media/calculator-locals.png "Okno místních hodnot")

Můžete také umístit ukazatel myši na proměnné v samotném kódu, abyste viděli jejich aktuální hodnoty, kde je provádění aktuálně pozastaveno. Ujistěte se, že je okno editoru aktivní, a to tak, že na něj kliknete nejdřív.

   ![Najetím myší zobrazíte aktuální hodnoty proměnných.](./media/calculator-hover-tooltip.gif "Najetím myší zobrazíte aktuální hodnoty proměnných.")

### <a name="to-continue-debugging"></a>Pokračování v ladění

1. Žlutý řádek na levé straně znázorňuje aktuální bod provádění. Aktuální řádek zavolá `Calculate`, takže stisknutím klávesy **F11** se **zajděte do** funkce. V těle funkce `Calculate` zjistíte sami sebe. Buďte opatrní při **krokování**; Pokud to uděláte příliš daleko, může dorazit spoustu času. Přejde do libovolného kódu, který použijete na řádku, na kterém se nacházíte, včetně standardních funkcí knihovny.

1. Teď, když je bod spuštění na začátku `Calculate` funkce, stisknutím klávesy **F10** přejdete na další řádek v provádění programu. **F10** se také označuje jako **krok za krokem**. Můžete použít **Krok** nahoru pro přechod mezi řádky a spojnici, aniž byste museli zobrazit podrobnosti o tom, co se v každé části řádku objevuje. Obecně byste měli místo **kroku into**použít **Krok** , pokud nechcete podrobně do kódu, který je volán jinam (jako při přístupu k textu `Calculate`).

1. Pokračujte v používání **klávesy F10** , abyste mohli **Krokovat** s každým řádkem, dokud se nevrátíte do funkce `main()` v druhém souboru a zastavte se na řádku `cout`.

   ![Krok z výpočtu a kontroly výsledku](./media/calculator-undefined-zero.gif "Krok z výpočtu a kontroly výsledku")

   Vypadá to, že program dělá, co je očekávané: přijímá první číslo a rozděluje ho druhým. Na `cout` řádku najeďte myší na proměnnou `result` nebo se podívejte na `result` v okně **Automatické** hodnoty. Uvidíte, že jeho hodnota je uvedena jako "INF", což nevypadá správně, takže ji Opravme. `cout` řádek právě vypisuje libovolnou hodnotu, která je uložena v `result`, takže když postupně provedete další **řádek, zobrazí se okno**konzoly:

   ![Výsledek dělení nulou](./media/calculator-divide-by-zero-fail.png "Výsledek dělení nulou")

   K tomuto výsledku dochází, protože dělení nulou není definováno, takže program nemá číselnou odpověď na požadovanou operaci.

### <a name="to-fix-the-divide-by-zero-error"></a>Oprava chyby "dělení nulou"

Podíváme se, aby dělení nulou bez problémů, takže uživatel může pochopit problém.

1. Proveďte následující změny v *CalculatorTutorial. cpp*. (Program můžete nechat spuštěný při úpravách, a to díky funkci ladicího programu s názvem **Upravit a pokračovat**):

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

1. Nyní stiskněte klávesu **F5** . Provádění programu pokračuje všemi způsoby, dokud se nemusíte pozastavit, aby pomohlo zadání uživatele. Zadejte `10 / 0` znovu. Nyní je vytištěna užitečnější zpráva. Uživatel je vyzván k zadání dalšího vstupu a program pokračuje v normálním provádění.

   ![Konečný výsledek po změně](./media/calculator-final-verification.gif "Konečný výsledek po změně")

   > [!Note]
   > Při úpravách kódu v režimu ladění existuje riziko, že se kód stane zastaralým. K tomu dojde v případě, že ladicí program stále používá starý kód a ještě neaktualizoval se změnami. Ladicí program zobrazí dialogové okno s informací o tom, kdy k tomu dojde. Někdy může být nutné stisknout klávesu **F5** pro aktualizaci spouštěného kódu. Zejména pokud provedete změnu uvnitř funkce, zatímco je bod provádění uvnitř této funkce, budete muset krok převzít z funkce a následně zpátky do ní získat aktualizovaný kód. Pokud to z nějakého důvodu nefunguje a zobrazí se chybová zpráva, můžete ladění zastavit kliknutím na červené čtverce na panelu nástrojů v nabídce v horní části rozhraní IDE a pak znovu spustit ladění, a to tak, že zadáte **F5** nebo kliknutím na zelenou šipku "Play" vedle tlačítka zastavit na panelu nástrojů.

   > Principy klávesových zkratek Run a Debug
   >
   > - **F5** (nebo **ladění** > **Spustit ladění**) spustí ladicí relaci, pokud již jedna není aktivní, a spustí program, dokud nebude dosaženo zarážky nebo když program potřebuje vstup uživatele. Pokud není nutný žádný vstup uživatele a není k dispozici žádná zarážka, program se ukončí a okno konzoly se po dokončení programu zavře. Pokud máte něco podobného jako spuštění programu "Hello World", použijte **CTRL + F5** nebo nastavte zarážku před zadáním klávesy **F5** , aby okno zůstalo otevřené.
   > - **CTRL + F5** (nebo **ladění** > **Spustit bez ladění**) spustí aplikaci bez přechodu do režimu ladění. Toto je mírně rychlejší než ladění a okno konzoly zůstane otevřené, i když program dokončí provádění.
   > - **F10** (označované jako **Krokovat**s přečtením) umožňuje iterovat kód, řádek po řádku a vizualizovat, jak se kód spouští a jaké hodnoty proměnných jsou v každém kroku provádění.
   > - Klávesa **F11** (označovaná jako **Krok do**) funguje podobně jako při **prvním kroku**, s výjimkou kroků na jakékoli funkce, které jsou volány na řádku provádění. Například pokud je řádek spouštěn voláním funkce, stisknutí klávesy **F11** přesune ukazatel na tělo funkce, aby bylo možné sledovat spouštěný kód funkce před návratem k řádku, na kterém jste začali. Stisknutí klávesy **F10** nad voláním funkce a pouhým přechodem na další řádek; k volání funkce stále dochází, ale program se nezastaví, aby vám ukázal, co dělá.

### <a name="close-the-app"></a>Zavřít aplikaci

- Pokud je pořád spuštěný, zavřete okno konzoly pro aplikaci kalkulačky.

## <a name="the-finished-app"></a>Dokončená aplikace

Blahopřejeme! Dokončili jste kód pro aplikaci kalkulačky a vytvořili jste ho a rozpnuli ho v aplikaci Visual Studio.

## <a name="next-steps"></a>Další kroky

[Další informace o aplikaci Visual Studio proC++](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end
