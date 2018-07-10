---
title: 'Návod: Vytváření a používání vlastního dynamického propojení knihovny (C++) | Microsoft Docs'
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19c9c013d591f4c6de14ecd4a2c582d8f0f3e4d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392585"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Návod: Vytváření a používání vlastního dynamického propojení knihovny (C++)

Tento podrobný návod ukazuje, jak pomocí prostředí Visual Studio IDE můžete vytvořit vlastní dynamická knihovna (DLL) napsané v jazyce C++ a použít jej z jiné aplikace C++. Knihovny DLL jsou jedním z nejužitečnějších druhy součásti systému Windows. Můžete je jako způsob, jak sdílet kód a prostředky, zmenšení velikosti aplikací a aby bylo snazší rozšířit své aplikace a služby. V tomto návodu vytvořte knihovnu DLL, která implementuje některé matematické funkce a pak vytvořte konzolovou aplikaci, která využívá funkce z knihovny DLL. Na této cestě získejte Úvod k některým programovací techniky a konvence použité v knihovny DLL systému Windows.

Tento názorný postup obsahuje tyto úlohy:

- Vytvoření projektu knihovny DLL v sadě Visual Studio.

- Přidáte exportované funkce a proměnné na knihovnu DLL.

- Vytvoření projektu aplikace konzoly v sadě Visual Studio.

- Pomocí funkce a proměnné naimportované z knihovny DLL v konzolové aplikace.

- Dokončená aplikace spusťte.

Jako knihovnu staticky propojené knihovny DLL _exportuje_ proměnné, funkce a prostředky podle názvu a aplikace _importuje_ tyto názvy používat tyto proměnné, funkce a prostředky. Na rozdíl od staticky propojené knihovny systému Windows se připojí k exporty v knihovně DLL při načítání, nebo za běhu, místo připojení je v době spojení importy ve vaší aplikaci. Windows vyžaduje, aby doplňující informace, které nejsou součástí standardní C++ kompilace modelu Chcete-li tato připojení. Visual C++ compiler implementuje některé specifické pro společnost Microsoft rozšíření pro C++ poskytnout tyto doplňující informace. Tato rozšíření objasníme, jak jsme přejděte.

Tento návod vytvoří dvě řešení sady Visual Studio; ten, který vytvoří knihovnu DLL a ten, který sestaví klientské aplikace. Knihovnu DLL používá konvence volání jazyka C, takže může být volána z aplikace vytvořené pomocí jiných jazyků, dokud platformy a volání a propojování konvence shodovat. Použití klientské aplikace _implicitní propojení_, kde Windows odkazuje na knihovnu DLL v okamžiku načtení aplikace. To umožní aplikaci volání funkcí knihovny DLL zadaných stejně jako funkce v staticky propojené knihovny.

