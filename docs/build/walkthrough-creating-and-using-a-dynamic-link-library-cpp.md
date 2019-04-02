---
title: 'Návod: Vytvoření a použití vlastní dynamické propojení knihovny (C++)'
ms.custom: conceptual
ms.date: 09/24/2018
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 248b423659d026774d4945ee6330a39dc4c6e16e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770145"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Návod: Vytvoření a použití vlastní dynamické propojení knihovny (C++)

Tento podrobný návod ukazuje, jak pomocí integrovaného vývojového prostředí sady Visual Studio můžete vytvořit vlastní dynamická knihovna (DLL) napsané v jazyce C++ a použít ji z jiné aplikace C++. Knihovny DLL patří mezi nejužitečnější typy součástí Windows. Můžete je jako způsob, jak sdílet kód a prostředky, zmenšení velikosti aplikace a aby bylo snazší rozšíření aplikací a služeb. V tomto názorném postupu vytvořit knihovnu DLL, která implementuje některé matematické funkce a pak vytvořte konzolovou aplikaci, která používá funkcí z DLL Knihovny. Na cestě vám představíme některé programovací techniky a konvencemi použitými v knihovnách DLL Windows.

Tento návod pokrývá následující úkoly:

- Vytvoření projektu knihovny DLL v sadě Visual Studio.

- Přidáte do knihovny DLL exportovaných funkcí a proměnných.

- Vytvoření projektu konzolové aplikace v sadě Visual Studio.

- Pomocí funkce a proměnné naimportované z knihovny DLL v konzolovou aplikaci.

- Spusťte dokončenou aplikaci.

Staticky propojené knihovny, knihovny DLL, jako jsou _exportuje_ proměnné, funkce a prostředky podle názvu a vaše aplikace _importuje_ tyto názvy používat tyto proměnné, funkce a prostředky. Na rozdíl od staticky propojené knihovny Windows se připojí k exportů v knihovně DLL v okamžiku načtení nebo v době běhu, namísto připojení v době spojení importy ve vaší aplikaci. Windows vyžaduje dodatečné informace, které nejsou součástí standardní model kompilace C++ k vytvoření těchto připojení. Kompilátor MSVC implementuje některá rozšíření specifické pro společnost Microsoft c++ poskytuje tyto dodatečné informace. Tato rozšíření vám vysvětlíme, jak budeme.

Tento návod vytvoří dvě řešení sady Visual Studio; ten, který vytvoří knihovnu DLL a ten, který sestaví klientské aplikace. Knihovnu DLL používá konvence volání jazyka C, takže může být volána z aplikace vytvořené pomocí jiných jazycích, za předpokladu, platformy a volání a konvence propojení shodovat. Tato aplikace používá klienta _implicitní propojení_, ve kterém Windows odkazy na knihovny DLL v okamžiku načtení aplikace. Toto propojení umožní aplikaci volání funkcí knihovny DLL zadaný stejně jako funkce v staticky propojené knihovny.

