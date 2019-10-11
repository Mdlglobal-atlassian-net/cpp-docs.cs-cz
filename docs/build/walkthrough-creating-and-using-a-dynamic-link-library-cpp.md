---
title: 'Návod: Vytvoření a použití vlastní knihovny DLL (C++)'
description: Slouží C++ k vytvoření knihovny DLL (Dynamic-Link Library) systému Windows v aplikaci Visual Studio.
ms.custom: conceptual
ms.date: 08/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 7bc0cb58cbbe995aa9d74e3ccb627ddc442bd4fb
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "70026034"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Návod: Vytvoření a použití vlastní knihovny DLL (C++)

Tento podrobný návod ukazuje, jak použít integrované vývojové prostředí (IDE) sady Visual Studio k vytvoření vlastní knihovny DLL (Dynamic Link Library) napsané C++ v Microsoft (MSVC). Pak ukazuje, jak použít knihovnu DLL z jiné C++ aplikace. Knihovny DLL (známé také jako *sdílené knihovny* v operačních systémech UNIX) jsou jedním z nejužitečnějších typů součástí Windows. Můžete je použít jako způsob, jak sdílet kód a prostředky a zmenšit velikost svých aplikací. Knihovny DLL také usnadňují službu a rozšiřování aplikací.

V tomto návodu vytvoříte knihovnu DLL, která implementuje některé matematické funkce. Pak vytvoříte konzolovou aplikaci, která používá funkce z knihovny DLL. Získáte také Úvod k některým programovacím technikům a konvencím používaným v knihovnách DLL systému Windows.

Tento názorný postup se zabývá následujícími úlohami:

- Vytvořte projekt knihovny DLL v aplikaci Visual Studio.

- Do knihovny DLL přidejte exportované funkce a proměnné.

- Vytvořte projekt konzolové aplikace v aplikaci Visual Studio.

- Použijte funkce a proměnné importované z knihovny DLL v konzolové aplikaci.

- Spusťte dokončenou aplikaci.

Podobně jako staticky propojená knihovna, knihovna DLL _exportuje_ proměnné, funkce a prostředky podle názvu. Klientská aplikace _importuje_ názvy pro použití proměnných, funkcí a prostředků. Na rozdíl od staticky propojené knihovny Windows spojuje importy v aplikaci s exporty v knihovně DLL v době načítání nebo v době běhu, namísto jejich propojení v době připojení. Systém Windows vyžaduje další informace, které nejsou součástí standardního C++ modelu kompilace, aby bylo možné tato připojení provést. Kompilátor MSVC implementuje některá rozšíření specifická pro společnost Microsoft k C++ poskytnutí těchto dalších informací. Tato rozšíření Vysvětleme.

Tento návod vytvoří dvě řešení sady Visual Studio; ten, který vytváří knihovnu DLL, a jednu, která sestavuje klientskou aplikaci. Knihovna DLL používá konvenci volání jazyka C. Dá se volat z aplikací napsaných v jiných programovacích jazycích, pokud se shoda platforem, konvencí volání a konvence propojení shodují. Klientská aplikace používá _implicitní propojení_, kde Windows propojuje aplikaci s knihovnou DLL při načtení. Toto propojení umožňuje, aby aplikace zavolala funkce poskytnuté knihovnou DLL stejně jako funkce ve staticky propojené knihovně.

