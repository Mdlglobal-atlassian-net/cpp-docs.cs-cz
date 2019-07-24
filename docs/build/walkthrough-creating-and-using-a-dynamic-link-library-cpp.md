---
title: 'Návod: Vytvoření a použití vlastní knihovny DLL (C++)'
description: Slouží C++ k vytvoření knihovny DLL (Dynamic-Link Library) systému Windows v aplikaci Visual Studio.
ms.custom: conceptual
ms.date: 07/17/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 8ca89471177ba2d1fa98bfaf51b86ed15dcd6d2f
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299808"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Návod: Vytvoření a použití vlastní knihovny DLL (C++)

Tento podrobný návod ukazuje, jak použít integrované vývojové prostředí (IDE) sady Visual Studio k vytvoření vlastní knihovny DLL (Dynamic Link Library) napsané v C++a jejím použití z jiné C++ aplikace. Knihovny DLL (známé také jako sdílené knihovny v operačních systémech UNIX) jsou jedním z nejužitečnějších typů součástí Windows. Můžete je použít jako způsob, jak sdílet kód a prostředky, zmenšit velikost vašich aplikací a usnadnit službu a rozšiřování aplikací. V tomto návodu vytvoříte knihovnu DLL, která implementuje některé matematické funkce, a pak vytvoříte konzolovou aplikaci, která používá funkce z knihovny DLL. V takovém případě získáte Úvod k některým programovacím technikům a konvencím používaným v knihovnách DLL systému Windows.

Tento názorný postup se zabývá následujícími úlohami:

- Vytvořte projekt knihovny DLL v aplikaci Visual Studio.

- Do knihovny DLL přidejte exportované funkce a proměnné.

- Vytvořte projekt konzolové aplikace v aplikaci Visual Studio.

- Použijte funkce a proměnné importované z knihovny DLL v konzolové aplikaci.

- Spusťte dokončenou aplikaci.

Podobně jako staticky propojená knihovna, knihovna DLL _exportuje_ proměnné, funkce a prostředky podle názvu a aplikace _importuje_ tyto názvy pro použití proměnných, funkcí a prostředků. Na rozdíl od staticky propojené knihovny Windows spojuje importy v aplikaci s exporty v knihovně DLL v době načítání nebo v době běhu, namísto jejich propojení v době připojení. Systém Windows vyžaduje další informace, které nejsou součástí standardního C++ modelu kompilace, aby bylo možné tato připojení provést. Kompilátor MSVC implementuje některá rozšíření specifická pro společnost Microsoft k C++ poskytnutí těchto dalších informací. Tato rozšíření Vysvětleme.

Tento návod vytvoří dvě řešení sady Visual Studio; ten, který vytváří knihovnu DLL, a jednu, která sestavuje klientskou aplikaci. Knihovna DLL používá konvenci volání jazyka C, aby ji bylo možné volat z aplikací vytvořených pomocí jiných jazyků, pokud se shodují konvence platformy a volání a propojení. Klientská aplikace používá _implicitní propojení_, kde Windows propojuje aplikaci s knihovnou DLL při načtení. Toto propojení umožňuje, aby aplikace zavolala funkce poskytnuté knihovnou DLL stejně jako funkce ve staticky propojené knihovně.