Tento názorný postup nezahrnuje některé běžné situace. Použití knihovny DLL jazyka C++ jiné programovací jazyky nezobrazí. Vytvoření knihovny DLL pouze prostředků nezobrazí. Nezobrazí ani použití explicitní načtení knihovny DLL v době běhu, spíše než v okamžiku načtení. Buďte bez obav, můžete použít Visual C++ k provádění těchto akcí. Odkazy na další informace o knihovnách DLL naleznete v části [knihovny DLL v jazyce Visual C++](dlls-in-visual-cpp.md). Další informace o implicitní a explicitní propojení najdete v tématu [určující, kterou propojovací metodu použít](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Informace o vytváření knihovny DLL C++ pro použití s programovací jazyky, které používají jazyk C konvence propojení najdete v tématu [export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md). Informace o tom, jak vytvořit knihovny DLL pro použití s jazyky rozhraní .NET najdete v tématu [volání funkcí knihovny DLL z aplikací Visual Basic](calling-dll-functions-from-visual-basic-applications.md).

Tento návod používá Visual Studio 2017, ale kód a většina pokyny platí pro starší verze. Postup pro vytváření nových projektů změnit, spouští se v sadě Visual Studio 2017 verze 15.3. Tento návod popisuje, jak vytvářet projekty pro novější i starší verze. Vyhledejte kroky, které odpovídají verzi sady Visual Studio.

## <a name="prerequisites"></a>Požadavky

- Počítač, na kterém běží Microsoft Windows 7 nebo novější verze. Doporučujeme pro nejlepší vývojové prostředí Windows 10.

- A copy of Visual Studio 2017. Informace o tom, jak stáhnout a nainstalovat sadu Visual Studio najdete v tématu [instalace sady Visual Studio 2017](/visualstudio/install/install-visual-studio). Když spustíte instalační program, ujistěte se, že **vývoj desktopových aplikací pomocí C++** úlohy je zaškrtnuté políčko. Nedělejte si starosti, pokud je tato úloha nenainstaloval při instalaci sady Visual Studio. Můžete znovu spustit instalační program a jeho instalaci.

   ![Vývoj desktopových aplikací pomocí C++](media/desktop-development-with-cpp.png "vývoj desktopových aplikací pomocí C++")

- Znalost základní informace o používání integrovaného vývojového prostředí sady Visual Studio. Pokud jste používali aplikace klasické pracovní plochy Windows před, můžete pravděpodobně udržovat. Úvodní informace najdete v tématu [IDE sady Visual Studio o základních charakteristikách](/visualstudio/ide/visual-studio-ide).

- Pochopení dostatek základy jazyka C++ spolu s příkladem sledovat. Nedělejte si starosti, jsme nic nedělají nic složitého.

## <a name="create-the-dll-project"></a>Vytvoření projektu knihovny DLL

V této sadě úlohy vytvoření projektu pro vaši knihovnu DLL, přidat kód a sestavte ho. Pokud chcete začít, spusťte Visual Studio IDE a přihlásit, pokud je potřeba. Pokyny pro Visual Studio 2017 verze 15.3 být první. Pokyny pro starší verze později, pokud je potřeba proto přeskočit přímo.

### <a name="to-create-a-dll-project-in-visual-studio-2017-version-153-or-later"></a>Vytvoření projektu knihovny DLL v sadě Visual Studio 2017 verze 15.3 nebo novější

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu** otevřít **nový projekt** dialogové okno.

1. V levém podokně **nový projekt** dialogového okna rozbalte **nainstalováno** a **Visual C++** v případě potřeby a klikněte na tlačítko **Windows Desktop** . V prostředním podokně vyberte **desktopový Průvodce pro Windows**. Zadejte `MathLibrary` v **název** pole zadejte název projektu.

   ![Pojmenujte projekt MathLibrary](media/mathlibrary-new-project-name-153.png "pojmenujte projekt MathLibrary")

1. Zvolte **OK** tlačítka Zavřít **nový projekt** dialogu a začněte **desktopový projekt Windows** průvodce.

1. V **Windows desktopový projekt** průvodce, v části **typ aplikace**vyberte **dynamická knihovna (.dll)**.

   ![Vytvoření knihovny DLL v Průvodci desktopový projekt Windows](media/mathlibrary-desktop-project-wizard-dll.png "vytvoření knihovny DLL v Průvodci desktopový projekt Windows")

1. Zvolte **OK** tlačítko pro vytvoření projektu.

> [!NOTE]
> Opravte problém v sadě Visual Studio 2017 verze 15.3 je potřeba provést další kroky. Postupujte podle těchto pokynů můžete zobrazit, pokud je potřeba tuto změnu provést.
>
>1. V **Průzkumníka řešení**, pokud již není vybrána, vyberte **MathLibrary** projektu v rámci **řešení "MathLibrary"**.
>
>1. V panelu nabídky zvolte **projektu** > **vlastnosti**.
>
>1. V levém podokně **stránky vlastností** dialogu **preprocesor** pod **vlastnosti konfigurace** > **C/C++**. Zkontrolujte obsah **Definice preprocesoru** vlastnost.<br/><br/>![Zkontrolujte vlastnost Definice preprocesoru](media/mathlibrary-153bug-preprocessor-definitions-check.png "Zkontrolujte vlastnost Definice preprocesoru")<br/><br/>Pokud se zobrazí **MATHLIBRARY&#95;EXPORTY** v **Definice preprocesoru** seznamu, pak nemusíte nic měnit. Pokud se zobrazí **MathLibrary&#95;EXPORTY** místo toho pokračujte následujícím postupem.
>
>1. V horní části **stránky vlastností** dialogové okno Změnit **konfigurace** rozevíracího seznamu **všechny konfigurace**.
>
>1. V podokně vlastností vyberte ovládací prvek rozevírací seznam vedle pole pro úpravy pro **Definice preprocesoru**a klikněte na tlačítko **upravit**.<br/><br/>![Upravit vlastnost Definice preprocesoru](media/mathlibrary-153bug-preprocessor-definitions-property.png "upravit vlastnost Definice preprocesoru")
>
>1. V horním podokně **Definice preprocesoru** dialogovém okně Přidat nový symbol `MATHLIBRARY_EXPORTS`.<br/><br/>![Přidejte MATHLIBRARY_EXPORTS symbol](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "přidat MATHLIBRARY_EXPORTS symbol")
>
>1. Zvolte **OK** zrušíte **Definice preprocesoru** dialogového okna a klikněte na tlačítko **OK** uložte provedené změny ve vlastnostech projektu.

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>Vytvoření projektu knihovny DLL ve starších verzích sady Visual Studio

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**.

1. V levém podokně **nový projekt** dialogového okna rozbalte **nainstalováno** > **šablony**a vyberte **Visual C++**, a v prostředním podokně vyberte **Konzolová aplikace Win32**. Zadejte `MathLibrary` v **název** textového pole zadejte název projektu.

   ![Pojmenujte projekt MathLibrary](media/mathlibrary-project-name.png "pojmenujte projekt MathLibrary")

1. Zvolte **OK** tlačítka Zavřít **nový projekt** dialogu a začněte **Průvodce aplikací Win32**.

   ![Přehled Průvodce aplikací Win32](media/mathlibrary-project-wizard-1.png "Přehled Průvodce aplikací Win32")

1. Zvolte **Další** tlačítko. Na **nastavení aplikace** stránce v části **typ aplikace**vyberte **DLL**.

   ![Vytvoření knihovny DLL v Průvodce aplikací Win32](media/mathlibrary-project-wizard-2.png "vytvoření knihovny DLL v Průvodce aplikací Win32")

1. Zvolte **Dokončit** tlačítko pro vytvoření projektu.

Po dokončení průvodce řešení, zobrazí se vygenerovaný projektu a zdrojových souborech v **Průzkumníka řešení** okna v sadě Visual Studio.

![Vygeneruje řešení v sadě Visual Studio](media/mathlibrary-solution-explorer-153.png "vygeneruje řešení v sadě Visual Studio")

Pravé teď tuto knihovnu DLL velmi mnoho neprovádí. V dalším kroku vytvoříte soubor hlaviček pro deklaraci funkce knihovny DLL exportuje a obnovte definice funkcí knihovny DLL být ještě užitečnější.

### <a name="to-add-a-header-file-to-the-dll"></a>Chcete-li přidat soubor hlaviček knihovny DLL

1. Chcete-li vytvořit soubor hlaviček pro vaše funkce na řádku nabídek, zvolte **projektu** > **přidat novou položku**.

1. V **přidat novou položku** dialogové okno, v levém podokně vyberte **Visual C++**. V prostředním podokně vyberte **soubor hlaviček (.h)**. Zadejte `MathLibrary.h` jako název souboru hlaviček.

   ![Přidat záhlaví v dialogovém okně Přidat novou položku](media/mathlibrary-add-new-item-header-file.png "přidat soubor hlaviček v dialogovém okně Přidat novou položku")

1. Zvolte **přidat** tlačítko, které vygeneruje prázdný soubor hlaviček, které se zobrazí v novém okně editoru.

   ![Prázdný soubor MathLibrary.h v editoru](media/edit-empty-mathlibrary-header.png "MathLibrary.h prázdný soubor v editoru")

1. Nahraďte obsah souboru hlaviček s tímto kódem:

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

Tento soubor hlavičky deklaruje některé funkce k vytvoření zobecněný pořadí Fibonacciho dané dvě počáteční hodnoty. Volání `fibonacci_init(1, 1)` generuje známých Fibonacciho číslo sekvence.

Všimněte si, že preprocesor příkazů v horní části souboru. Ve výchozím nastavení, přidá nový projekt šablony pro knihovnu DLL  **<em>PROJECTNAME</em>&#95;EXPORTY** definovaná makra preprocesoru pro projekt knihovny DLL. V tomto příkladu sady Visual Studio definuje **MATHLIBRARY&#95;EXPORTY** při sestavení vašeho projektu MathLibrary knihovny DLL. (Průvodce v sadě Visual Studio 2017 verze 15.3 nenutí tuto definici symbolu na velká písmena. Pokud zadáte název projektu "MathLibrary", pak je definován symbol MathLibrary&#95;EXPORTY místo MATHLIBRARY&#95;EXPORTY. That's důvod, proč existují další kroky výše uvedené tento symbol.)

Když **MATHLIBRARY&#95;EXPORTY** makro je definováno, **MATHLIBRARY&#95;rozhraní API** makra sady `__declspec(dllexport)` modifikátor v deklaracích funkcí. Tento modifikátor sděluje kompilátoru a linkeru, aby exportovat funkce nebo proměnné z knihovny DLL tak, aby ho můžete použít jiné aplikace. Při **MATHLIBRARY&#95;EXPORTY** není definován, například v souboru hlaviček je obsažen klientské aplikace, **MATHLIBRARY&#95;API** se vztahuje `__declspec(dllimport)` modifikátor deklarace. Tento modifikátor optimalizuje import funkce nebo proměnné v aplikaci. Další informace najdete v tématu [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Chcete-li přidat implementaci do knihovny DLL

1. V okně editoru vyberte kartu **MathLibrary.cpp** Pokud je již otevřen. Pokud ne, v **Průzkumníka řešení**, otevřete **MathLibrary.cpp** v **zdrojové soubory** složky **MathLibrary** projektu.

1. V editoru nahraďte obsah souboru MathLibrary.cpp následujícím kódem:

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h"
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

Pokud chcete ověřit, že vše funguje zatím, kompilovat knihovny DLL. Chcete-li zkompilovat, zvolte **sestavení** > **sestavit řešení** na řádku nabídek. Výstup by měl vypadat podobně jako:

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Blahopřejeme, jste vytvořili knihovnu DLL pomocí jazyka Visual C++. V dalším kroku vytvoříte klientskou aplikaci, která používá funkcí exportovaných knihovnou DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Vytvořit klientskou aplikaci, která používá knihovnu DLL

Při vytváření knihovny DLL musíte přemýšlet o tom, jak můžete použít vaši knihovnu DLL. Pro kompilaci kódu, který volá funkcí exportovaných knihovnou knihovny DLL, musí obsahovat deklarace ve zdrojovém kódu klienta. V době spojení, kdy se řeší tyto volání funkcí knihovny DLL, musí mít linkeru *importní knihovny*, soubor speciální knihovny, který obsahuje informace o tom, jak najít funkce, namísto skutečný kód Windows. A za běhu, musí být dostupné pro klienta v umístění, operační systém můžete najít knihovnu DLL.

Chcete používat knihovny DLL, zda vaše vlastní nebo knihovny DLL třetích stran, váš projekt klientské aplikace musí najít záhlaví, které deklarují knihovny DLL exportuje knihovny importu pro linker a samotná knihovna DLL. Jedním ze způsobů, je zkopírovat všechny tyto soubory do vašeho klientského projektu. Pro knihovny DLL třetích stran, které je nepravděpodobné, že chcete-li změnit váš klient je ve vývoji tato metoda může být nejlepší způsob, jak je používat. Když sestavíte taky knihovny DLL, je však lepší, aby se zabránilo duplicitě. Pokud provedete kopie knihovny DLL, které jsou ve vývoji, můžete nechtěně změnit soubor hlaviček v jedné kopie, ale nikoli u druhého nebo použití zastaralé knihovny. K tomuto problému vyhnout, doporučujeme že nastavit cesty zahrnutí ve vašem projektu klienta zahrnout soubory hlaviček knihovny DLL z projektu knihovny DLL. Nastavuje cestu ke knihovně ve vašem projektu klienta a zahrnují importu knihovny DLL z projektu knihovny DLL. A nakonec zkopírujte sestavení knihovny DLL z projektu knihovny DLL do výstupního adresáře sestavení. Tento krok umožňuje klientské aplikace a použít stejný kód knihovny DLL, které vytváříte.

### <a name="to-create-a-client-app-in-visual-studio-2017-version-153-or-later"></a>Chcete-li vytvořit klientskou aplikaci v sadě Visual Studio 2017 verze 15.3 nebo novější

1. Chcete-li vytvořit aplikace s C++, který používá knihovnu DLL, kterou jste vytvořili, na panelu nabídek zvolte **souboru** > **nový** > **projektu**.

1. V levém podokně **nový projekt** dialogového okna, vyberte **Windows Desktop** pod **nainstalováno** > **Visual C++**. V prostředním podokně vyberte **desktopový Průvodce pro Windows**. Zadejte název projektu, `MathClient`v **název** textové pole.

   ![Pojmenujte projekt klienta](media/mathclient-new-project-name-153.png "pojmenujte projekt klienta")

1. Zvolte **OK** spustit **desktopový projekt Windows** průvodce. V Průvodci zvolte **OK** vytvořit projekt klientské aplikace.

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Chcete-li vytvořit klientskou aplikaci ve starších verzích sady Visual Studio 2017

1. Chcete-li vytvořit aplikace s C++, který používá knihovnu DLL, kterou jste vytvořili, na panelu nabídek zvolte **souboru** > **nový** > **projektu**.

1. V levém podokně **nový projekt** dialogového okna, vyberte **Win32** pod **nainstalováno** > **šablony**  >  **Visual C++**. V prostředním podokně vyberte **Konzolová aplikace Win32**. Zadejte název projektu, `MathClient`v **název** textové pole.

   ![Pojmenujte projekt klienta](media/mathclient-project-name.png "pojmenujte projekt klienta")

1. Zvolte **OK** tlačítka Zavřít **nový projekt** dialogu a začněte **Průvodce aplikací Win32**. Na **přehled** stránku **Průvodce aplikací Win32** dialogového okna zvolte **Další** tlačítko.

1. Na **nastavení aplikace** stránce v části **typ aplikace**vyberte **konzolovou aplikaci** Pokud ještě není vybraná.

1. Zvolte **Dokončit** tlačítko pro vytvoření projektu.

Po dokončení průvodce je vytvořen projekt minimální konzolové aplikace. Název hlavní zdrojový soubor je stejný jako název projektu, který jste zadali dříve. V tomto příkladu je pojmenována **MathClient.cpp**. Je možné vytvořit, ale nepoužívá vaše knihovna DLL ještě.

V dalším kroku k volání funkce MathLibrary ve zdrojovém kódu, váš projekt musí obsahovat MathLibrary.h souboru. Může zkopírujte tento soubor hlavičky do projektu aplikace klienta a následně jej přidat do projektu jako existující položky. Tato metoda může být dobrou volbou pro knihovny třetích stran. Ale při práci na kódu pro vaši knihovnu DLL ve stejnou dobu jako klient, který může vést k změny v souboru jedno záhlaví, které se nezobrazují v jiném. Pokud chcete tomuto problému vyhnout, můžete změnit **další adresáře souborů k zahrnutí** cestu ve vašem projektu a zahrnout cestu k původní hlavičku.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Pokud chcete přidat záhlaví knihovny DLL do vaší cesty vložených souborů

1. Otevřít **stránky vlastností** dialogové okno pro **MathClient** projektu.

1. V **konfigurace** rozevíracího seznamu vyberte **všechny konfigurace** Pokud ještě není vybraná.

1. V levém podokně vyberte **Obecné** pod **vlastnosti konfigurace** > **C/C++**.

1. V podokně vlastností, vyberte ovládací prvek rozevíracího seznamu vedle položky **další adresáře souborů k zahrnutí** textové pole a klikněte na tlačítko **upravit**.

   ![Upravit vlastnost další adresáře souborů k zahrnutí](media/mathclient-additional-include-directories-property.png "upravit vlastnost další adresáře souborů k zahrnutí")

1. V horním podokně dvakrát klikněte **další adresáře souborů k zahrnutí** dialogové okno Povolit ovládacího prvku pro úpravy.

1. V textovém poli zadejte cestu k umístění **MathLibrary.h** hlavičkový soubor. V takovém případě můžete použít relativní cestu ze složky obsahující soubory .cpp v projektu klienta do složky, která obsahuje soubor hlaviček v projektu knihovny DLL. Pokud klientský projekt je v samostatném řešení ve stejné složce jako knihovna DLL řešení, relativní cestu by měl vypadat takto:

   `..\..\MathLibrary\MathLibrary`

   Pokud vaše projekty knihovny DLL a klienta jsou ve stejném řešení nebo řešení v různých složkách, pak musíte nastavit relativní cestu odpovídajícím způsobem.

   ![Přidat hlavičku umístění k vlastnosti další adresáře souborů k zahrnutí](media/mathclient-additional-include-directories.png "přidat hlavičku umístění k vlastnosti další adresáře souborů k zahrnutí")

1. Po zadání cesty k souboru záhlaví v **další adresáře souborů k zahrnutí** dialogového okna zvolte **OK** tlačítko přejdete zpět na **stránky vlastností** dialogovém okně a Klikněte na tlačítko **OK** tlačítko uložte provedené změny.

Nyní můžete zahrnout **MathLibrary.h** a funkce deklaruje v klientské aplikaci. Nahraďte obsah **MathClient.cpp** pomocí tohoto kódu:

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
#include "pch.h"
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

Tento kód lze zkompilovat, ale nejsou spojeny, protože propojovací program nemůže najít knihovnu importu potřebné k sestavení aplikace ještě. Propojovací program musí najít soubor MathLibrary.lib úspěšně propojení. Přidání souboru MathLibrary.lib do sestavení tak, že nastavíte **Další závislosti** vlastnost. Ještě jednou může zkopírovat soubor knihovny do projektu aplikace klienta, ale pokud jsou knihovny a klientské aplikace ve vývoji, které by mohly vést k změny v jedné kopie, které se nezobrazují v jiném. Pokud chcete tomuto problému vyhnout, můžete změnit **další adresáře knihoven** cestu ve vašem projektu a zahrnout cestu ke knihovně původní při propojování.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Chcete-li přidat knihovnu importu knihovny DLL do projektu

1. Otevřít **stránky vlastností** dialogové okno pro **MathClient** projektu.

1. V **konfigurace** rozevíracího seznamu vyberte **všechny konfigurace** Pokud ještě není vybraná.

1. V levém podokně vyberte **vstup** pod **vlastnosti konfigurace** > **Linkeru**. V podokně vlastností, vyberte ovládací prvek rozevíracího seznamu vedle položky **Další závislosti** textové pole a klikněte na tlačítko **upravit**.

   ![Upravit vlastnost Další závislosti](media/mathclient-additional-dependencies-property.png "upravit vlastnost Další závislosti")

1. V **Další závislosti** dialogovém okně Přidat `MathLibrary.lib` do seznamu v horní části ovládacích prvků pro úpravy.

   ![Přidat závislost knihovny](media/mathclient-additional-dependencies.png "Přidat závislost knihovny")

1. Zvolte **OK** chcete přejít zpátky k **stránky vlastností** dialogové okno.

1. V levém podokně vyberte **Obecné** pod **vlastnosti konfigurace** > **Linkeru**. V podokně vlastností, vyberte ovládací prvek rozevíracího seznamu vedle položky **další adresáře knihoven** textové pole a klikněte na tlačítko **upravit**.

   ![Upravit vlastnost další adresáře knihoven](media/mathclient-additional-library-directories-property.png "upravit vlastnost další adresáře knihoven")

1. V horním podokně dvakrát klikněte **další adresáře knihoven** dialogové okno Povolit ovládacího prvku pro úpravy. V textovém poli zadejte cestu k umístění **MathLibrary.lib** souboru. Zadejte tuto hodnotu použít makra, které funguje pro ladění a verze sestavení:

   `..\..\MathLibrary\$(IntDir)`

   ![Přidejte adresář knihovny](media/mathclient-additional-library-directories.png "přidejte adresář knihovny")

1. Po zadání cesty k souboru knihovny v **další adresáře knihoven** dialogového okna zvolte **OK** tlačítko přejdete zpět na **stránky vlastností** dialogové okno.

Klientská aplikace teď můžete zkompilovat a propojit úspěšně, ale stále není třeba všechno, co je nutné ho spustit. Když operační systém načítá aplikaci, hledá MathLibrary knihovny DLL. Pokud v některé adresáře systému, cesta prostředí nebo v adresáři místní aplikace nemůže najít knihovnu DLL, zatížení se nezdaří. Chcete vyhnout tomuto problému jedním ze způsobů je kopírování knihovny DLL do adresáře, který obsahuje spustitelný soubor klienta jako součást procesu sestavení. Kopírování knihovny DLL, můžete přidat **post-build Event** do projektu, chcete-li přidat příkaz, který zkopíruje knihovny DLL do výstupního adresáře sestavení. Příkaz tady zadané, zkopíruje knihovny DLL pouze v případě, že nebyl nalezen nebo došlo ke změně a makra, používá ke kopírování do a z správné umístění ladění nebo maloobchodního prodeje pro vaši konfiguraci.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Kopírování knihovny DLL v události po sestavení

1. Otevřete **stránky vlastností** dialogové okno pro **MathClient** projektu, pokud ještě není otevřeno.

1. V rozevíracím seznamu konfigurace, vyberte **všechny konfigurace** Pokud ještě není vybraná.

1. V levém podokně vyberte **post-build Event** pod **vlastnosti konfigurace** > **události sestavení**.

1. V podokně vlastností vyberte ovládacího prvku pro úpravy v **příkazového řádku** pole a pak zadejte tento příkaz:

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Přidat příkaz po sestavení](media/mathclient-post-build-command-line.png "přidat příkaz po sestavení")