Tento návod nezahrnuje některé běžné situace. Kód nezobrazuje použití C++ knihoven DLL jinými programovacími jazyky. Neukazuje, jak [vytvořit knihovnu DLL s pouze prostředky](creating-a-resource-only-dll.md)nebo jak použít [explicitní propojení](linking-an-executable-to-a-dll.md#linking-explicitly) s knihovnou DLL v době běhu, nikoli při načtení. Vše v klidovém prostředí, pomocí MSVC a sady Visual Studio můžete provádět všechny tyto akce.

Odkazy na Další informace o knihovnách DLL naleznete v tématu [CreateC++ C/dlls in Visual Studio](dlls-in-visual-cpp.md). Další informace o implicitním propojení a explicitním propojení najdete v tématu [určení, kterou propojovací metodu použít](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Informace o vytváření C++ knihoven DLL pro použití s programovacími jazyky, které používají konvence propojení jazyka c, naleznete v tématu [Exportování C++ funkcí pro použití ve spustitelných souborech jazyka c](exporting-cpp-functions-for-use-in-c-language-executables.md). Informace o tom, jak vytvořit knihovny DLL pro použití s jazyky rozhraní .NET, naleznete v tématu [volání funkcí knihovny DLL z aplikací Visual Basic](calling-dll-functions-from-visual-basic-applications.md).

## <a name="prerequisites"></a>Požadavky

- Počítač se systémem Microsoft Windows 7 nebo novější verzí. Pro nejlepší vývojové prostředí doporučujeme Windows 10.

::: moniker range=">=vs-2017"

- Kopie sady Visual Studio. Informace o tom, jak stáhnout a nainstalovat Visual Studio, najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio). Když spustíte instalační program, ujistěte se, že je zaškrtnuté políčko **vývoj pro stolní počítače pomocí C++**  úlohy. Nedělejte si starosti, pokud jste při instalaci sady Visual Studio nenainstalovali tuto úlohu. Instalační program můžete spustit znovu a nainstalovat hned.

   ![Vývoj desktopových C++ aplikací pomocí](media/desktop-development-with-cpp.png "Vývoj desktopových C++ aplikací pomocí")

::: moniker-end

::: moniker range="vs-2015"

- Kopie sady Visual Studio. Informace o tom, jak stáhnout a nainstalovat Visual Studio 2015, najdete v tématu [instalace sady Visual studio 2015](/visualstudio/install/install-visual-studio-2015?view=vs-2015). Použijte **vlastní** instalaci pro instalaci C++ kompilátoru a nástrojů, protože nejsou nainstalovány ve výchozím nastavení.

::: moniker-end

- Porozumění základům používání integrovaného vývojového prostředí (IDE) sady Visual Studio Pokud jste už používali desktopové aplikace pro Windows, můžete si je nechat. Úvod najdete v tématu [prohlídka funkcí rozhraní IDE sady Visual Studio](/visualstudio/ide/visual-studio-ide).

- Seznamte se s dostatečným základem C++ jazyka, který se má sledovat. Nedělejte si starosti, nemůžeme nic složitě.

::: moniker range="vs-2017"

> [!NOTE]
> Tento návod předpokládá, že používáte Visual Studio 2017 verze 15,9 nebo novější. Některé starší verze sady Visual Studio 2017 obsahovaly vady v šablonách kódu nebo používaly jiná dialogová okna uživatelského rozhraní. Chcete-li se vyhnout problémům, použijte Instalační program pro Visual Studio k aktualizaci sady Visual Studio 2017 na verzi 15,9 nebo novější.

::: moniker-end

## <a name="create-the-dll-project"></a>Vytvoření projektu knihovny DLL

V této sadě úkolů vytvoříte projekt pro knihovnu DLL, přidáte kód a sestavíte jej. Začněte tím, že spustíte Visual Studio IDE a přihlásíte se, pokud potřebujete. Pokyny se mírně liší v závislosti na verzi sady Visual Studio, kterou používáte. Ujistěte se, že je v ovládacím prvku v levém horním rohu této stránky vybraná správná verze.

::: moniker range=">=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>Vytvoření projektu knihovny DLL v aplikaci Visual Studio 2019

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt** a otevřete tak dialogové okno **vytvořit nový projekt** .

   ![Vytvořit nový projekt knihovny DLL](media/create-new-dll-project-2019.png "Vytvoření projektu MathLibrary")

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Library**.

1. Z filtrovaného seznamu typů projektů vyberte **dynamická knihovna (DLL)** a pak klikněte na tlačítko **Další**.

1. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** *MathLibrary* a zadejte název projektu. Ponechte výchozí **umístění** a hodnoty **názvu řešení** . Nastavte **řešení** na **vytvořit nové řešení**. Zrušte zaškrtnutí políčka **umístit řešení a projekt do stejného adresáře** , pokud je zaškrtnuto.

1. Kliknutím na tlačítko **vytvořit** vytvořte projekt.

Po vytvoření řešení můžete zobrazit vygenerovaný projekt a zdrojové soubory v okně **Průzkumník řešení** v aplikaci Visual Studio.

![Vygenerované řešení v aplikaci Visual Studio](media/mathlibrary-solution-explorer-162.png "Vygenerované řešení v aplikaci Visual Studio")

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>Vytvoření projektu knihovny DLL v aplikaci Visual Studio 2017

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt** . otevře se dialogové okno **Nový projekt** .

1. V levém podokně dialogového okna **Nový projekt** vyberte možnost **nainstalované** >   > **prostředí Visual C++**  **Windows Desktop**. V prostředním podokně vyberte **Knihovna DLL (Dynamic-Link Library)** . Do pole **název** zadejte *MathLibrary* a zadejte název projektu. Ponechte výchozí **umístění** a hodnoty **názvu řešení** . Nastavte **řešení** na **vytvořit nové řešení**. Pokud není zaškrtnuté, vyhledejte **v řešení vytvořit adresář** .

   ![Pojmenování projektu MathLibrary](media/mathlibrary-new-project-name-159.png "Pojmenování projektu MathLibrary")

1. Kliknutím na tlačítko **OK** vytvořte projekt.

Po vytvoření řešení můžete zobrazit vygenerovaný projekt a zdrojové soubory v okně **Průzkumník řešení** v aplikaci Visual Studio.

![Vygenerované řešení v aplikaci Visual Studio](media/mathlibrary-solution-explorer-159.png "Vygenerované řešení v aplikaci Visual Studio")

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-dll-project-in-visual-studio-2015-and-older-versions"></a>Vytvoření projektu knihovny DLL v aplikaci Visual Studio 2015 a starších verzích

1. Na panelu nabídek vyberte **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte položku **nainstalované** > **šablony**a vyberte možnost **vizuál C++** a potom v prostředním podokně vyberte položku **Konzolová aplikace Win32**. Zadáním *MathLibrary* do textového pole **název** zadejte název projektu. Ponechte výchozí **umístění** a hodnoty **názvu řešení** . Nastavte **řešení** na **vytvořit nové řešení**. Pokud není zaškrtnuté, vyhledejte **v řešení vytvořit adresář** .

   ![Pojmenování projektu MathLibrary](media/mathlibrary-project-name.png "Pojmenování projektu MathLibrary")

1. Kliknutím na tlačítko **OK** zavřete dialogové okno **Nový projekt** a spusťte **Průvodce aplikací Win32**.

   ![Průvodce aplikací Win32 – přehled](media/mathlibrary-project-wizard-1.png "Průvodce aplikací Win32 – přehled")

1. Zvolte **Další** tlačítko. Na stránce **nastavení aplikace** klikněte v části **Typ aplikace**na položku **Knihovna DLL**.

   ![Průvodce vytvořením knihovny DLL v aplikaci Win32](media/mathlibrary-project-wizard-2.png "Průvodce vytvořením knihovny DLL v aplikaci Win32")

1. Kliknutím na tlačítko **Dokončit** vytvořte projekt.

Až průvodce dokončí řešení, můžete zobrazit vygenerovaný projekt a zdrojové soubory v okně **Průzkumník řešení** v aplikaci Visual Studio.

![Vygenerované řešení v aplikaci Visual Studio](media/mathlibrary-solution-explorer-153.png "Vygenerované řešení v aplikaci Visual Studio")

::: moniker-end

Nyní tato knihovna DLL nemá příliš mnoho. V dalším kroku vytvoříte hlavičkový soubor pro deklarování funkcí, které exportuje vaše knihovna DLL, a pak přidáte definice funkcí do knihovny DLL, aby byly užitečnější.

### <a name="to-add-a-header-file-to-the-dll"></a>Přidání souboru hlaviček do knihovny DLL

1. Chcete-li vytvořit hlavičkový soubor pro vaše funkce, v řádku nabídek vyberte možnost **projekt** > **Přidat novou položku**.

1. V dialogovém okně **Přidat novou položku** v levém podokně vyberte možnost **C++Visual**. V prostředním podokně vyberte **hlavičkový soubor (. h)** . Jako název hlavičkového souboru zadejte *MathLibrary. h* .

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

Všimněte si příkazů preprocesoru v horní části souboru. Nová šablona projektu pro projekt knihovny DLL přidává **exporty _ProjectName_&#95;EXPORTS** do definovaných maker preprocesoru. V tomto příkladu definuje Visual Studio **exporty&#95;MATHLIBRARY** při sestavení projektu knihovny DLL MATHLIBRARY.

Když je definováno makro **MATHLIBRARY&#95;EXPORTS** , makro **rozhraní&#95;MATHLIBRARY API** nastaví `__declspec(dllexport)` modifikátor v deklaracích funkce. Tento modifikátor instruuje kompilátor a linker, aby exportovali funkci nebo proměnnou z knihovny DLL pro použití v jiných aplikacích. Pokud **MATHLIBRARY&#95;exporty** nejsou definovány, například když je hlavičkový soubor součástí klientské aplikace, `__declspec(dllimport)` **rozhraní MATHLIBRARY&#95;API** použije pro deklarace modifikátor. Tento modifikátor optimalizuje import funkce nebo proměnné v aplikaci. Další informace naleznete v tématu [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Přidání implementace do knihovny DLL

::: moniker range=">=vs-2019"

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **zdrojové soubory** a vyberte možnost **Přidat** > **novou položku**. Vytvořte nový soubor. cpp s názvem *MathLibrary. cpp*stejným způsobem, jako jste přidali nový hlavičkový soubor v předchozím kroku.

1. V okně editoru vyberte kartu pro **MathLibrary. cpp** , pokud je již otevřena. Pokud ne, v **Průzkumník řešení**dvakrát klikněte na **MathLibrary. cpp** ve složce **zdrojové soubory** projektu **MathLibrary** a otevřete ji.

1. V editoru nahraďte obsah souboru MathLibrary. cpp následujícím kódem:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "pch.h" // use stdafx.h in Visual Studio 2017 and earlier
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

::: moniker-end

::: moniker range="<=vs-2017"

1. V okně editoru vyberte kartu pro **MathLibrary. cpp** , pokud je již otevřena. Pokud ne, v **Průzkumník řešení**dvakrát klikněte na **MathLibrary. cpp** ve složce **zdrojové soubory** projektu **MathLibrary** a otevřete ji.

1. V editoru nahraďte obsah souboru MathLibrary. cpp následujícím kódem:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019 and later
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

::: moniker-end

Chcete-li ověřit, že vše funguje zatím, zkompilujte dynamickou knihovnu. Chcete-li kompilovat, klikněte na tlačítko **sestavit** > **sestavení** na řádku nabídek. Knihovna DLL a související výstupy kompilátoru jsou umístěny do složky s názvem *ladění* přímo pod složkou řešení. Pokud vytvoříte sestavení pro vydání, výstup se umístí do složky s názvem *release*. Výstup by měl vypadat přibližně takto:

::: moniker range=">=vs-2019"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>pch.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="vs-2017"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="vs-2015"

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

::: moniker-end

Gratulujeme, vytvořili jste knihovnu DLL pomocí sady Visual Studio! V dalším kroku vytvoříte klientskou aplikaci, která používá funkce exportované knihovnou DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Vytvořit klientskou aplikaci, která používá knihovnu DLL

Když vytváříte knihovnu DLL, zamyslete se nad tím, jak ji klientské aplikace mohou používat. Pro volání funkcí nebo přístup k datům exportovaným knihovnou DLL musí mít zdrojový kód klienta k dispozici deklarace v době kompilace. V době připojení linker vyžaduje informace pro vyřešení volání funkce nebo přístupu k datům. Knihovna DLL poskytuje tyto informace v *knihovně importu*, což je soubor, který obsahuje informace o tom, jak najít funkce a data namísto skutečného kódu. A v době běhu musí být knihovna DLL k dispozici klientovi, v umístění, které může operační systém najít.

Bez ohledu na to, jestli je to vaše vlastní nebo od třetí strany, váš projekt klientské aplikace potřebuje k použití knihovny DLL několik informací. Musí najít hlavičky, které deklaruje exporty knihoven DLL, knihovny importů pro Linker a samotnou knihovnu DLL. Jedním z řešení je zkopírovat všechny tyto soubory do klientského projektu. Pro knihovny DLL třetích stran, které se při vývoji vašeho klienta pravděpodobně nemění, může být tato metoda nejlepším způsobem jejich použití. Pokud ale také vytváříte knihovnu DLL, je lepší se vyhnout duplicitám. Pokud vytváříte místní kopii souborů DLL, které jsou ve vývoji, můžete omylem změnit soubor hlaviček v jednom kopírování, ale ne na druhém, nebo použít neaktuální knihovnu.

Chcete-li předejít nesynchronizaci kódu, doporučujeme nastavit cestu zahrnutí v projektu klienta, aby zahrnovala soubory hlaviček DLL přímo z projektu knihovny DLL. Také nastavte cestu knihovny ve vašem klientském projektu tak, aby zahrnovala knihovny DLL import knihoven z projektu knihovny DLL. A nakonec zkopírujte vytvořenou knihovnu DLL z projektu knihovny DLL do výstupního adresáře sestavení klienta. Tento krok umožňuje, aby klientská aplikace používala stejný kód knihovny DLL, který sestavíte.

::: moniker range=">=vs-2019"

### <a name="to-create-a-client-app-in-visual-studio"></a>Vytvoření klientské aplikace v aplikaci Visual Studio

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt** a otevřete tak dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Console**.

1. Z filtrovaného seznamu typů projektů zvolte Konzolová **aplikace** a pak zvolte **Další**.

1. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** *MathClient* a zadejte název projektu. Ponechte výchozí **umístění** a hodnoty **názvu řešení** . Nastavte **řešení** na **vytvořit nové řešení**. Zrušte zaškrtnutí políčka **umístit řešení a projekt do stejného adresáře** , pokud je zaškrtnuto.

   ![Pojmenovat klientský projekt](media/mathclient-project-name-2019.png "Pojmenovat klientský projekt")

1. Pro vytvoření projektu klienta klikněte na tlačítko **vytvořit** .

Pro vás se vytvoří projekt s minimální konzolou aplikace. Název pro hlavní zdrojový soubor je stejný jako název projektu, který jste zadali dříve. V tomto příkladu je název **MathClient. cpp**. Můžete ji sestavit, ale ještě nepoužívá vaši knihovnu DLL.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>Vytvoření klientské aplikace v aplikaci Visual Studio 2017

1. Chcete-li C++ vytvořit aplikaci, která používá knihovnu DLL, kterou jste vytvořili, v řádku nabídek klikněte na položku **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** vyberte v části nainstalovaná > **C++aplikace**možnost **plocha Windows** . V prostředním podokně vyberte **Konzolová aplikace systému Windows**. Do pole **název** upravte zadejte název projektu *MathClient*.  Ponechte výchozí **umístění** a hodnoty **názvu řešení** . Nastavte **řešení** na **vytvořit nové řešení**. Pokud není zaškrtnuté, vyhledejte **v řešení vytvořit adresář** .

   ![Pojmenovat klientský projekt](media/mathclient-new-project-name-159.png "Pojmenovat klientský projekt")

1. Kliknutím na **tlačítko OK** vytvořte projekt klientské aplikace.

Pro vás se vytvoří projekt s minimální konzolou aplikace. Název pro hlavní zdrojový soubor je stejný jako název projektu, který jste zadali dříve. V tomto příkladu je název **MathClient. cpp**. Můžete ji sestavit, ale ještě nepoužívá vaši knihovnu DLL.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-visual-studio-2015"></a>Vytvoření klientské aplikace v aplikaci Visual Studio 2015

1. Chcete-li C++ vytvořit aplikaci, která používá knihovnu DLL, kterou jste vytvořili, v řádku nabídek klikněte na položku **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** vyberte v části **nainstalované** > **šablony** > **vizuál C++** položku **Win32** . V prostředním podokně vyberte **Konzolová aplikace Win32**. Do pole **název** upravte zadejte název projektu *MathClient*. Ponechte výchozí **umístění** a hodnoty **názvu řešení** . Nastavte **řešení** na **vytvořit nové řešení**. Pokud není zaškrtnuté, vyhledejte **v řešení vytvořit adresář** .

   ![Pojmenovat klientský projekt](media/mathclient-project-name.png "Pojmenovat klientský projekt")

1. Kliknutím na tlačítko **OK** zavřete dialogové okno **Nový projekt** a spusťte **Průvodce aplikací Win32**. Na stránce **Přehled** v dialogovém okně **Průvodce aplikací Win32** klikněte na tlačítko **Další** .

1. Na stránce **nastavení aplikace** klikněte v části **Typ aplikace**na položku **Konzolová aplikace** , pokud ještě není vybraná.

1. Kliknutím na tlačítko **Dokončit** vytvořte projekt.

Až Průvodce skončí, vytvoří se pro vás minimální projekt konzolové aplikace. Název pro hlavní zdrojový soubor je stejný jako název projektu, který jste zadali dříve. V tomto příkladu je název **MathClient. cpp**. Můžete ji sestavit, ale ještě nepoužívá vaši knihovnu DLL.

::: moniker-end

Dále pro volání funkcí MathLibrary ve zdrojovém kódu musí projekt zahrnovat soubor *MathLibrary. h* . Tento hlavičkový soubor můžete zkopírovat do projektu klientské aplikace a pak ho přidat do projektu jako existující položku. Tato metoda může být dobrou volbou pro knihovny třetích stran. Nicméně pokud pracujete na kódu pro knihovnu DLL a klienta současně, soubory hlaviček by mohly být mimo synchronizaci. Chcete-li se tomuto problému vyhnout, nastavte cestu k **dalším adresářům include** v projektu tak, aby zahrnovala cestu k původní hlavičce.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Přidání hlavičky knihovny DLL do cesty k zahrnutí

1. Kliknutím pravým tlačítkem myši na uzel **MathClient** v **Průzkumník řešení** otevřete dialogové okno **stránky vlastností** .

1. V rozevíracím seznamu **Konfigurace** vyberte možnost **všechny konfigurace** , pokud ještě není vybraná.

1. V levém podokně vyberte **vlastnosti** >  > konfigurace**C/C++** **Obecné**.

1. V podokně vlastností zaškrtněte políčko vedle rozevíracího seznamu **Další vložené adresáře** a pak zvolte **Upravit**.

   ![Upravte vlastnost další adresáře zahrnutí](media/mathclient-additional-include-directories-property.png "Upravte vlastnost další adresáře zahrnutí")

1. Pokud chcete povolit ovládací prvek pro úpravy, poklikejte na horní podokno dialogového okna **Další vložené adresáře** . Případně můžete vybrat ikonu složky a vytvořit novou položku.

1. V ovládacím prvku pro úpravy zadejte cestu k umístění souboru hlaviček **MathLibrary. h** . Můžete vybrat ovládací prvek se třemi tečkami ( **...** ) a přejít do správné složky.

   Můžete také zadat relativní cestu ze zdrojových souborů klienta do složky, která obsahuje soubory hlaviček DLL. Pokud jste postupovali podle pokynů k umístění projektu klienta do samostatného řešení z knihovny DLL, relativní cesta by měla vypadat takto:

   `..\..\MathLibrary\MathLibrary`

   Pokud je vaše knihovna DLL a klientské projekty ve stejném řešení, relativní cesta může vypadat takto:

   `..\MathLibrary`

   Pokud jsou knihovny DLL a klientské projekty v jiných složkách, upravte relativní cestu tak, aby odpovídala. Případně můžete vyhledat složku pomocí ovládacího prvku tři tečky.

   ![Přidejte umístění záhlaví do vlastnosti další adresáře zahrnutí](media/mathclient-additional-include-directories.png "Přidejte umístění záhlaví do vlastnosti další adresáře zahrnutí")

1. Po zadání cesty k souboru hlaviček v dialogovém okně **Další vložené adresáře** klikněte na tlačítko **OK** . V dialogovém okně **stránky vlastností** kliknutím na tlačítko **OK** uložte změny.

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

Tento kód může být zkompilován, ale není propojen. Pokud nyní vytvoříte klientskou aplikaci, zobrazí se v seznamu chyb několik chyb LINKERŮ LNK2019. Důvodem je, že v projektu chybí nějaké informace: Neurčili jste, že váš projekt ještě není závislý na knihovně *MathLibrary. lib* . A, neřekli jste linker, jak najít soubor *MathLibrary. lib* .

Chcete-li tento problém vyřešit, můžete zkopírovat soubor knihovny přímo do projektu klientské aplikace. Linker ho najde a použije automaticky. Pokud je však knihovna i klientská aplikace ve vývoji, může to vést k změnám v jedné kopii, která není zobrazená v druhé. Chcete-li se tomuto problému vyhnout, můžete nastavit vlastnost **Další závislosti** a sdělit systému sestavení, že váš projekt závisí na *MathLibrary. lib*. A v projektu můžete nastavit další cestu k **adresářům knihovny** , aby při propojení zahrnovala cestu k původní knihovně.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Přidání knihovny pro import knihoven DLL do projektu

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel **MathClient** a kliknutím na **vlastnosti** otevřete dialogové okno **stránky vlastností** .

1. V rozevíracím seznamu **Konfigurace** vyberte možnost **všechny konfigurace** , pokud ještě není vybraná. Zajišťuje, aby se všechny změny vlastností projevily pro sestavení ladění i vydaných verzí.

1. V levém podokně vyberte **Konfigurace vlastnosti** > **linker** > **input**. V podokně vlastností zaškrtněte políčko vedle rozevíracího seznamu **Další závislosti** a pak zvolte **Upravit**.

   ![Úprava vlastnosti Další závislosti](media/mathclient-additional-dependencies-property.png "Úprava vlastnosti Další závislosti")

1. V dialogovém okně **Další závislosti** přidejte *MathLibrary. lib* do seznamu v horním ovládacím prvku pro úpravy.

   ![Přidat závislost knihovny](media/mathclient-additional-dependencies.png "Přidat závislost knihovny")

1. Kliknutím na **tlačítko OK** se vraťte do dialogového okna **stránky vlastností** .

1. V levém podokně vyberte **konfigurační vlastnosti** > **linker** > **Obecné**. V podokně vlastností vyberte rozevírací seznam vedle pole **Další adresáře knihovny** upravit a pak zvolte **Upravit**.

   ![Upravte vlastnost další adresáře knihovny.](media/mathclient-additional-library-directories-property.png "Upravte vlastnost další adresáře knihovny")

1. Dvojitým kliknutím v horním podokně dialogového okna **Další adresáře knihovny** povolíte ovládací prvek pro úpravy. V ovládacím prvku pro úpravy zadejte cestu k umístění souboru **MathLibrary. lib** . Ve výchozím nastavení se nachází ve složce s názvem *ladění* přímo ve složce řešení dll. Pokud vytvoříte sestavení pro vydání, soubor se umístí do složky s názvem *release*. Můžete použít `$(IntDir)` makro, aby linker mohl najít vaši knihovnu DLL bez ohledu na to, který typ sestavení vytvoříte. Pokud jste postupovali podle pokynů k umístění projektu klienta do samostatného řešení z projektu knihovny DLL, relativní cesta by měla vypadat takto:

   `..\..\MathLibrary\$(IntDir)`

   Pokud je vaše knihovna DLL a klientské projekty ve stejném řešení, relativní cesta by měla vypadat takto:

   `..\MathLibrary\$(IntDir)`

   ![Přidat adresář knihovny](media/mathclient-additional-library-directories.png "Přidat adresář knihovny")

1. Jakmile zadáte cestu k souboru knihovny v dialogovém okně **Další adresáře knihovny** , klikněte na tlačítko **OK** , čímž se vrátíte do dialogového okna **stránky vlastností** . Kliknutím na **tlačítko OK** uložte změny vlastností.

Klientská aplikace se teď může kompilovat a propojit úspěšně, ale pořád nemá vše, co potřebuje ke spuštění. Když operační systém načte vaši aplikaci, vyhledá MathLibrary DLL. Pokud knihovna DLL nenajde v určitých systémových adresářích, cestě k prostředí nebo adresáři místní aplikace, zatížení se nepodaří. V závislosti na operačním systému se zobrazí chybová zpráva podobná této:

![Chyba nenalezené knihovny DLL MathLibrary](media/mathclient-system-error-mathlibrary-dll-not-found.png "Chyba nenalezené knihovny DLL MathLibrary")

Jedním ze způsobů, jak se tomuto problému vyhnout, je zkopírovat knihovnu DLL do adresáře, který obsahuje spustitelný soubor klienta jako součást procesu sestavení. Můžete přidat **událost po sestavení** do projektu a přidat příkaz, který zkopíruje knihovnu DLL do výstupního adresáře sestavení. Zadaný příkaz zkopíruje knihovnu DLL pouze v případě, že chybí nebo se změnila. Používá makra ke kopírování do a z umístění pro ladění nebo vydání na základě konfigurace sestavení.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Zkopírování knihovny DLL v události po sestavení

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel **MathClient** a kliknutím na **vlastnosti** otevřete dialogové okno **stránky vlastností** .

1. V rozevíracím seznamu **Konfigurace** vyberte možnost **všechny konfigurace** , pokud ještě není vybraná.

1. V levém podokně vyberte **vlastnosti** > konfigurace událost**sestavení** > události**po sestavení**.

1. V podokně vlastností vyberte v poli **příkazový řádek** ovládací prvek pro úpravy. Pokud jste postupovali podle pokynů k umístění projektu klienta do samostatného řešení z projektu knihovny DLL, pak zadejte tento příkaz:

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   Pokud je vaše knihovna DLL a klientské projekty ve stejném adresáři řešení, zadejte tento příkaz:

   `xcopy /y /d "..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Přidání příkazu po sestavení](media/mathclient-post-build-command-line.png "Přidání příkazu po sestavení")

1. Kliknutím na tlačítko **OK** uložte změny vlastností projektu.

Klientská aplikace teď má všechno, co potřebuje k sestavování a spouštění. Sestavte aplikaci tak, že na řádku nabídek kliknete na **sestavit** > **řešení sestavení** . Okno **výstup** v aplikaci Visual Studio by mělo mít něco podobného jako v následujícím příkladu v závislosti na vaší verzi sady Visual Studio:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Gratulujeme, vytvořili jste aplikaci, která volá funkce v knihovně DLL. Nyní spusťte aplikaci, abyste viděli, co dělá. Na panelu nabídek vyberte možnost **ladit** > **Spustit bez ladění**. Visual Studio otevře příkazové okno, ve kterém bude program běžet. Poslední část výstupu by měla vypadat takto:

![Spuštění klientské aplikace bez ladění](media/mathclient-run-without-debugging.png "Spuštění klientské aplikace bez ladění")

Stisknutím libovolné klávesy zavřete okno příkazového řádku.

Teď, když jste vytvořili knihovnu DLL a klientskou aplikaci, můžete experimentovat. Zkuste nastavit zarážky v kódu klientské aplikace a spusťte aplikaci v ladicím programu. Podívejte se, co se stane, když zadáte krok do volání knihovny. Do knihovny přidejte další funkce nebo napište jinou klientskou aplikaci, která používá vaši DLL knihovnu.

Při nasazení aplikace je nutné také nasadit knihovny DLL, které používá. Nejjednodušší způsob, jak vytvořit knihovny DLL, které sestavíte, nebo které jste zahrnuli ze třetích stran, je k dispozici, aby byly vloženy do stejného adresáře jako vaše aplikace. Je známý jako *nasazení v místní aplikaci*. Další informace o nasazení najdete v tématu [nasazení v vizuálu C++ ](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Viz také:

[Volání funkcí knihovny DLL z aplikací Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