Tento návod nezahrnuje některé běžné situace. Nezobrazuje použití C++ knihoven DLL jinými programovacími jazyky. Neukazuje, jak vytvořit knihovnu DLL, která je jen pro prostředky. Také nezobrazuje použití explicitního propojení s knihovnami DLL pro načtení v době běhu, nikoli při načtení. Vše, co je dobré, můžete k tomu použít Visual Studio. Odkazy na Další informace o knihovnách DLL naleznete v tématu [CreateC++ C/dlls in Visual Studio](dlls-in-visual-cpp.md). Další informace o implicitním propojení a explicitním propojení najdete v tématu [určení, kterou propojovací metodu použít](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Informace o vytváření C++ knihoven DLL pro použití s programovacími jazyky, které používají konvence propojení jazyka c, naleznete v tématu [Exportování C++ funkcí pro použití ve spustitelných souborech jazyka c](exporting-cpp-functions-for-use-in-c-language-executables.md). Informace o tom, jak vytvořit knihovny DLL pro použití s jazyky rozhraní .NET, naleznete v tématu [volání funkcí knihovny DLL z aplikací Visual Basic](calling-dll-functions-from-visual-basic-applications.md).

## <a name="prerequisites"></a>Požadavky

- Počítač se systémem Microsoft Windows 7 nebo novější verzí. Pro nejlepší vývojové prostředí doporučujeme Windows 10.

- Kopie sady Visual Studio. Informace o tom, jak stáhnout a nainstalovat Visual Studio, najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio). Když spustíte instalační program, ujistěte se, že je zaškrtnuté políčko **vývoj pro stolní počítače pomocí C++**  úlohy. Nedělejte si starosti, pokud jste při instalaci sady Visual Studio nenainstalovali tuto úlohu. Instalační program můžete spustit znovu a nainstalovat hned.

   ![Vývoj desktopových C++ aplikací pomocí](media/desktop-development-with-cpp.png "Vývoj desktopových C++ aplikací pomocí")

- Porozumění základům používání integrovaného vývojového prostředí (IDE) sady Visual Studio Pokud jste už používali desktopové aplikace pro Windows, můžete si je nechat. Úvod najdete v tématu [prohlídka funkcí rozhraní IDE sady Visual Studio](/visualstudio/ide/visual-studio-ide).

- Seznamte se s dostatečným základem C++ jazyka, který se má sledovat. Nedělejte si starosti, nemůžeme nic složitě.

## <a name="create-the-dll-project"></a>Vytvoření projektu knihovny DLL

V této sadě úkolů vytvoříte projekt pro knihovnu DLL, přidáte kód a sestavíte jej. Začněte tím, že spustíte Visual Studio IDE a přihlásíte se, pokud potřebujete. Pokyny se mírně liší v závislosti na verzi sady Visual Studio, kterou používáte. Ujistěte se, že je v ovládacím prvku v levém horním rohu této stránky vybraná správná verze.

::: moniker range="=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>Vytvoření projektu knihovny DLL v aplikaci Visual Studio 2019

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt** a otevřete tak dialogové okno **vytvořit nový projekt** .

   ![Vytvořit nový projekt knihovny DLL](media/create-new-dll-project-2019.png "Vytvoření projektu MathLibrary")

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Library**. 

1. Z filtrovaného seznamu typů projektů zvolte **dynamická knihovna (DLL)** a pak klikněte na tlačítko **Další**. Na další stránce `MathLibrary` do pole **název** zadejte název projektu a v případě potřeby zadejte umístění projektu.

1. Kliknutím na tlačítko **vytvořit** vytvořte projekt.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>Vytvoření projektu knihovny DLL v aplikaci Visual Studio 2017

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt** . otevře se dialogové okno **Nový projekt** .

1. V levém podokně dialogového okna **Nový projekt** rozbalte v případě potřeby položku **nainstalované** a **vizuál C++**  a pak zvolte možnost **Windows Desktop**. V prostředním podokně vyberte možnost **Průvodce desktopovou plochou systému Windows**. Do `MathLibrary` pole **název** zadejte název projektu.

   ![Pojmenování projektu MathLibrary](media/mathlibrary-new-project-name-153.png "Pojmenování projektu MathLibrary")

1. Kliknutím na tlačítko **OK** zavřete dialogové okno **Nový projekt** a spusťte průvodce **projektem Windows Desktop** .

1. V průvodci **projekt pracovní plochy systému Windows** v části **Typ aplikace**vyberte možnost **dynamická knihovna (. dll)** .

   ![Průvodce vytvořením knihovny DLL v desktopovém projektu Windows](media/mathlibrary-desktop-project-wizard-dll.png "Průvodce vytvořením knihovny DLL v desktopovém projektu Windows")

1. Kliknutím na tlačítko **OK** vytvořte projekt.