Tento názorný postup nezahrnuje některé běžné situace. C++ – knihovny DLL používané jinými programovací jazyky nezobrazí. Postup vytvoření knihovny DLL určené pouze nezobrazí. Použití explicitní propojení načtení knihovny DLL za běhu, spíše než v době načtení také nezobrazí. REST zajištěná, Visual C++ můžete provádět tyto akce. Odkazy na další informace o knihoven DLL naleznete v tématu [knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md). Další informace o implicitní a explicitní propojení najdete v tématu [rozhodnutí, která propojení metodu použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Informace o vytváření knihovny DLL C++ pro použití s programovacích jazyků, které používají konvence propojení jazyka C najdete v tématu [export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md). Informace o tom, jak vytvořit knihovny DLL pro použití s jazyky rozhraní .NET najdete v tématu [volání funkcí knihovny DLL z aplikací jazyka Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md).

Tento návod používá Visual Studio 2017, ale kód a většina pokyny platí pro starší verze. Postup vytvoření nové projekty změnit od verze Visual Studio 2017 verze 15.3. Tento návod popisuje, jak k vytváření projektů pro novější a starší verze. Podívejte se na kroky, které odpovídají verzi sady Visual Studio.

## <a name="prerequisites"></a>Požadavky

- Počítače se systémem Microsoft Windows 7 nebo novější verze. Pro dosažení co nejlepších výsledků vývoj doporučujeme Windows 10.

- Kopie Visual Studio 2017. Informace o tom, jak stáhnout a nainstalovat Visual Studio najdete v tématu [nainstalovat Visual Studio 2017](/visualstudio/install/install-visual-studio). Když spustíte instalační program, ujistěte se, že **vývoj aplikací s jazykem C++** zatížení je zaškrtnuté. Nebojte se, pokud jste nenainstalovali tímto zatížením, při instalaci sady Visual Studio. Můžete znovu spusťte instalační program a nainstalujte jej.

   ![Vývoj aplikací s jazykem C++](media/desktop-development-with-cpp.png "vývoj aplikací s C++")

- Seznámíte se základy používání prostředí Visual Studio IDE. Pokud jste použili aplikacích klasické pracovní plochy Windows před, můžete pravděpodobně udržovat. Úvod najdete v části [prohlídka funkce Visual Studio IDE](/visualstudio/ide/visual-studio-ide).

- Pochopení dostatek základy jazyka C++ se podle nich zorientujete. Nemusíte si dělat starosti, provedeme nemáte nic nenastavujte příliš komplikovaný.

## <a name="create-the-dll-project"></a>Vytvoření projektu knihovny DLL

V této sadě úlohy vytvoření projektu pro knihovny DLL, přidejte kód a sestavte jej. Pokud chcete začít, spusťte Visual Studio IDE a přihlásit, pokud je potřeba. Pokyny pro Visual Studio 2017 verze 15.3 nejdřív se musí uvést. Pokyny pro starší verze později, takže přeskočit Pokud potřebujete.

### <a name="to-create-a-dll-project-in-visual-studio-2017-version-153-or-later"></a>Vytvoření projektu knihovny DLL v aplikaci Visual Studio 2017 verze 15.3 nebo novější

1. Na řádku nabídek zvolte **soubor**, **nový**, **projektu** otevřete **nový projekt** dialogové okno.

1. V levém podokně **nový projekt** dialogové okno, rozbalte seznam **nainstalovaná** a **Visual C++** Pokud potřebné a potom vyberte **Windows Desktop**. V prostředním podokně vyberte **Windows Desktop průvodce**. Zadejte `MathLibrary` v **název** pole k zadání názvu pro projekt.

   ![Název projektu MathLibrary](media/mathlibrary-new-project-name-153.png "název projektu MathLibrary")

1. Vyberte **OK** tlačítko pro zavření **nový projekt** dialogové okno a spusťte **projektu pro Windows Desktop** průvodce.

1. V **projektu pro Windows Desktop** průvodce v části **typ aplikace**, vyberte **dynamické knihovny (DLL)**.

   ![Vytvoření knihovny DLL v průvodci Windows Desktop projektu](media/mathlibrary-desktop-project-wizard-dll.png "vytvoření knihovny DLL v systému Windows Desktop projektu průvodce")

1. Vyberte **OK** tlačítko pro vytvoření projektu.

> [!NOTE]
> Chcete-li vyřešit problém v aplikaci Visual Studio 2017 verze 15.3 jsou potřeba udělat další kroky. Postupujte podle těchto pokynů, které chcete zobrazit, pokud potřebujete provést tuto změnu.
>
>1. V **Průzkumníku řešení**, pokud ještě není vybrané, vyberte **MathLibrary** projektu v části **řešení 'MathLibrary'**.
>
>1. Na řádku nabídek zvolte **projektu**, **vlastnosti**.
>
>1. V levém podokně **stránky vlastností** dialogové okno, vyberte **preprocesor** pod **vlastnosti konfigurace**, **C/C++**. Zkontrolujte obsah **Definice preprocesoru** vlastnost.<br/><br/>![Zkontrolujte vlastnost Definice preprocesoru](media/mathlibrary-153bug-preprocessor-definitions-check.png "Zkontrolujte vlastnost Definice preprocesoru")<br/><br/>Pokud se zobrazí **MATHLIBRARY&#95;EXPORTUJE** v **Definice preprocesoru** seznamu, pak nemusíte nic nezmění. Pokud se zobrazí **MathLibrary&#95;EXPORTUJE** místo toho pokračujte podle těchto kroků.
>
>1. V horní části **stránky vlastností** dialogové okno, změny **konfigurace** rozevírací seznam pro **všechny konfigurace**.
>
>1. V podokně vlastností vyberte ovládacího prvku rozevíracího seznamu vedle pole pro úpravy pro **Definice preprocesoru**a potom zvolte **upravit**.<br/><br/>![Upravit vlastnost Definice preprocesoru](media/mathlibrary-153bug-preprocessor-definitions-property.png "upravit vlastnost Definice preprocesoru")
>
>1. V horní podokno **Definice preprocesoru** dialogu přidat nový symbol `MATHLIBRARY_EXPORTS`.<br/><br/>![Přidat MATHLIBRARY_EXPORTS symbol](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "přidat MATHLIBRARY_EXPORTS symbol")
>
>1. Zvolte **OK** pro zavření **Definice preprocesoru** dialogové okno a potom zvolte **OK** se uložit změny do vlastností projektu.

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>Vytvoření projektu knihovny DLL v starší verze sady Visual Studio

1. Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.

1. V levém podokně **nový projekt** dialogové okno, rozbalte seznam **nainstalovaná**, **šablony**a vyberte **Visual C++** a pak v Centru Vyberte možnost **Konzolová aplikace Win32**. Zadejte `MathLibrary` v **název** textové pole k zadání názvu pro projekt.

   ![Název projektu MathLibrary](media/mathlibrary-project-name.png "název projektu MathLibrary")

1. Vyberte **OK** tlačítko pro zavření **nový projekt** dialogové okno a spusťte **Win32 – Průvodce aplikací**.

   ![Win32 – Průvodce aplikací – přehled](media/mathlibrary-project-wizard-1.png "Win32 – Průvodce aplikací – přehled")

1. Vyberte **Další** tlačítko. Na **nastavení aplikace** v části **typ aplikace**, vyberte **knihovny DLL**.

   ![Vytvoření knihovny DLL v Win32 – Průvodce aplikací](media/mathlibrary-project-wizard-2.png "vytvoření knihovny DLL v Win32 – Průvodce aplikací")

1. Vyberte **Dokončit** tlačítko pro vytvoření projektu.

Po dokončení průvodce řešení, uvidíte generovaného projektu a zdrojových souborech v **Průzkumníku řešení** oken v sadě Visual Studio.

![Generuje řešení v sadě Visual Studio](media/mathlibrary-solution-explorer-153.png "generované řešení v sadě Visual Studio")

Pravé teď tuto knihovnu DLL velmi mnoho neprovádí. Dále vytvoříte soubor hlaviček deklarovat funkcí knihovny DLL exportuje a poté přidejte definice funkcí na knihovnu DLL, aby byla užitečnější.

### <a name="to-add-a-header-file-to-the-dll"></a>Chcete-li přidat soubor hlaviček na knihovnu DLL

1. Chcete-li vytvořit soubor hlavičky pro funkce, na panelu nabídek, zvolte **projektu**, **přidat novou položku**.

1. V **přidat novou položku** dialogové okno, v levém podokně, vyberte **Visual C++**. V prostředním podokně vyberte **soubor (hlaviček)**. Zadejte `MathLibrary.h` jako název pro soubor hlaviček.

   ![Přidat hlavičku v dialogovém okně Přidat novou položku](media/mathlibrary-add-new-item-header-file.png "přidat soubor hlaviček v dialogovém okně Přidat novou položku")

1. Vyberte **přidat** pro vygenerování prázdné záhlaví souboru, který se zobrazí v novém okně editor.

   ![Prázdný soubor MathLibrary.h v editoru](media/edit-empty-mathlibrary-header.png "prázdný MathLibrary.h souboru v editoru")

1. Nahraďte obsah souboru hlavička s tímto kódem:

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

Tento soubor hlaviček deklaruje některé funkce k vytvoření zobecněný pořadí Fibonacciho dané dva počáteční hodnoty. Volání `fibonacci_init(1, 1)` posloupnost známé Fibonacciho číslo.

Všimněte si preprocesoru příkazy v horní části souboru. Ve výchozím nastavení, přidá nový projekt šablona pro knihovny DLL ***PROJECTNAME *&#95;EXPORTUJE** k definované makra preprocesoru pro projektu knihovny DLL. V tomto příkladu definuje Visual Studio **MATHLIBRARY&#95;EXPORTUJE** při sestavení projektu MathLibrary DLL. (Průvodce v nástroji Visual Studio 2017 verze 15.3 nevynutí tuto definici symbol na velká písmena. Pokud zadáte název projektu "MathLibrary" pak symbol definované je MathLibrary&#95;EXPORTUJE místo MATHLIBRARY&#95;export. That's proto existují další kroky výše a přidejte tento symbol.)

Při **MATHLIBRARY&#95;EXPORTUJE** makro je definován, **MATHLIBRARY&#95;rozhraní API** makro nastaví `__declspec(dllexport)` modifikátor na deklarace funkcí. Tento modifikátor informuje kompilátoru a linkeru pro export funkce nebo proměnná z knihovny DLL, aby se může použít jiné aplikace. Při **MATHLIBRARY&#95;EXPORTUJE** je definován, například soubor hlaviček je obsažen ve klientskou aplikaci, **MATHLIBRARY&#95;rozhraní API** se vztahuje `__declspec(dllimport)` modifikátor k deklarace. Tento modifikátor optimalizuje import funkce nebo proměnná v aplikaci. Další informace najdete v tématu [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Chcete-li přidat implementace na knihovnu DLL

1. V okně editoru vyberte kartu pro **MathLibrary.cpp** Pokud je již otevřeno. Pokud ne, v **Průzkumníku řešení**, otevřete **MathLibrary.cpp** v **zdrojové soubory** složky **MathLibrary** projektu.

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

Pokud chcete ověřit, že vše funguje dosavadní, Zkompilujte knihovnu DLL. Zkompilovat, zvolte **sestavení**, **sestavit řešení** v řádku nabídek. Výstup by měl vypadat přibližně takto:

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

Blahopřejeme, jste vytvořili knihovny DLL pomocí Visual C++. V dalším kroku vytvoříte klientskou aplikaci, která využívá funkce exportované sadou knihovnu DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Vytvořit klientskou aplikaci, která používá knihovnu DLL

Při vytváření knihovny DLL, musí si myslíte o použití knihovny DLL. Kompilace kódu, který volá funkce exportované sadou knihovny DLL, musí být deklarací součástí zdrojového kódu klienta. Během odkaz, když jsou vyřešeny těchto volání funkcí knihovny DLL, musí mít linkeru *importovat knihovny*, zvláštní druh knihovny soubor, který obsahuje informace pro Windows o tom, jak najít funkce místo skutečný kód. A za běhu, musí být knihovnu DLL dostupných pro klienta v umístění, které můžete najít operačního systému.

Chcete-li používat knihovny DLL, zda vaše vlastní nebo knihovny DLL třetích stran, projekt klientské aplikace musí být schopni najít seznam hlaviček, které deklarovat knihovnu DLL exporty knihoven importovat pro linkeru a samotné knihovny DLL. Jedním ze způsobů k tomu je zkopírujte všechny tyto soubory do vašeho klientského projektu. Pro knihovny DLL třetích stran, které pravděpodobně změnit při vašeho klienta je ve vývoji může se jednat nejlepší způsob, jak je používat. Při sestavování také knihovnu DLL, je však lepší předejdete duplikace. Pokud provedete kopii souborů DLL, které jsou ve vývoji, může vám omylem změnit soubor hlaviček v jedné kopie, ale není dalších nebo použijte zastaralá knihovna. K tomuto problému vyhnout, doporučujeme že nastavit cestu zahrnutí ve vašem projektu klienta a zahrnout soubory hlaviček knihovny DLL z projektu knihovny DLL. Také můžete nastavte cestu knihovny ve vašem projektu klienta a obsahovat importu knihovny DLL z projektu knihovny DLL. A nakonec, zkopírujte vytvořený knihovny DLL z projektu knihovny DLL do výstupního adresáře sestavení. Tím se zajistí, že vaší klientské aplikace používá stejný kód knihovny DLL, které vytvoříte.

### <a name="to-create-a-client-app-in-visual-studio-2017-version-153-or-later"></a>Chcete-li vytvořit klientskou aplikaci ve Visual Studio 2017 verze 15.3 nebo novější

1. K vytvoření aplikace C++, která používá knihovnu DLL, kterou jste právě vytvořili, zvolte v řádku nabídek zvolte **soubor**, **nový**, **projektu**.

1. V levém podokně **nový projekt** dialogovém okně, vyberte **Windows Desktop** pod **nainstalovaná**, **Visual C++**. V prostředním podokně vyberte **Windows Desktop průvodce**. Zadejte název projektu, `MathClient`v **název** textové pole.

   ![Název projektu klienta](media/mathclient-new-project-name-153.png "název projektu klienta")

1. Zvolte **OK** spustit **projektu pro Windows Desktop** průvodce. V průvodci vyberte **OK** vytvořit projekt klientské aplikace.

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Chcete-li vytvořit klientskou aplikaci ve starších verzích Visual Studio 2017

1. K vytvoření aplikace C++, která používá knihovnu DLL, kterou jste právě vytvořili, zvolte v řádku nabídek zvolte **soubor**, **nový**, **projektu**.

1. V levém podokně **nový projekt** dialogovém okně, vyberte **Win32** pod **nainstalovaná**, **šablony**, **Visual C++**. V prostředním podokně vyberte **Konzolová aplikace Win32**. Zadejte název projektu, `MathClient`v **název** textové pole.

   ![Název projektu klienta](media/mathclient-project-name.png "název projektu klienta")

1. Vyberte **OK** tlačítko pro zavření **nový projekt** dialogové okno a spusťte **Win32 – Průvodce aplikací**. Na **přehled** stránky **Win32 – Průvodce aplikací** dialogovém okně vyberte **Další** tlačítko.

1. Na **nastavení aplikace** v části **typ aplikace**, vyberte **Konzolová aplikace** Pokud již není vybrána.

1. Vyberte **Dokončit** tlačítko pro vytvoření projektu.

Po dokončení průvodce je vytvořen projektu minimální konzolové aplikace. Název hlavní zdrojový soubor je stejný jako název projektu, které jste zadali dříve. V tomto příkladu je název **MathClient.cpp**. Můžete ji vytvořit, ale nepoužívá vaše knihovna DLL ještě.

V dalším kroku k volání funkce MathLibrary ve zdrojovém kódu, musí obsahovat projektu soubor MathLibrary.h. Může tento záhlaví soubor zkopírovat do projektu aplikace klienta a potom ho přidat do projektu jako existující položka. To může být vhodný pro knihovny třetích stran. Ale pokud pracujete na kód pro knihovny DLL ve stejnou dobu jako váš klient, který může vést k změny v souboru jeden hlavičky, které se neprojeví v dalších. Chcete-li tomuto problému vyhnout, můžete změnit **další adresáře Include** cestu ve vašem projektu a zahrnovat cestu k původní hlavičku.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Chcete-li přidat hlavičku knihovny DLL pro vaší obsahovat cestu

1. Otevřete **stránky vlastností** dialogové okno pro **MathClient** projektu.

1. V **konfigurace** rozevíracího seznamu vyberte **všechny konfigurace** Pokud již není vybrána.

1. V levém podokně vyberte **Obecné** pod **vlastnosti konfigurace**, **C/C++**.

1. V podokně vlastností vyberte ovládacího prvku rozevíracího seznamu vedle položky **další adresáře Include** textového pole a potom vyberte **upravit**.

   ![Upravit vlastnost další adresáře Include](media/mathclient-additional-include-directories-property.png "upravit vlastnost další adresáře Include")

1. V horním podokně dvakrát klikněte **další adresáře Include** dialogové okno Povolit ovládací prvek upravit.

1. V ovládacím prvku upravit, zadejte cestu k umístění **MathLibrary.h** soubor hlaviček. V takovém případě můžete použít relativní cesta:

   `..\..\MathLibrary\MathLibrary`

   ![Přidat hlavičku umístění pro další adresáře Include vlastnost](media/mathclient-additional-include-directories.png "přidat hlavičku umístění pro další adresáře Include vlastnost")

1. Po zadání cesty k souboru do pole hlavičky **další adresáře Include** dialogovém okně vyberte **OK** tlačítko přejdete na **stránky vlastností** dialogové okno, a Zvolte **OK** tlačítko uložte provedené změny.

Teď můžete použít **MathLibrary.h** souboru a pomocí funkce deklaruje v klientské aplikace. Nahraďte obsah **MathClient.cpp** pomocí tohoto kódu:

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
#include "stdafx.h"
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

Tento kód můžete kompilovat, ale není propojená, protože linkeru nelze nalézt knihovny importu potřeba ještě sestavení aplikace. Linkeru musí být schopen najít soubor MathLibrary.lib propojení úspěšně. Soubor MathLibrary.lib musíte přidat do sestavení nastavením **Další závislosti** vlastnost. Ještě jednou může zkopírovat soubor knihovny do projektu aplikace klienta, ale pokud knihovny a klientské aplikace jsou ve vývoji, který může vést k změny v jedné kopie, které se neprojeví v dalších. Chcete-li tomuto problému vyhnout, můžete změnit **další adresáře knihovny** cestu ve vašem projektu a zahrnovat cestu k původní knihovna při propojení.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Chcete-li do projektu přidejte knihovny importu knihovny DLL

1. Otevřete **stránky vlastností** dialogové okno pro **MathClient** projektu.

1. V **konfigurace** rozevíracího seznamu vyberte **všechny konfigurace** Pokud již není vybrána.

1. V levém podokně vyberte **vstup** pod **vlastnosti konfigurace**, **Linkeru**. V podokně vlastností vyberte ovládacího prvku rozevíracího seznamu vedle položky **Další závislosti** textového pole a potom vyberte **upravit**.

   ![Upravit vlastnosti Další závislosti](media/mathclient-additional-dependencies-property.png "upravit vlastnost Další závislosti")

1. V **Další závislosti** dialogu přidat `MathLibrary.lib` v horní části seznamu ovládacích prvků pro úpravy.

   ![Přidat závislost knihovny](media/mathclient-additional-dependencies.png "Přidat závislost knihovny")

1. Zvolte **OK** se vrátíte k **stránky vlastností** dialogové okno.

1. V levém podokně vyberte **Obecné** pod **vlastnosti konfigurace**, **Linkeru**. V podokně vlastností vyberte ovládacího prvku rozevíracího seznamu vedle položky **další adresáře knihovny** textového pole a potom vyberte **upravit**.

   ![Upravit vlastnost další adresáře knihovny](media/mathclient-additional-library-directories-property.png "upravit vlastnost další adresáře knihovny")

1. V horním podokně dvakrát klikněte **další adresáře knihovny** dialogové okno Povolit ovládací prvek upravit. V ovládacím prvku upravit, zadejte cestu k umístění **MathLibrary.lib** souboru. Zadejte tuto hodnotu pomocí makra, která funguje pro ladění a verze sestavení:

   `..\..\MathLibrary\$(IntDir)`

   ![Přidejte adresář knihovny](media/mathclient-additional-library-directories.png "přidejte adresář knihovny")

1. Po zadání cesty k souboru knihovny v **další adresáře knihovny** dialogovém okně vyberte **OK** tlačítko přejdete na **stránky vlastností** dialogové okno.

Klientská aplikace teď můžete zkompilovat a propojit úspěšně, ale stále nemá všechny objekty, které je nutné ho spustit. Až se operační systém načte vaší aplikace, hledá MathLibrary DLL. Pokud v některých systémových adresářů, cestě prostředí nebo adresáři místní aplikace nemůže najít knihovnu DLL, zatížení se nezdaří. Jeden z přístupů k tomuto problému vyhnout je zkopírovat do adresáře, který obsahuje vaše spustitelný soubor klienta jako součást procesu sestavení knihovnu DLL. Pokud chcete zkopírovat knihovnu DLL, můžete přidat **události po sestavení** do projektu, chcete-li přidat příkaz který zkopíruje knihovnu DLL do výstupního adresáře sestavení. Příkaz zadaný v tomto poli zkopíruje knihovnu DLL, pouze v případě, že chybí nebo se změnila a používá makra ke kopírování do a z správné ladění nebo prodejní umístění pro vaši konfiguraci.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Kopírování knihovny DLL v události po sestavení

1. Otevřete **stránky vlastností** dialogové okno pro **MathClient** projektu, pokud již není otevřený.

1. V rozevíracím seznamu konfigurace, vyberte **všechny konfigurace** Pokud již není vybrána.

1. V levém podokně vyberte **události po sestavení** pod **vlastnosti konfigurace**, **události sestavení**.

1. V podokně vlastností vyberte Upravit ovládacího prvku **příkazového řádku** pole a pak zadejte tento příkaz:

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Příkaz po sestavení přidat](media/mathclient-post-build-command-line.png "přidejte příkaz po sestavení")