1. Zvolte **OK** tlačítko uložte provedené změny ve vlastnostech projektu.

Klientské aplikace má teď všechno, co je potřeba sestavit a spustit. Sestavte aplikaci výběrem **sestavení** > **sestavit řešení** na řádku nabídek. **Výstup** okna v sadě Visual Studio by měl mít vypadat:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Blahopřejeme, vytvořili jste aplikaci, která se volá funkce v knihovně DLL. Nyní spusťte aplikace, abyste viděli, co to dělá. V panelu nabídky zvolte **ladění** > **spustit bez ladění**. Visual Studio otevře okno příkazového řádku pro spuštění programu. Poslední část výstup by měl vypadat:

![Klientská aplikace spustit bez ladění](media/mathclient-run-without-debugging.png "klientskou aplikaci spustit bez ladění")

Stisknutím jakékoli klávesy zavřete příkazové okno.

Teď, když jste vytvořili knihovnu DLL a klientské aplikace, můžete experimentovat. Zkuste nastavení zarážek v kódu klientské aplikace a spusťte aplikaci v ladicím programu. Podívejte se, co se stane při krokování s vnořením volání knihovny. Přidání dalších funkcí do knihovny nebo zápis jinou klientskou aplikaci, která používá vaše knihovna DLL.

Když nasadíte aplikaci, je nutné nasadit knihoven DLL, která používá. Nejjednodušší způsob, jak zpřístupnit knihovny DLL, který jste vytvořili nebo které zahrnete od jiných výrobců do vaší aplikace je jejich umístění ve stejném adresáři jako aplikace, označované také jako *nasazení aplikace – místní*. Další informace o nasazení naleznete v tématu [nasazení v jazyce Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Viz také:

[Volání funkcí knihovny DLL z aplikací Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