> [!NOTE]
> K vyřešení problému v aplikaci Visual Studio 2017 verze 15,3 jsou nutné další kroky. Postupujte podle těchto pokynů, abyste viděli, jestli potřebujete tuto změnu provést.
>
>1. V **Průzkumník řešení**, pokud ještě není vybraná, vyberte projekt **MathLibrary** v části **řešení "MathLibrary"** .
>
>1. Na panelu nabídek vyberte **vlastnosti** **projektu** > .
>
>1. V levém podokně dialogového okna **stránky vlastností** vyberte možnost **preprocesor** v části **vlastnosti** > konfigurace**C/C++** . Ověřte obsah vlastnosti **Definice preprocesoru** .<br/><br/>![Podívejte se na vlastnost definice] preprocesoru. (media/mathlibrary-153bug-preprocessor-definitions-check.png "Podívejte se na vlastnost definice") preprocesoru.<br/><br/>Pokud se v seznamu **definice** preprocesoru zobrazí **MATHLIBRARY&#95;exporty** , pak nemusíte žádné změny měnit. Pokud se místo toho zobrazí **MathLibrary&#95;exporty** , pokračujte podle těchto kroků.
>
>1. V horní části dialogového okna **stránky vlastností** změňte rozevírací seznam **Konfigurace** na **všechny konfigurace**.
>
>1. V podokně vlastností vyberte rozevírací seznam vedle pole upravit pro **definice**preprocesoru a pak zvolte možnost **Upravit**.<br/><br/>![Upravit vlastnost definic preprocesoru](media/mathlibrary-153bug-preprocessor-definitions-property.png "Upravit vlastnost definic preprocesoru")
>
>1. V horním podokně dialogového okna **Definice preprocesoru** přidejte nový symbol `MATHLIBRARY_EXPORTS`.<br/><br/>![Přidat symbol MATHLIBRARY_EXPORTS](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "Přidat symbol MATHLIBRARY_EXPORTS")
>
>1. Kliknutím na **tlačítko OK** zavřete dialogové okno **Definice preprocesoru** a potom kliknutím na **tlačítko OK** uložte změny vlastností projektu.

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>Vytvoření projektu knihovny DLL ve starších verzích sady Visual Studio

1. Na panelu nabídek vyberte **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte položku **nainstalované** > **šablony**a vyberte možnost **vizuál C++** a potom v prostředním podokně vyberte položku **Konzolová aplikace Win32**. Zadejte `MathLibrary` do pole **název** pro úpravy pro zadání názvu projektu.

   ![Pojmenování projektu MathLibrary](media/mathlibrary-project-name.png "Pojmenování projektu MathLibrary")

1. Kliknutím na tlačítko **OK** zavřete dialogové okno **Nový projekt** a spusťte **Průvodce aplikací Win32**.

   ![Průvodce aplikací Win32 – přehled](media/mathlibrary-project-wizard-1.png "Průvodce aplikací Win32 – přehled")

1. Zvolte **Další** tlačítko. Na stránce **nastavení aplikace** klikněte v části **Typ aplikace**na položku **Knihovna DLL**.

   ![Průvodce vytvořením knihovny DLL v aplikaci Win32](media/mathlibrary-project-wizard-2.png "Průvodce vytvořením knihovny DLL v aplikaci Win32")

1. Kliknutím na tlačítko **Dokončit** vytvořte projekt.

Až průvodce dokončí řešení, můžete zobrazit vygenerovaný projekt a zdrojové soubory v okně **Průzkumník řešení** v aplikaci Visual Studio.

![Vygenerované řešení v aplikaci Visual Studio](media/mathlibrary-solution-explorer-153.png "Vygenerované řešení v aplikaci Visual Studio")

Nyní tato knihovna DLL nemá příliš mnoho. V dalším kroku vytvoříte hlavičkový soubor pro deklarování funkcí, které exportuje DLL, a pak přidáte definice funkcí do knihovny DLL, aby byly užitečnější.

::: moniker-end

### <a name="to-add-a-header-file-to-the-dll"></a>Přidání souboru hlaviček do knihovny DLL

1. Chcete-li vytvořit hlavičkový soubor pro vaše funkce, v řádku nabídek vyberte možnost **projekt** > **Přidat novou položku**.