1. Vyberte **OK** tlačítko Uložit změny do vlastností projektu.

Nyní vaší klientské aplikace obsahuje všechno potřebné k sestavení a spuštění. Sestavení aplikace tak, že zvolíte **sestavení**, **sestavit řešení** v řádku nabídek. **Výstup** oken v sadě Visual Studio by měl obsahovat přibližně takto:

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Blahopřejeme, jste vytvořili aplikaci, která volá funkce v knihovně DLL. Nyní můžete spusťte aplikace, abyste viděli, jak funguje. Na řádku nabídek zvolte **ladění**, **spustit bez ladění**. Visual Studio otevře okno příkazového řádku pro program, který chcete spustit. Poslední část výstup by měl vypadat takto:

![Spustit klientskou aplikaci bez ladění](media/mathclient-run-without-debugging.png "spustit klientskou aplikaci bez ladění")

Stisknutím libovolné klávesy zavřete příkazové okno.

Teď, když jste vytvořili, knihovny DLL a klientskou aplikaci, můžete experimentovat. Zkuste nastavit zarážky v kódu aplikace klienta a spusťte aplikaci v ladicím programu. Najdete, co se stane, když krok do volání knihovny. Přidání dalších funkcí do knihovny nebo zapisovat jiné klientskou aplikaci, která používá vaše knihovna DLL.

Když nasadíte aplikaci, musíte také nasadit knihovny DLL používá. Nejjednodušší způsob, jak zpřístupnit knihovny DLL, které vytvoříte, nebo které zahrnete od třetích stran pro vaši aplikaci je uloží je do stejného adresáře jako aplikace, také známé jako *nasazení aplikace místní*. Další informace o nasazení najdete v tématu [nasazení v jazyce Visual C++](..\ide\deployment-in-visual-cpp.md).

## <a name="see-also"></a>Viz také

[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)  
[Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)  
[Návod: Nasazení programu (C++)](../ide/walkthrough-deploying-your-program-cpp.md)  
[Volání funkcí knihovny DLL z aplikací Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md)