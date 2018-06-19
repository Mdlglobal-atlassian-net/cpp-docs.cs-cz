---
title: 'Návod: Vytvoření a použití statické knihovny (C++) | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
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
ms.openlocfilehash: d136dae553f623cbd607a69ab710fa9c6fe6c91b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891578"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>Návod: Vytvoření a použití statické knihovny (C++)
Tento podrobný návod ukazuje, jak vytvořit statické knihovny (soubor .lib) pro použití s aplikací C++. Použití statické knihovny je skvělým způsobem, jak kód opakovaně. Místo znovu implementace stejných rutin v každé aplikaci, která vyžaduje funkci, je napsat jednou v statické knihovny a pak na ni odkazujte z aplikací. Kód odkazované z statické knihovny stane součástí aplikace – nemusíte instalovat k použití kódu jiný soubor.  
  
 Tento názorný postup obsahuje tyto úlohy:  
  
-   [Vytvoření projektu statické knihovny](#BKMK_CreateLibProject)  
  
-   [Přidání třídy se statickou knihovnou](#BKMK_AddClassToLib)  
  
-   [Vytvoření konzolové aplikace C++, který odkazuje na statické knihovny](#BKMK_CreateAppToRefTheLib)  
  
-   [Pomocí funkce ze statické knihovny v aplikaci](#BKMK_UseLibInApp)  
  
-   [Spuštění aplikace](#BKMK_RunApp)  
  
## <a name="prerequisites"></a>Požadavky  
 Pochopení základy jazyka C++.  
  
##  <a name="BKMK_CreateLibProject"></a> Vytvoření projektu statické knihovny  
  
#### <a name="to-create-a-static-library-project"></a>Vytvoření projektu statické knihovny  
  
1.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
2.  V levém podokně **nový projekt** dialogové okno, rozbalte seznam **nainstalovaná**, **šablony**, **Visual C++** a potom vyberte  **Win32**.  
  
3.  V prostředním podokně vyberte **Konzolová aplikace Win32**.  
  
4.  Zadejte název projektu – například **MathFuncsLib**– v **název** pole. Zadejte název pro řešení – například **StaticLibrary**– v **název řešení** pole. Vyberte **OK** tlačítko.  
  
5.  Na **přehled** stránky **Win32 – Průvodce aplikací** dialogovém okně vyberte **Další** tlačítko.  
  
6.  Na **nastavení aplikace** v části **typ aplikace**, vyberte **statické knihovny.**  
  
7.  Na **nastavení aplikace** v části **další možnosti**, zrušte **předkompilované hlavičky** zaškrtávací políčko.  
  
8.  Vyberte **Dokončit** tlačítko pro vytvoření projektu.  
  
##  <a name="BKMK_AddClassToLib"></a> Přidání třídy se statickou knihovnou  
  
#### <a name="to-add-a-class-to-the-static-library"></a>Přidání třídy se statickou knihovnou  
  
1.  Pokud chcete vytvořit soubor hlaviček pro novou třídu, otevřete místní nabídku pro **MathFuncsLib** projektu v **Průzkumníku řešení**a potom vyberte **přidat**, **novou položku** . V **přidat novou položku** dialogovém v levém podokně v části **Visual C++**, vyberte **kód**. V prostředním podokně vyberte **soubor (hlaviček)**. Zadejte název pro soubor hlaviček – například **MathFuncsLib.h**– a potom zvolte **přidat** tlačítko. Zobrazí se prázdný hlavičkový soubor.  
  
2.  Přidejte třídu s názvem **MyMathFuncs** na běžné matematické operace, jako je přidání, odčítání, násobení a dělení. Kód by měl vypadat takto:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]  
  
3.  Chcete-li vytvořit zdrojový soubor pro novou třídu, otevřete místní nabídku pro **MathFuncsLib** projektu v **Průzkumníku řešení**a potom zvolte **přidat**, **novou položku** . V **přidat novou položku** dialogovém v levém podokně v části **Visual C++**, vyberte **kód**. V prostředním podokně vyberte **soubor C++ ()**. Zadejte název zdrojového souboru – například **MathFuncsLib.cpp**– a potom zvolte **přidat** tlačítko. Zobrazí se prázdný zdrojového souboru.  
  
4.  Použít k implementaci funkce pro tento zdrojový soubor **MyMathFuncs**. Kód by měl vypadat takto:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]  
  
5.  Zkompilujte se statickou knihovnou výběrem **sestavení**, **sestavit řešení** v řádku nabídek. Tím se vytvoří statickou knihovnu, kterou lze použít jiné programy.  
  
    > [!NOTE]
    >  Při sestavování v sadě Visual Studio příkazového řádku, musíte sestavit programu ve dvou krocích. Nejprve spustit **cl /c /EHsc MathFuncsLib.cpp** zkompilovat kód a vytvořte soubor objektu, který je pojmenován **MathFuncsLib.obj**. ( **Cl** příkaz vyvolá Kompilátor Cl.exe a **/c** možnost určuje kompilovat bez propojení. Další informace najdete v tématu [/c (Kompilovat bez propojení)](../build/reference/c-compile-without-linking.md).) Druhý, spusťte **lib MathFuncsLib.obj** k propojení kód a vytvořit se statickou knihovnou **MathFuncsLib.lib**. ( **Lib** příkaz vyvolá správce knihovny, Lib.exe. Další informace najdete v tématu [LIB odkaz](../build/reference/lib-reference.md).)  
  
##  <a name="BKMK_CreateAppToRefTheLib"></a> Vytvoření konzolové aplikace C++, který odkazuje na statické knihovny  
  
#### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>K vytvoření aplikace konzoly C++, která odkazuje na statické knihovny  
  
1.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
2.  V levém podokně v části **Visual C++**, vyberte **Win32**.  
  
3.  V prostředním podokně vyberte **Konzolová aplikace Win32**.  
  
4.  Zadejte název projektu – například **MyExecRefsLib**– v **název** pole. V rozevíracího seznamu vedle položky **řešení**, vyberte **přidat do řešení**. Tento postup přidá nový projekt na řešení, které obsahuje se statickou knihovnou. Vyberte **OK** tlačítko.  
  
5.  Na **přehled** stránky **Win32 – Průvodce aplikací** dialogovém okně vyberte **Další** tlačítko.  
  
6.  Na **nastavení aplikace** v části **typ aplikace**, vyberte **Konzolová aplikace**.  
  
7.  Na **nastavení aplikace** v části **další možnosti**, zrušte **předkompilované hlavičky** zaškrtávací políčko.  
  
8.  Vyberte **Dokončit** tlačítko pro vytvoření projektu.  
  
##  <a name="BKMK_UseLibInApp"></a> Pomocí funkce ze statické knihovny v aplikaci  
  
#### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Chcete použít funkci z se statickou knihovnou v aplikaci  
  
1.  Po vytvoření konzolové aplikace se vytvoří prázdný program. Název zdrojového souboru je stejný jako název, který jste zvolili dříve. V tomto příkladu je název **MyExecRefsLib.cpp**.  
  
2.  Matematické rutiny můžete použít v statickou knihovnu, musí být uveden. K tomuto účelu otevřete místní nabídku pro **MyExecRefsLib** projektu v **Průzkumníku řešení**a potom zvolte **odkazy**. V **MyExecRefsLibProperty stránky** dialogové okno, rozbalte seznam **společných vlastností** uzlu, vyberte **Framework a odkazy na**a potom vyberte **přidat Nový odkaz** tlačítko. Další informace o **odkazy** dialogové okno, najdete v části [přidávání odkazů](../ide/adding-references-in-visual-cpp-projects.md).  
  
3.  **Přidat odkaz na** zobrazí dialogové okno knihovny, které lze odkazovat. **Projekty** karta Vypíše seznam projektů v aktuálním řešení a všechny knihovny, které obsahují. Na **projekty** vyberte **MathFuncsLib** zaškrtněte políčko a potom vyberte **OK** tlačítko.  
  
4.  Odkazy **MathFuncsLib.h** soubor hlaviček, je třeba změnit cesty zahrnuté adresáře. V **stránky vlastností** dialogové okno pro **MyExecRefsLib**, rozbalte **vlastnosti konfigurace** uzlu, rozbalte **C/C++** uzel, a potom vyberte **Obecné**. Vedle **další adresáře Include**, zadejte cestu **MathFuncsLib** adresáře nebo procházením vyhledejte ho.  
  
     Chcete-li procházet cestu k adresáři, otevřete seznam vlastností hodnota rozevíracího seznamu a poté zvolte **upravit**. V **další adresáře Include** dialogové okno, v textovém poli, vyberte prázdný řádek a potom zvolte tlačítko se třemi tečkami (**...** ) na konci řádku. V **vyberte adresář** dialogové okno, vyberte **MathFuncsLib** adresář a potom zvolte **vyberte složku** tlačítko výběr uložte a zavřete dialogové okno. V **další adresáře Include** dialogové okno, vyberte **OK** tlačítko a potom v **stránky vlastností** dialogovém okně vyberte **OK**tlačítko uložte změny do projektu.  
  
5.  Teď můžete použít **MyMathFuncs** – třída v této aplikaci. Chcete-li to provést, nahraďte obsah **MyExecRefsLib.cpp** s tímto kódem:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]  
  
6.  Sestavení spustitelný soubor výběrem **sestavení**, **sestavit řešení** v řádku nabídek.  
  
##  <a name="BKMK_RunApp"></a> Spuštění aplikace  
  
#### <a name="to-run-the-app"></a>Ke spuštění aplikace  
  
1.  Ujistěte se, že **MyExecRefsLib** je vybraná jako výchozí projekt tak, že otevřete místní nabídku pro **MyExecRefsLib** v **Průzkumníku**a pak vyberete  **Nastavit jako spouštěný projekt**.  
  
2.  Chcete-li spustit projekt v řádku nabídek, zvolte **ladění**, **spustit bez ladění**. Výstup by měl vypadat takto:  
  
    ```Output  
    a + b = 106.4  
    a - b = -91.6  
    a * b = 732.6  
    a / b = 0.0747475  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření a použití dynamické knihovny (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)   
 [Desktopové aplikace (Visual C++)](../windows/desktop-applications-visual-cpp.md)