1. V dialogovém okně **Přidat novou položku** v levém podokně vyberte možnost **C++Visual**. V prostředním podokně vyberte **hlavičkový soubor (. h)** . Zadejte `MathLibrary.h` název souboru hlaviček.

   ![Přidat hlavičku v dialogovém okně Přidat novou položku](media/mathlibrary-add-new-item-header-file.png "Přidat hlavičkový soubor v dialogovém okně Přidat novou položku")

1. Kliknutím na tlačítko **Přidat** vygenerujete prázdný hlavičkový soubor, který se zobrazí v novém okně editoru.

   ![Prázdný soubor MathLibrary. h v editoru](media/edit-empty-mathlibrary-header.png "Prázdný soubor MathLibrary. h v editoru")

1. Nahraďte obsah hlavičkového souboru tímto kódem:

   ```cpp
   // MathLibrary.h - Contains declarations of math functions
   #pragma once

   #ifdef MATHLIBRARY_EXPORTS
   #define MATHLIBRARY_API __declspec(dllexport)
   #else
   #define MATHLIBRARY_API __declspec(dllimport)
   #endif

   // The Fibonacci recurrence relation describes a sequence F
   // where F(n) is { n = 0, a
   //               { n = 1, b
   //               { n > 1, F(n-2) + F(n-1)
   // for some initial integral values a and b.
   // If the sequence is initialized F(0) = 1, F(1) = 1,
   // then this relation produces the well-known Fibonacci
   // sequence: 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   extern "C" MATHLIBRARY_API void fibonacci_init(
       const unsigned long long a, const unsigned long long b);

   // Produce the next value in the sequence.
   // Returns true on success and updates current value and index;
   // false on overflow, leaves current value and index unchanged.
   extern "C" MATHLIBRARY_API bool fibonacci_next();

   // Get the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned long long fibonacci_current();

   // Get the position of the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned fibonacci_index();
   ```

Tento hlavičkový soubor deklaruje některé funkce pro vytvoření generalizované sekvence Fibonacci, pro které jsou zadány dvě počáteční hodnoty. Volání, které `fibonacci_init(1, 1)` generuje známou sekvenci Fibonacci čísla.

Všimněte si příkazů preprocesoru v horní části souboru. Ve výchozím nastavení nová šablona projektu pro knihovnu DLL přidá  **\<em > ProjectName\</em >&#95;exporty** do definovaných maker preprocesoru pro projekt knihovny DLL. V tomto příkladu definuje Visual Studio **exporty&#95;MATHLIBRARY** při sestavení projektu knihovny DLL MATHLIBRARY. 

::: moniker range="=vs-2017"

