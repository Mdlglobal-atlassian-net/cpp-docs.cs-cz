---
title: Vytvoření projektu aplikace konzoly C++
description: Vytvořte konzolovou aplikaci Hello World a Kalkulačka aplikace v jazyce Visual C++
ms.custom: mvc
ms.date: 03/25/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: b15bc7551c4bf99b6dd52f99bb5e69064ddb8308
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382692"
---
# <a name="create-a-c-console-app-project"></a>Vytvoření projektu aplikace konzoly C++

Obvyklým výchozím bodem pro programátor C++ je "Hello, world!" aplikace, která běží na příkazovém řádku. To je, co vytvoříte v sadě Visual Studio v tomto článku a pak budeme pokračovat na něco náročnější: Kalkulačka aplikace.

## <a name="prerequisites"></a>Požadavky

- Sada Visual Studio s **vývoj desktopových aplikací pomocí C++** úlohy, které jsou nainstalované a spuštěné v počítači. Pokud ještě není nainstalovaný, přečtěte si téma [podpora instalace jazyka C++ v sadě Visual Studio](../../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Vytvoření projektu aplikace

Visual Studio používá *projekty* organizaci kódu pro aplikace, a *řešení* k uspořádání vašich projektů. Projekt obsahuje všechny možnosti, konfigurace a pravidla používaná k vytváření aplikací. Spravuje také vztah mezi všechny projektové soubory a soubory s externí. Pokud chcete vytvořit aplikaci, nejprve vytvoříte nový projekt a řešení.

1. V řádku nabídek v sadě Visual Studio, zvolte **souboru** > **nový** > **projektu**. **Nový projekt** otevře se okno.

2. Na levém bočním panelu, ujistěte se, že **Visual C++** zaškrtnuto. V centru, zvolte **Konzolová aplikace Windows**.

3. V **název** textového pole v dolní části, pojmenujte nový projekt *CalculatorTutorial*, klikněte na tlačítko **OK**.

   ![Dialogové okno Nový projekt](./media/calculator-new-project-dialog.png "dialogového okna Nový projekt")

   Vytvoří prázdnou aplikaci konzoly Windows C++. Konzolové aplikace pomocí okna konzoly Windows a zobrazte výstup přijímají vstup uživatele. V sadě Visual Studio okno editoru se otevře a zobrazí vygenerovaný kód:

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

## <a name="verify-that-your-new-app-builds-and-runs"></a>Ověřte, že vaše nová aplikace se vytvoří a spustí

Šablonu pro novou konzolovou aplikaci systému windows vytvoří jednoduchou aplikaci "Hello World" jazyka C++. V tuto chvíli uvidíte jak Visual Studio vytvoří a spustí aplikace, které vytvoříte přímo z integrovaného vývojového prostředí.

1. Chcete-li projekt sestavit, zvolte **sestavit řešení** z **sestavení** nabídky. **Výstup** okno zobrazuje výsledky procesu sestavení.

   ![Sestavte projekt](./media/calculator-initial-build-output.png "sestavení projektu")

1. Chcete-li spustit kód, na panelu nabídek, zvolte **ladění**, **spustit bez ladění**.

   ![Spustit projekt](./media/calculator-hello-world-console.png "spustit projekt")

   Okno konzoly otevře a spustí vaši aplikaci. Když spustíte aplikaci konzoly v sadě Visual Studio, spustí váš kód a pak vypíše "stisknutím libovolné klávesy, abyste mohli pokračovat. . ." získáte možnost zobrazit výstup. Blahopřejeme! Vytvoření první "Hello, world!" Konzolová aplikace v sadě Visual Studio!

1. Stisknutím jakékoli klávesy zavřete okno konzoly a vraťte se do sady Visual Studio.

Teď máte nástroje pro sestavení a spuštění aplikace po každé změně, chcete-li ověřit, že kód stále funguje podle očekávání. Později vám ukážeme, jak ho ladit, pokud tomu tak není.

## <a name="edit-the-code"></a>Upravit kód

Teď obraťme kód v této šabloně do aplikace kalkulačku.

1. V *CalculatorTutorial.cpp* souboru, upravte kód tak, aby odpovídala takto:

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

   > Porozumění kódu:
   >
   > - `#include` Příkazy umožňuje odkazovat na kódu v jiných souborech. V některých případech může se zobrazit název souboru ohraničen ostrými závorkami (**\<\>**); jindy je ohraničen uvozovkami (**""**). Obecně platí ostré závorky se používají při odkazování na standardní knihovny C++, zatímco nabídky se používá pro jiné soubory.
   > - `#include "pch.h"` (Nebo ve starších verzích sady Visual Studio, `#include "stdafx.h"`) řádek odkazuje na něco jako předkompilované hlavičky. Tyto jsou často používány profesionálních programátorů umožňují zrychlit kompilace, ale jsou nad rámec tohoto kurzu.
   > - `using namespace std;` Řádku instruuje kompilátor, aby očekávají věci ze standardní knihovny C++, který se má použít v tomto souboru. Bez tohoto řádku by musel párový příkaz s každé klíčové slovo z knihovny `std::`, k označení její obor. Například bez tento řádek každý odkaz na `cout` musela zapsat, protože `std::cout`. `using` Příkaz je přidat – tak kód vypadaly úhledně více.
   > - `cout` – Klíčové slovo se používá k vytištění do standardního výstupu v jazyce C++. **\< \<** Operátor instruuje kompilátor, aby odeslat cokoli, co je napravo od ji ve standardním výstupu.
   > - **Endl** – klíčové slovo je jako klávesu Enter; ukončení řádku a přesune kurzor na další řádek. Je doporučeno pro umístění `\n` do řetězce (obsažen v "") provést totéž, jako `endl` vždy vyprázdní vyrovnávací paměť a může snížit výkon aplikace, ale protože to je velmi malou aplikaci, `endl` se místo toho používá pro lepší lepší čitelnost.
   > - Všechny příkazy C++ musí končit středníkem a musí obsahovat všechny aplikací v jazyce C++ `main()` funkce. Tato funkce je program spuštěn na začátku. Veškerý kód musí být dostupný z `main()` jinak se nedá použít.

1. Chcete-li uložit soubor, zadejte **Ctrl + S**, nebo zvolte **Uložit** ikonu v horní části rozhraní IDE, ikonu diskety v panelu nástrojů v řádku nabídek.

1. Chcete-li aplikaci spustit, stiskněte **Ctrl + F5** nebo přejděte na **ladění** nabídky a zvolte **spustit bez ladění**. Pokud se zobrazí automaticky otevírané okno s upozorněním **tento projekt není aktuální**, můžete vybrat **tento dialog již příště nezobrazovat**a klikněte na tlačítko **Ano** k sestavení aplikace. Měli byste vidět okno konzoly zobrazí zobrazí text uvedený v kódu.

   ![Sestavte a spusťte aplikaci](./media/calculator-first-launch.gif "sestavit a spustit aplikaci")

1. Jakmile budete hotovi, zavřete okno konzoly.

## <a name="add-code-to-do-some-math"></a>Přidejte kód pro procvičili matematiku

Je čas na přidání některých matematických logiku.

### <a name="to-add-a-calculator-class"></a>Přidání třídy Kalkulačka

1. Přejděte **projektu** nabídku a zvolte **přidat třídu**. V **název třídy** textové pole, zadejte *Kalkulačka*. Zvolte **OK**. Dva nové soubory nechejte se přidat do projektu. Chcete-li uložit všechny změněné soubory najednou, stiskněte **Ctrl + Shift + S**. Je klávesová zkratka **souboru** > **Uložit vše**. Je také tlačítko panelu nástrojů pro **Uložit vše**, ikona dvou disket nenašel vedle **Uložit** tlačítko. Obecně je vhodné provést **Uložit vše** často, takže můžete Nenechte si ujít všechny soubory při uložení.

   ![Vytvořte třídu Kalkulačka](./media/calculator-create-class.gif "vytvořit třídu Kalkulačka")

   Třída je jako matrice objektu, která něco dělá. V takovém případě definujeme kalkulačku a jak by mělo fungovat. **Přidat třídu** Průvodce využité nad vytvořené soubory .h a .cpp, které mají stejný název jako třída. Můžete zobrazit úplný seznam souborů v projektu **Průzkumníka řešení** okno viditelné Toolbar integrovaného vývojového prostředí. Pokud v okně není zobrazena, lze jej otevřít z řádku nabídek: Zvolte **zobrazení** > **Průzkumníka řešení**.

   ![Průzkumník řešení](./media/calculator-solution-explorer.png "Průzkumníka řešení")

   Teď byste měli mít tři karty, které se otevře v editoru: *CalculatorTutorial.cpp*, *Calculator.h*, a *Calculator.cpp*. Pokud omylem uzavřete jeden z nich, můžete znovu otevřít jej dvojitým kliknutím v **Průzkumníka řešení** okna.

1. V **Calculator.h**, odeberte `Calculator();` a `~Calculator();` řádky, které byly vytvořeny, protože je nebudete potřebovat tady. Dále přidejte následující řádek kódu, takže ho teď vypadá takto:

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > Porozumění kódu
   >
   > - Je přidaný řádek deklaruje novou funkci s názvem `Calculate`, který použijeme ke spuštění matematických operací pro sčítání, odčítání, násobení a dělení.
   > - Kód jazyka C++ je uspořádaný do *záhlaví* souborů (.h) a *zdroj* soubory (.cpp). Různé kompilátory podporují několik dalších přípon souborů, ale toto jsou hlavní ty vědět o. Funkce a proměnné jsou obvykle *deklarované*, která je zadaný název a typ, v souborech hlaviček, a *implementované*, nebo při definici, ve zdrojových souborech. Pro přístup kód definovaný v jiném souboru, můžete použít `#include "filename.h"`, kde "filename.h" je název souboru, který deklaruje proměnné nebo funkce, kterou chcete použít.
   > - Dva řádky odstraněné deklarované *konstruktor* a *destruktor* pro třídu. Pro jednoduchou třídu, jako je ten kompilátor vytvoří za vás a jejich použití jsou nad rámec tohoto kurzu.
   > - Je dobrým zvykem organizovat kód do různých souborů podle jeho význam, tak, aby byl snadno najít kód, který budete potřebovat později. V našem případě definujeme `Calculator` třídy nezávisle na soubor obsahující `main()` funkce, ale doporučujeme naplánovat tak, aby odkazovaly `Calculator` třídy v `main()`.

1. Zobrazí se zelená vlnovku se zobrazí v rámci `Calculate`. Je proto, že jsme ještě nebyl definován `Calculate` funkce v souboru .cpp. Najeďte myší aplikaci word, klikněte na žárovku, která se zobrazí a zvolte **vytvoření definice "Vypočítat" v Calculator.cpp**. Se zobrazí automaticky otevírané okno, které poskytuje náhled změn kódu, která byla vytvořena v jiném souboru. Kód byl přidán do *Calculator.cpp*.

   ![Vytvoření definice Calculate](./media/calculator-create-definition.gif "vytvořit definici vypočítat")

   V současné době pouze vrátí 0,0. Teď Změníme. Stisknutím klávesy **Esc** automaticky otevírané okno zavřete.

1. Přepněte *Calculator.cpp* souborů v okně editoru. Odeberte `Calculator()` a `~Calculator()` oddíly (stejně jako v souboru .h) a přidejte následující kód, který `Calculate()`:

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

   > Porozumění kódu
   >
   > - Funkce `Calculate` využívá číslo, operátor a druhé číslo a potom provede požadovanou operaci u čísel.
   > - Příkaz kontroly přepínač operátoru byla zadaná a to pouze spustí case odpovídající této operaci. Výchozí hodnota: case se používají jako základní v případě, že uživatel zadá operátor není povolena, takže nedojde k narušení program. Obecně je nejvhodnější pro zpracování Neplatný uživatelský vstup elegantnější způsobem, ale jde nad rámec tohoto kurzu.
   > - `double` – Klíčové slovo označuje typ číslo, které podporuje desetinná čísla. Tímto způsobem kalkulačce dokáže zpracovat desítkové matematické a matematikou celých čísel. `Calculate` Funkce je potřeba vždy vrátí číslo, protože `double` na začátku kódu (označuje návratový typ funkce), což je důvod, proč se vrací 0,0 i ve výchozím nastavení.
   > - Soubor .h deklaruje funkci *prototypu*, který instruuje kompilátor, předem, jaké parametry se vyžaduje, a jaké návratový typ od něj očekávat. Soubor .cpp má všechny podrobnosti implementace funkce.

Je-li sestavit a spustit kód znovu v tomto okamžiku, se stále ukončí po s dotazem, kterou operaci má provést. V dalším kroku upravíte `main` funkce provedete pár výpočtů.

### <a name="to-call-the-calculator-class-member-functions"></a>Volání funkce člena třídy Kalkulačka

1. Teď můžeme aktualizovat `main` fungovat v *CalculatorTutorial.cpp*:

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

   > Porozumění kódu
   >
   > - Protože programy v jazyce C++ vždy začínají hodnotou `main()` funkce, musíme volání našeho kódu z něj, tak `#include` příkazu je potřeba.
   > - Některé počáteční proměnné `x`, `y`, `oper`, a `result` jsou deklarovány na ukládání první číslo, druhé číslo, operátor a konečný výsledek. Vždy je dobrým zvykem, abyste jim zajistili některé počáteční hodnoty, aby se zabránilo nedefinované chování, která je, co se zde provádí.
   > - `Calculator c;` Řádek deklaruje objekt s názvem "c", protože instance `Calculator` třídy. Vlastní třídy je pouze pro fungování kalkulačky; objekt je konkrétní kalkulačky, který provede výpočty.
   > - `while (true)` Příkaz je smyčka. Kód uvnitř smyčka pokračuje v provádění opakovaně, dokud je podmínka uvnitř `()` platí. Vzhledem k tomu, že podmínka je jednoduše uveden jako `true`, je vždy hodnotu true, takže cyklu navždy. Ukončete program, musí uživatel ručně zavřete okno konzoly. V opačném případě program vždy čeká nový vstup.
   > - `cin` – Klíčové slovo se používá tak, aby přijímal vstup od uživatele. Tento vstupní datový proud je dostatečně inteligentní, aby zpracoval řádek textu zadaného v okně konzoly a umístěte do každé proměnné, které jsou uvedeny v pořadí, za předpokladu, že vstupní shody uživatele požadovanou specifikaci. Můžete upravit tento řádek tak, aby přijímal různých typů vstupu, například větší než dvě čísla, i když `Calculate()` funkce budete také muset aktualizovat tak, aby se o to postarají.
   > - `c.Calculate(x, oper, y);` Výraz volání `Calculate` funkce definovali dříve a je zdrojem zadané vstupní hodnoty. Funkce pak vrátí číslo, které se uloží v `result`.
   > - Nakonec `result` vytiskne na konzolu, tak uživateli se zobrazí výsledek výpočtu.

### <a name="build-and-test-the-code-again"></a>Sestavit a otestovat kód znovu

Nyní je čas otestovat program znovu, abyste měli jistotu, že všechno funguje správně.

1. Stisknutím klávesy **Ctrl + F5** znovu sestavte a spusťte aplikaci.

1. Zadejte `5 + 5`a stiskněte klávesu **Enter**. Ověřte, že výsledek je 10.

   ![Výsledek 5 + 5](./media/calculator-five-plus-five.png "výsledek 5 + 5")

## <a name="debug-the-app"></a>Ladění aplikace

Vzhledem k tomu, že uživateli je zadarmo zadávat nic do okna konzoly, se ujistěte, že kalkulačky zpracovává vstup podle očekávání. Místo spuštění programu, můžeme ho ladit místo toho tak jsme si můžete prohlédnout, co to dělá podrobně krok za krokem.

### <a name="to-run-the-app-in-the-debugger"></a>Spusťte aplikaci v ladicím programu

1. Nastavit zarážku na `result = c.Calculate(x, oper, y);` řádku, bezprostředně po uživateli se zobrazí výzva pro vstup. Chcete-li nastavit zarážku, klikněte na tlačítko vedle řádku v šedé svislá čára sledovat levému okraji okna editoru. Zobrazí se červená tečka.

   ![Nastavit zarážku](./media/calculator-set-breakpoint.gif "nastavte zarážku")

   Nyní když jsme ladění programu, vždy pozastaví provádění na tento řádek. Už máme přibližnou představu, který pro jednoduché případů bude program. Protože nechceme pozastavit provádění pokaždé, když, vytvoříme zarážka podmíněný.

1. Klikněte pravým tlačítkem na červenou tečku představující zarážku a zvolte **podmínky**. Do textového pole podmínky, zadejte `(y == 0) && (oper == '/')`. Zvolte **Zavřít** tlačítko až budete hotovi. Podmínka se automaticky uloží.

   ![Nastavení podmíněné zarážky](./media/calculator-conditional-breakpoint.gif "nastavení podmíněné zarážky")

   Nyní jsme pozastavit provádění na zarážce, konkrétně, pokud dojde k pokusu o dělení hodnotou 0.

1. Pokud chcete program ladit, stiskněte **F5**, nebo zvolte **místní ladicí program Windows** tlačítka panelu nástrojů, který má ikonu zelenou šipku. Ve vaší aplikaci konzoly Pokud něco jako "5-0", zadejte program se chovat normálně a stále spuštěný. Nicméně pokud zadáte "10 / 0", jeho pozastavení na zarážce. Můžete dokonce vložit libovolný počet mezer mezi operátor a čísla. `cin` je dostatečně inteligentní, aby správně analyzovat vstup.

   ![Pozastavení na zarážce podmíněného](./media/calculator-debug-conditional.gif "pozastavení na zarážce podmíněné")

### <a name="useful-windows-in-the-debugger"></a>Užitečné windows v ladicím programu

Pokaždé, když se při ladění kódu, můžete si všimnout, že se zobrazí několik nových oknech. Možnosti ladění můžou pomoct tato okna. Podívejte se na **automatické hodnoty** okna. **Automatické hodnoty** okno se zobrazuje aktuální hodnoty proměnných použít minimálně tři řádky před a až do aktuálního řádku.

   ![V okně Automatické hodnoty](./media/calculator-autos.png "okno Automatické hodnoty")

Chcete-li zobrazit všechny proměnné z této funkce, přepněte **lokální** okna. Hodnoty těchto proměnných při ladění, můžete upravit ve skutečnosti zobrazíte jaký vliv bude mít v programu. V tomto případě Ponecháme je samostatně.

   ![V okně místních hodnot](./media/calculator-locals.png "okno oknech místní hodnoty")

Můžete také pouze najetí myší na proměnné v samotném zobrazíte jejich aktuálními hodnotami, kde je momentálně pozastavený provádění kódu. Ujistěte se, že okno editoru fokus nejprve kliknutím na ni.

   ![Najetím myší zobrazíte aktuální hodnoty proměnných](./media/calculator-hover-tooltip.gif "při najetí myší, chcete-li zobrazit aktuální hodnoty proměnných")

### <a name="to-continue-debugging"></a>Pro pokračování v ladění

1. Žlutá čára na levé straně se zobrazí aktuální bod provádění. Aktuální řádek volání `Calculate`, takže stiskněte **F11** k **Krokovat s vnořením** funkce. Zorientujete se v těle `Calculate` funkce. Buďte opatrní při používání **Krokovat s vnořením**; Pokud tak učiníte příliš mnoho může odpad spoustu času. Přejde na jakýkoli kód, který používáte na řádek, který používáte, včetně funkce standardní knihovny.

1. Teď, když bod provádění na začátku `Calculate` funkci, stiskněte klávesu **F10** přesunout na další řádek při provádění programu. **F10** se taky říká **Krokovat s přeskočením**. Můžete použít **Krokovat s přeskočením** přesunout řádcích, bez seznamovat s podrobnostmi o co se děje v jednotlivých součástí řádku. Obecně byste měli použít **Krokovat s přeskočením** místo **Krokovat s vnořením**, pokud nechcete Ponořte se hlouběji do kódu, která je volána z jinde (stejně jako k dosažení tělo `Calculate`).

1. Pokračovat v používání **F10** k **Krokovat s přeskočením** každého řádku, dokud se nevrátíte se zpátky do `main()` fungovat v jiném souboru a zastaví se na `cout` řádku.

   ![Vystoupení ze Calculate a zkontrolujte výsledek](./media/calculator-undefined-zero.gif "vystoupení ze Calculate a zkontrolovat výsledky")

   Vypadá to program provádí, co se očekává: přijímá první číslo a rozděluje po sekundách. Na `cout` řádek, najeďte myší `result` proměnné nebo se podívejte na `result` v **automatické hodnoty** okna. Uvidíte, že její hodnota je uveden jako "informace", který nevypadá moc správně, takže ho opravit. `cout` Řádku právě výstupy, ať hodnota je uložená v `result`, takže když vejdete další řádek předávání pomocí **F10**, v okně konzoly se zobrazí:

   ![Výsledek dělení nulou](./media/calculator-divide-by-zero-fail.png "výsledek dělení nulou")

   Tento výsledek dochází dělení nulou není definováno, takže program neobsahuje numerické odpověď na požadovanou operaci.

### <a name="to-fix-the-divide-by-zero-error"></a>Chcete-li vyřešit chybu "dělení nulou"

Pojďme dělení nulou více elegantně zpracovat, to uživateli umožní pochopit i problém.

1. Proveďte následující změny v *CalculatorTutorial.cpp*. (Můžete nechat program spuštěný při úpravě díky funkci ladicího programu s názvem **upravit a pokračovat**):

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

1. Nyní stiskněte **F5** po. Program pokračuje tímto způsobem, dokud má pozastavit požádat pro uživatelský vstup. Zadejte `10 / 0` znovu. Nyní je užitečnější zpráva vytištěna. Zobrazí se uživateli výzva pro další vstup a program pokračuje v provádění normálně.

   ![Konečný výsledek po změně](./media/calculator-final-verification.gif "konečný výsledek po provedení změn")

   > [!Note]
   > Při úpravách kódu při v režimu ladění, existuje riziko kódu budou zastaralá. To se stane, když ladicí program je pořád spuštěný starý kód a ještě neaktualizoval ji se změnami. Ladicí program zobrazí dialogové okno vás informovat, pokud k tomu dojde. V některých případech budete muset stiskněte **F5** aktualizovat právě prováděný kód. Zejména pokud provedete změnu uvnitř funkce při bodu provádění je uvnitř, že funkce, je potřeba krok mimo funkci a pak zpátky do něj znovu zobrazíte aktualizovaný kód. Pokud to nepomůže z nějakého důvodu a objeví se chybová zpráva, můžete zastavit ladění po kliknutí na červený čtvereček na panelu nástrojů v rámci nabídky v horní části rozhraní IDE a pak znovu spusťte ladění tak, že zadáte **F5** nebo výběrem zelené " Přehrát"šipku vedle tlačítka Zastavit na panelu nástrojů.
   
   > Principy zkratky spuštění a ladění
   >
   > - **F5** (nebo **ladění** > **spustit ladění**) spustí relaci ladění, pokud ještě není aktivní a spustí program, dokud nebude dosaženo zarážky nebo uživatelského vstupu pro potřeby aplikace. Pokud je nutný zásah uživatele a bez zarážek není k dispozici k volání, program se ukončí a v okně konzoly se ukončí sám při ukončení programu. Pokud máte něco jako "Hello World" program ke spuštění, použijte **Ctrl + F5** nebo nastavte zarážku před zadáním **F5** nechat okno otevřené.
   > - **CTRL + F5** (nebo **ladění** > **spustit bez ladění**) spustí aplikaci bez přechodu do režimu ladění. Toto je mírně rychlejší než ladění a v okně konzoly se zůstane otevřený po dokončení provádění.
   > - **F10** (označované jako **Krokovat s přeskočením**) umožňuje iterovat přes kódu řádek po řádku a vizualizace, jak spustit kód a jaké jsou hodnoty proměnných v každém kroku spuštění.
   > - **F11** (označované jako **Krokovat s vnořením**) funguje podobně jako **Krokovat s přeskočením**, s výjimkou vstoupí do jakékoli funkce volána na řádek provádění. Například pokud spouštěný řádek volá funkci, stiskněte **F11** přesune ukazatel do těla funkce, takže můžete postupovat podle této funkce kód spuštěn před vrátíte do řádku začalo v. Stisknutím klávesy **F10** kroky prostřednictvím volání funkce a pouze přesune na další řádek; volání funkce se stále dochází, ale nebude pozastavit program zobrazit, co dělají.

### <a name="close-the-app"></a>Zavřete aplikaci

1. Pokud je stále spuštěna, zavřete okno konzoly pro aplikaci kalkulačku.

## <a name="the-finished-app"></a>Dokončená aplikace

Blahopřejeme! Dokončení kódu pro aplikaci kalkulačky a integrované a ladit v sadě Visual Studio.

## <a name="next-steps"></a>Další kroky

[Další informace o sadě Visual Studio pro C++](https://blogs.msdn.microsoft.com/vcblog/2017/04/21/getting-started-with-visual-studio-for-c-and-cpp-development/)
