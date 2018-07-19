---
title: 'Návod: Vytvoření a použití statické knihovny (C++) | Dokumentace Microsoftu'
ms.custom: get-started-article
ms.date: 07/12/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1bcbf5747b667615c96ced3488e16f2a8fc0ef2d
ms.sourcegitcommit: 9ad287c88bdccee2747832659fe50c2e5d682a0b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39034800"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>Návod: Vytvoření a použití statické knihovny (C++)
Tento podrobný návod ukazuje, jak vytvořit statické knihovny (soubor .lib) pro použití s aplikací v jazyce C++. Použití statické knihovny je skvělým způsobem pro opětovné použití kódu. Místo aby byly stejné rutiny v každé aplikaci, která vyžaduje funkci pokaždé znova implementovány, je napsat jednou ve statické knihovně a potom na něj odkazovat z aplikací. Kód spojený ze statické knihovny se stane součástí vaší aplikace – není nutné instalovat jiný soubor pro použití kódu.  
  
 Tento návod pokrývá následující úkoly:  
  
-   [Vytvoření projektu statické knihovny](#CreateLibProject)  
  
-   [Přidání třídy do statické knihovny](#AddClassToLib)  
  
-   [Vytvoření konzolové aplikace jazyka C++, který odkazuje na statickou knihovnu](#CreateAppToRefTheLib)  
  
-   [Pomocí funkcí ze statické knihovny v aplikaci](#UseLibInApp)  
  
-   [Spuštění aplikace](#RunApp)  
  
## <a name="prerequisites"></a>Požadavky  
 Porozumění základům jazyka C++.  
  
##  <a name="CreateLibProject"></a> Vytvoření projektu statické knihovny  
  
#### <a name="to-create-a-static-library-project"></a>Vytvoření projektu statické knihovny  
  
1.  V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2. V levém podokně **nový projekt** dialogového okna rozbalte **nainstalováno, Visual C++** a pak vyberte **Windows Desktop**.
  
3. V prostředním podokně vyberte **desktopový Průvodce pro Windows**.  
  
4.  Zadejte název projektu – například **MathFuncsLib**– v **název** pole. Zadejte název pro toto řešení – například **StaticLibrary**– v **název řešení** pole. Zvolte **OK** tlačítko.  
  
5. V části **typ aplikace**, vyberte statická knihovna (.lib).  
  
6. V části **další možnosti**, zrušte zaškrtnutí políčka **Předkompilovaná hlavička** zaškrtávací políčko.
  
7. Zvolte **OK** pro vytvoření projektu.  
 
##  <a name="AddClassToLib"></a> Přidání třídy do statické knihovny  
  
#### <a name="to-add-a-class-to-the-static-library"></a>Přidání třídy do statické knihovny  
  
1.  Chcete-li vytvořit soubor hlaviček pro novou třídu, otevřete místní nabídku pro **MathFuncsLib** projekt **Průzkumníka řešení**a klikněte na tlačítko **přidat**, **nová položka** . V **přidat novou položku** dialogové okno, v levém podokně v části **Visual C++** vyberte **kód**. V prostředním podokně vyberte **soubor hlaviček (.h)**. Zadejte název souboru hlaviček, například **MathFuncsLib.h**– a klikněte na tlačítko **přidat** tlačítko. Zobrazí se prázdný soubor hlaviček.  
  
2.  Přidejte třídu pojmenovanou **MyMathFuncs** pro běžné matematické operace, jako je například sčítání, odčítání, násobení a dělení. Kód by měl vypadat takto:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]  
  
3.  Chcete-li vytvořit zdrojový soubor pro novou třídu, otevřete místní nabídku **MathFuncsLib** projekt **Průzkumníku řešení**a klikněte na tlačítko **přidat**, **nová položka** . V **přidat novou položku** dialogové okno, v levém podokně v části **Visual C++** vyberte **kód**. V prostředním podokně vyberte **soubor C++ (.cpp)**. Zadejte název zdrojového souboru, například **MathFuncsLib.cpp**– a klikněte na tlačítko **přidat** tlačítko. Zobrazí se prázdný zdrojový soubor.  
  
4.  Použijte tento soubor k implementaci funkcionality pro **MyMathFuncs**. Kód by měl vypadat takto:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]  
  
5.  Zkompilujte statickou knihovnu tak, že vyberete **sestavení**, **sestavit řešení** na řádku nabídek. Tím se vytvoří statická knihovna, kterou můžete použít v jiných programech.  
  
    > [!NOTE]
    >  Při sestavování v příkazovém řádku aplikace Visual Studio, je nutné vytvořit program ve dvou krocích. Nejprve spusťte **cl /c/EHsc MathFuncsLib.cpp** ke kompilaci kódu a vytvořte objektový soubor s názvem **MathFuncsLib.obj**. ( **Cl** příkazu vyvolá Kompilátor Cl.exe a **/c** možnost určí možnost kompilace bez propojení. Další informace najdete v tématu [/c (Kompilovat bez propojení)](../build/reference/c-compile-without-linking.md).) Za druhé, spusťte **lib MathFuncsLib.obj** propojení kódu a vytvoření statické knihovny **MathFuncsLib.lib**. ( **Lib** příkazu vyvolá správce knihovny Lib.exe. Další informace najdete v tématu [LIB Reference](../build/reference/lib-reference.md).)  
  
##  <a name="CreateAppToRefTheLib"></a> Vytvoření konzolové aplikace jazyka C++, který odkazuje na statickou knihovnu  
  
#### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>K vytvoření konzolové aplikace jazyka C++, který odkazuje na statickou knihovnu  
  
1.  V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2. V levém podokně **nový projekt** dialogového okna rozbalte **nainstalováno, Visual C++** a pak vyberte **Windows Desktop**.  

3. V prostředním podokně vyberte **desktopový Průvodce pro Windows**.  
  
4.  Zadejte název projektu – například **MyExecRefsLib**– v **název** pole. V rozevíracího seznamu vedle položky **řešení**vyberte **přidat do řešení**. Tím přidáte nový projekt do řešení, které obsahuje statickou knihovnu. Zvolte **OK** tlačítko.  
5. V části **typ aplikace**vyberte **Konzolová aplikace (.exe)**.

6. V části **Additioal možnosti**, zrušte zaškrtnutí políčka **Předkompilovaná hlavička** zaškrtávací políčko.

7. Zvolte **OK** pro vytvoření projektu.  
  
##  <a name="UseLibInApp"></a> Pomocí funkcí ze statické knihovny v aplikaci  
  
#### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Využití funkcí ze statické knihovny v aplikaci  
  
1.  Jakmile vytvoříte konzolovou aplikaci, je vytvořen prázdný program. Název zdrojového souboru je stejný jako název, který jste zvolili dříve. V tomto příkladu je pojmenována **MyExecRefsLib.cpp**.  
  
2.  Před použitím matematických rutin ze statické knihovny, je nutné je odkazovat. Chcete-li to provést, otevřete místní nabídku projektu MyExecRefsLib v podokně **Průzkumníka řešení**a klikněte na tlačítko **přidat, odkazovat**.  
  
3.  **Přidat odkaz** dialogové okno obsahuje knihovny, které lze odkazovat. **Projekty** karta obsahuje seznam projektů v aktuálním řešení a všechny knihovny, které obsahují. Na **projekty** kartu, vyberte **MathFuncsLib** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.  
  
4.  Odkaz **MathFuncsLib.h** soubor hlaviček, je třeba změnit cesty obsažených adresářů. V **stránky vlastností** dialogové okno pro **MyExecRefsLib**, rozbalte **vlastnosti konfigurace** uzlu, rozbalte **C/C++** uzel, a potom vyberte **Obecné**. Vedle položky **další adresáře souborů k zahrnutí**, zadejte cestu **MathFuncsLib** adresář nebo procházením vyhledejte ho.  
  
     Procházením vyhledejte cestu k adresáři otevřete rozevírací seznam hodnot vlastnost a klikněte na tlačítko **upravit**. V **další adresáře souborů k zahrnutí** dialogové okno, v textovém poli vyberte prázdný řádek a pak zvolte tlačítko se třemi tečkami (**...** ) na konci řádku. V **vybrat adresář** dialogové okno, vyberte **MathFuncsLib** adresář a klikněte na tlačítko **vybrat složku** tlačítko pro výběr uložte a zavřete dialogové okno. V **další adresáře souborů k zahrnutí** dialogového okna zvolte **OK** tlačítko a potom v **stránky vlastností** dialogového okna zvolte **OK**tlačítko uložte provedené změny do projektu.  
  
5.  Teď můžete použít **MyMathFuncs** třídy v této aplikaci. Chcete-li to provést, nahraďte obsah **MyExecRefsLib.cpp** s tímto kódem:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]  
  
6.  Sestavte projekt výběrem **sestavení**, **sestavit řešení** na řádku nabídek.  
  
##  <a name="RunApp"></a> Spuštění aplikace  
  
#### <a name="to-run-the-app"></a>Ke spuštění aplikace  
  
1.  Ujistěte se, že **MyExecRefsLib** je vybraná jako výchozí projekt tak, že otevřete místní nabídku pro **MyExecRefsLib** v **Průzkumníka řešení**a poté volbou  **Nastavit jako spouštěný projekt**.  
  
2.  Chcete-li spustit projekt, na panelu nabídek, zvolte **ladění**, **spustit bez ladění**. Výstup by měl vypadat takto:  
  
    ```Output  
    a + b = 106.4  
    a - b = -91.6  
    a * b = 732.6  
    a / b = 0.0747475  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření a použití dynamické knihovny (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)   
 [Desktopové aplikace (Visual C++)](../windows/desktop-applications-visual-cpp.md)