(Průvodce v aplikaci Visual Studio 2017 verze 15,3 nenutí tuto definici symbolu na velká písmena. Pokud zadáte název projektu "MathLibrary", pak je definovaný symbol MathLibrary&#95;EXPORTS namísto exportů&#95;MathLibrary. To je důvod, proč je pro přidání tohoto symbolu k dispozici další postup.)

::: moniker-end

Když je definováno makro **MATHLIBRARY&#95;EXPORTS** , makro **rozhraní&#95;MATHLIBRARY API** nastaví `__declspec(dllexport)` modifikátor v deklaracích funkce. Tento modifikátor instruuje kompilátor a linker, aby vyexportoval funkci nebo proměnnou z knihovny DLL tak, aby ji mohly používat jiné aplikace. Pokud **MATHLIBRARY&#95;exporty** nejsou definovány, například když je hlavičkový soubor součástí klientské aplikace, `__declspec(dllimport)` **rozhraní MATHLIBRARY&#95;API** použije pro deklarace modifikátor. Tento modifikátor optimalizuje import funkce nebo proměnné v aplikaci. Další informace naleznete v tématu [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Přidání implementace do knihovny DLL

::: moniker range="vs-2019"

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **zdrojové soubory** a přidejte nový soubor `MathLibrary.cpp` . cpp stejným způsobem jako v předchozím kroku, který jste přidali nový soubor hlaviček.

::: moniker-end

1. V okně editoru vyberte kartu pro **MathLibrary. cpp** , pokud je již otevřena. Pokud ne, v **Průzkumník řešení**otevřete **MathLibrary. cpp** ve složce **zdrojové soubory** projektu **MathLibrary** .

1. V editoru nahraďte obsah souboru MathLibrary. cpp následujícím kódem:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

Chcete-li ověřit, že vše funguje zatím, zkompilujte dynamickou knihovnu. Chcete-li kompilovat, klikněte na tlačítko **sestavit** > **sestavení** na řádku nabídek. Výstup by měl vypadat přibližně takto. Všimněte si, že spustitelný soubor DLL a související výstup kompilátoru jsou umístěny do složky s názvem *ladění* přímo pod složkou řešení. Pokud vytvoříte sestavení pro vydání, výstup bude umístěn do složky s názvem *release*:

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Gratulujeme, vytvořili jste knihovnu DLL pomocí sady Visual Studio! V dalším kroku vytvoříte klientskou aplikaci, která používá funkce exportované knihovnou DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Vytvořit klientskou aplikaci, která používá knihovnu DLL

Při vytváření knihovny DLL je třeba si představit, jak lze použít knihovnu DLL. Pro zkompilování kódu, který volá funkce exportované knihovnou DLL, musí být deklarace zahrnuty ve zdrojovém kódu klienta. V době propojování, když jsou tato volání funkcí knihovny DLL vyřešena, musí mít linker *knihovnu import*, speciální soubor knihovny, který obsahuje informace pro systém Windows o tom, jak najít funkce namísto skutečného kódu. A v době běhu musí být knihovna DLL k dispozici klientovi, v umístění, které může operační systém najít.

Chcete-li použít knihovnu DLL bez ohledu na to, jestli vaše vlastní nebo knihovna DLL jiného výrobce, musí váš projekt klientské aplikace najít hlavičky, které deklaruje exporty knihoven DLL, importovat knihovny pro Linker a samotnou knihovnu DLL. Jedním ze způsobů je zkopírovat všechny tyto soubory do klientského projektu. Pro knihovny DLL třetích stran, které se při vývoji vašeho klienta pravděpodobně nemění, může být tato metoda nejlepším způsobem jejich použití. Pokud ale také vytváříte knihovnu DLL, je lepší se vyhnout duplicitám. Pokud vytvoříte kopii souborů DLL, které jsou ve vývoji, můžete omylem změnit soubor hlaviček v jednom kopírování, ale ne na druhém, nebo použít neaktuální knihovnu. Chcete-li se tomuto problému vyhnout, doporučujeme nastavit cestu zahrnutí v projektu klienta, aby zahrnovala soubory hlaviček DLL z projektu knihovny DLL. Také nastavte cestu knihovny ve vašem klientském projektu tak, aby zahrnovala knihovny DLL import knihoven z projektu knihovny DLL. A nakonec zkopírujte vytvořenou knihovnu DLL z projektu knihovny DLL do výstupního adresáře sestavení. Tento krok umožňuje, aby klientská aplikace používala stejný kód knihovny DLL, který sestavíte.

::: moniker range="vs-2019"

### <a name="to-create-a-client-app-in-visual-studio-2019"></a>Vytvoření klientské aplikace v aplikaci Visual Studio 2019

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt** a otevřete tak dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Console**. 

1. Z filtrovaného seznamu typů projektů zvolte Konzolová **aplikace** a pak zvolte **Další**. Na další stránce `MathClient` do pole **název** zadejte název projektu a v případě potřeby zadejte umístění projektu.

   ![Pojmenovat klientský projekt](media/mathclient-project-name-2019.png "Pojmenovat klientský projekt")

1. Pro vytvoření projektu klienta klikněte na tlačítko **vytvořit** .

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>Vytvoření klientské aplikace v aplikaci Visual Studio 2017

1. Chcete-li C++ vytvořit aplikaci, která používá knihovnu DLL, kterou jste vytvořili, v řádku nabídek klikněte na položku **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** vyberte v části nainstalovaná  > **C++aplikace**možnost **plocha Windows** . V prostředním podokně vyberte možnost **Průvodce desktopovou plochou systému Windows**. Do textového pole **název** zadejte název projektu `MathClient`.

   ![Pojmenovat klientský projekt](media/mathclient-new-project-name-153.png "Pojmenovat klientský projekt")

1. Kliknutím na **tlačítko OK** spusťte průvodce **projektem aplikace Windows Desktop** . V průvodci vytvořte projekt klientské aplikace kliknutím na **tlačítko OK** .

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Vytvoření klientské aplikace ve starších verzích sady Visual Studio 2017

1. Chcete-li C++ vytvořit aplikaci, která používá knihovnu DLL, kterou jste vytvořili, v řádku nabídek klikněte na položku **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** vyberte v části **nainstalované** > **šablony** > **vizuál C++** položku **Win32** . V prostředním podokně vyberte **Konzolová aplikace Win32**. Do textového pole **název** zadejte název projektu `MathClient`.

   ![Pojmenovat klientský projekt](media/mathclient-project-name.png "Pojmenovat klientský projekt")

1. Kliknutím na tlačítko **OK** zavřete dialogové okno **Nový projekt** a spusťte **Průvodce aplikací Win32**. Na stránce **Přehled** v dialogovém okně **Průvodce aplikací Win32** klikněte na tlačítko **Další** .

1. Na stránce **nastavení aplikace** klikněte v části **Typ aplikace**na položku **Konzolová aplikace** , pokud ještě není vybraná.

1. Kliknutím na tlačítko **Dokončit** vytvořte projekt.

::: moniker-end

Až Průvodce skončí, vytvoří se pro vás minimální projekt konzolové aplikace. Název pro hlavní zdrojový soubor je stejný jako název projektu, který jste zadali dříve. V tomto příkladu je název **MathClient. cpp**. Můžete ji sestavit, ale ještě nepoužívá vaši knihovnu DLL.

Dále pro volání funkcí MathLibrary ve zdrojovém kódu musí projekt zahrnovat soubor MathLibrary. h. Tento hlavičkový soubor můžete zkopírovat do projektu klientské aplikace a pak ho přidat do projektu jako existující položku. Tato metoda může být dobrou volbou pro knihovny třetích stran. Nicméně pokud pracujete na kódu vaší knihovny DLL ve stejnou dobu jako váš klient, může to vést k změnám v jednom hlavičkovém souboru, který není zobrazen v druhém. Chcete-li se tomuto problému vyhnout, můžete změnit cestu k **dalším adresářům zahrnutí** v projektu tak, aby zahrnovala cestu k původní hlavičce.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Přidání hlavičky knihovny DLL do cesty k zahrnutí

1. Kliknutím pravým tlačítkem myši na uzel **MathClient** v **Průzkumník řešení** otevřete dialogové okno **stránky vlastností** .

1. V rozevíracím seznamu **Konfigurace** vyberte možnost **všechny konfigurace** , pokud ještě není vybraná.

1. V levém podokně vyberte v části **vlastnosti** > konfigurace**C/C++** . **Obecné** .

1. V podokně vlastností zaškrtněte políčko vedle rozevíracího seznamu **Další vložené adresáře** a pak zvolte **Upravit**.

   ![Upravte vlastnost další adresáře zahrnutí] . (media/mathclient-additional-include-directories-property.png "Upravte vlastnost další adresáře zahrnutí") .

1. Pokud chcete povolit ovládací prvek pro úpravy, poklikejte na horní podokno dialogového okna **Další vložené adresáře** .

1. V ovládacím prvku pro úpravy zadejte cestu k umístění souboru hlaviček **MathLibrary. h** . Klikněte na šipku dolů a pak zvolte  **\<Upravit >** . Můžete kliknout na ikonu složky a potom se třemi tečkami ( **...** ) přejít do správné složky.
 
   V tomto případě můžete také zadat relativní cestu ze složky, která obsahuje soubory. cpp v klientském projektu, do složky, která obsahuje soubor. h v projektu knihovny DLL. Pokud je váš klientský projekt v samostatném řešení ve stejné složce jako řešení knihovny DLL, relativní cesta by měla vypadat takto:

   `..\MathLibrary\MathLibrary`

   Pokud vaše knihovna DLL a klientské projekty jsou ve stejném řešení, nebo jsou řešení v různých složkách, je nutné odpovídajícím způsobem upravit relativní cestu nebo jinak vyhledat složku pomocí výše popsané metody.

   ![Přidejte umístění záhlaví do vlastnosti další adresáře zahrnutí] . (media/mathclient-additional-include-directories.png "Přidejte umístění záhlaví do vlastnosti další adresáře zahrnutí") .

1. Po zadání cesty k souboru hlaviček v dialogovém okně **Další vložené adresáře** klikněte na tlačítko **OK** , vraťte se do dialogového okna **stránky vlastností** a pak kliknutím na tlačítko **OK** uložte změny.

Nyní můžete zahrnout soubor **MathLibrary. h** a používat funkce, které deklaruje v klientské aplikaci. Nahraďte obsah **MathClient. cpp** pomocí tohoto kódu:

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
// #include "pch.h" Uncomment for Visual Studio 2017 and earlier
#include <iostream>
#include "MathLibrary.h"

int main()
{
    // Initialize a Fibonacci relation sequence.
    fibonacci_init(1, 1);
    // Write out the sequence values until overflow.
    do {
        std::cout << fibonacci_index() << ": "
            << fibonacci_current() << std::endl;
    } while (fibonacci_next());
    // Report count of values written before overflow.
    std::cout << fibonacci_index() + 1 <<
        " Fibonacci sequence values fit in an " <<
        "unsigned 64-bit integer." << std::endl;
}
```

Tento kód může být zkompilován, ale ne propojený, protože linker nemůže najít knihovnu importu potřebnou k sestavení aplikace. Linker musí najít soubor MathLibrary. lib pro úspěšné připojení. Přidejte soubor MathLibrary. lib do sestavení nastavením vlastnosti **Další závislosti** . Znovu můžete zkopírovat soubor knihovny do projektu klientské aplikace, ale v případě vývoje knihovny i klientské aplikace může dojít ke změnám v jedné kopii, která není zobrazená v druhé. Chcete-li se tomuto problému vyhnout, můžete v projektu změnit cestu k **adresářům dalších knihoven** , aby při propojení zahrnovala cestu k původní knihovně.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Přidání knihovny pro import knihoven DLL do projektu

1. Kliknutím pravým tlačítkem myši na uzel **MathClient** v **Průzkumník řešení** otevřete dialogové okno **stránky vlastností** .

1. V rozevíracím seznamu **Konfigurace** vyberte možnost **všechny konfigurace** , pokud ještě není vybraná. Toto nastavení zajišťuje, že cesta je nastavena pro sestavení pro ladění i pro vydání.

1. V levém podokně vyberte **vstup** v části **vlastnosti** > konfigurace**linker**. V podokně vlastností zaškrtněte políčko vedle rozevíracího seznamu **Další závislosti** a pak zvolte **Upravit**.

   ![Úprava vlastnosti Další závislosti](media/mathclient-additional-dependencies-property.png "Úprava vlastnosti Další závislosti")

1. V dialogovém okně **Další závislosti** přidejte `MathLibrary.lib` do seznamu v horním ovládacím prvku pro úpravy.

   ![Přidat závislost knihovny](media/mathclient-additional-dependencies.png "Přidat závislost knihovny")

1. Kliknutím na **tlačítko OK** se vraťte do dialogového okna **stránky vlastností** .

1. V levém podokně vyberte v části **vlastnosti** > konfigurace**linkeru**možnost **Obecné** . V podokně vlastností vyberte rozevírací seznam vedle pole **Další adresáře knihovny** upravit a pak zvolte **Upravit**.

   ![Upravte vlastnost další adresáře knihovny] . (media/mathclient-additional-library-directories-property.png "Upravte vlastnost další adresáře knihovny") .

1. Dvojitým kliknutím v horním podokně dialogového okna **Další adresáře knihovny** povolíte ovládací prvek pro úpravy. V ovládacím prvku pro úpravy zadejte cestu k umístění souboru **MathLibrary. lib** . Je ve složce s názvem `Debug` přímo ve složce řešení. Pokud vytvoříte sestavení pro vydání, výstup bude umístěn do složky s názvem `Release`. Můžete použít následující makro, aby linker mohl najít knihovnu DLL bez ohledu na to, který typ sestavení vytvoříte:

   **Visual Studio 2019:**

   `..\MathLibrary\$(IntDir)`

   **Visual Studio 2017 a starší:**

   `..\..\MathLibrary\$(IntDir)`

   ![Přidat adresář knihovny](media/mathclient-additional-library-directories.png "Přidat adresář knihovny")

1. Jakmile zadáte cestu k souboru knihovny v dialogovém okně **Další adresáře knihovny** , klikněte na tlačítko **OK** , čímž se vrátíte do dialogového okna **stránky vlastností** .

Klientská aplikace se teď může kompilovat a propojit úspěšně, ale pořád nemá vše, co potřebuje ke spuštění. Když operační systém načte vaši aplikaci, vyhledá MathLibrary DLL. Pokud knihovna DLL nenajde v určitých systémových adresářích, cestě k prostředí nebo adresáři místní aplikace, zatížení se nepodaří. Jedním ze způsobů, jak se tomuto problému vyhnout, je zkopírovat knihovnu DLL do adresáře, který obsahuje spustitelný soubor klienta jako součást procesu sestavení. Ke zkopírování knihovny DLL můžete přidat **událost po sestavení** do projektu a přidat příkaz, který zkopíruje knihovnu DLL do výstupního adresáře sestavení. Zadaný příkaz zkopíruje knihovnu DLL pouze v případě, že chybí nebo se změnila a používá makra ke kopírování do a ze správných umístění pro ladění nebo vydání pro vaši konfiguraci.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Zkopírování knihovny DLL v události po sestavení

1. Kliknutím pravým tlačítkem myši na uzel **MathClient** v **Průzkumník řešení** otevřete dialogové okno **stránky vlastností** .

1. V rozevíracím seznamu konfigurace vyberte možnost **všechny konfigurace** , pokud ještě není vybraná.

1. V levém podokně vyberte **událost po sestavení** v části **vlastnosti** > konfigurace**události sestavení**.

1. V podokně vlastností vyberte v poli **příkazový řádek** ovládací prvek pro úpravy a potom zadejte tento příkaz:

   **Visual Studio 2019:**

   `xcopy /y /d "..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

    **Visual Studio 2017 a starší:**

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Přidání příkazu po sestavení](media/mathclient-post-build-command-line.png "Přidání příkazu po sestavení")

1. Kliknutím na tlačítko **OK** uložte změny vlastností projektu.

Klientská aplikace teď má všechno, co potřebuje k sestavování a spouštění. Sestavte aplikaci tak, že na řádku nabídek kliknete na **sestavit** > **řešení sestavení** . Okno **výstup** v aplikaci Visual Studio by mělo mít něco podobného jako v následujícím příkladu v závislosti na vaší verzi sady Visual Studio:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Gratulujeme, vytvořili jste aplikaci, která volá funkce v knihovně DLL. Nyní spusťte aplikaci, abyste viděli, co dělá. Na panelu nabídek vyberte možnost **ladit** > **Spustit bez ladění**. Visual Studio otevře příkazové okno, ve kterém bude program běžet. Poslední část výstupu by měla vypadat takto:

![Spuštění klientské aplikace bez ladění](media/mathclient-run-without-debugging.png "Spuštění klientské aplikace bez ladění")

Stisknutím libovolné klávesy zavřete okno příkazového řádku.

Teď, když jste vytvořili knihovnu DLL a klientskou aplikaci, můžete experimentovat. Zkuste nastavit zarážky v kódu klientské aplikace a spusťte aplikaci v ladicím programu. Podívejte se, co se stane, když zadáte krok do volání knihovny. Do knihovny přidejte další funkce nebo napište jinou klientskou aplikaci, která používá vaši DLL knihovnu.

Při nasazení aplikace je nutné také nasadit knihovny DLL, které používá. Nejjednodušší způsob, jak vytvořit knihovny DLL, které sestavíte nebo které zahrnete z třetích stran, které jsou k dispozici pro vaši aplikaci, je umístit je do stejného adresáře jako aplikace, označované také jako *nasazení v místní aplikaci*. Další informace o nasazení najdete v tématu [nasazení v vizuálu C++ ](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Viz také:

[Volání funkcí knihovny DLL z aplikací Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
