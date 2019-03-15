---
title: 'Postupy: Vytvoření projektu jazyka C++ z existujícího kódu'
ms.date: 01/15/2019
helpviewer_keywords:
- C++, creating projects from existing code
- Create New Project From Existing Code Files Wizard, project settings
f1_keywords:
- vc.appwiz.importwiz.location
- vc.appwiz.importwiz.appsettings
- vc.appwiz.importwiz.debugsettings
- vc.appwiz.importwiz.releasesettings
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
ms.openlocfilehash: 1658e19595d8cfc7966ca881abfdd2aa8acf76ab
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823192"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Postupy: Vytvoření projektu jazyka C++ z existujícího kódu

V sadě Visual Studio, můžete do projektu C++ s použitím portu existujících souborů kódu **vytvoření nového projektu z existujících souborů kódu** průvodce. Tento průvodce vytvoří řešení projekt, který používá systém MSBuild ke správě zdrojových souborů a konfiguraci sestavení. Funguje nejlépe s poměrně jednoduchá projekty, které nemají komplexních složky hierarchie. Průvodce není k dispozici ve starších edicích Express sady Visual Studio. 

Přenesení existujících souborů kódu do projektu jazyka C++ umožňuje použít nativní MSBuild funkce správy projektů integrovanou do rozhraní IDE. Pokud byste radši chtěli použít existující systém sestavení, jako jsou soubory pravidel nmake, CMake nebo alternativy, můžete místo toho použít možnosti Otevřít složku nebo CMake. Další informace najdete v tématu [projekty otevřít složku pro jazyk C++](open-folder-projects-cpp.md) nebo [projekty CMake v sadě Visual Studio](cmake-projects-in-visual-studio.md). Obě možnosti umožňují používat funkce rozhraní IDE, jako [IntelliSense](/visualstudio/ide/using-intellisense) a [vlastnosti projektu](working-with-project-properties.md).

### <a name="to-create-a-c-project-from-existing-code"></a>Vytvoření projektu jazyka C++ z existujícího kódu

1. Na **souboru** nabídce vyberte možnost **nový** > **projekt z existujícího kódu**.

1. První stránka **vytvořit nový projekt z existujících souborů kódu** průvodce, vyberte **Visual C++** v **jaký typ projektu chcete vytvořit?** seznamu. Zvolte **Další** pokračujte.

1. Zadejte umístění vašeho projektu, adresáře pro zdrojové soubory a typy souborů, které Průvodce naimportuje do nového projektu. Zvolte **Další** pokračujte.

    | Nastavení | Popis |
    | --- | --- |
    | **Umístění souboru projektu** | Určuje cestu k adresáři nový projekt. Toto umístění je, kde průvodce uloží všechny soubory (a jeho podadresářích) nového projektu.<br/><br/>Vyberte **Procházet** zobrazíte **umístění souboru projektu** dialogového okna. Přejděte do správné složky a určete adresář, který obsahuje nový projekt. |
    | **název projektu** | Určuje název nového projektu. Soubory projektu, které mají přípony souborů, jako je VCXPROJ přijme, tento název a existujících souborů kódu zachovají původní názvy. |
    | **Přidejte soubory do projektu z těchto složek** | Zaškrtněte, pokud chcete nastavit průvodcem ke kopírování existujících souborů kódu z jejich původní adresářů (které jsou uvedeny v seznamu pod tento ovládací prvek) do nového projektu.<br/><br/>Zkontrolujte **přidat podsložky** k určení kopírování souborů kódu ze všech podadresářů do projektu. Adresáře jsou uvedeny v **složky** sloupce.<br/>-Vybrat **přidat** zobrazíte **přidat soubory do projektu z této složky** dialogové okno, chcete-li určit adresáře, které průvodce vyhledá existujících souborů kódu.<br/>-Vybrat **odebrat** odstranit cestu k adresáři vybrali v rozevíracím seznamu.<br/><br/>V **typů, který chcete přidat do projektu soubor** zadejte typů souborů, které průvodce přidá nový projekt založený na daný soubor rozšíření. Přípony souborů jsou uvedeny s zástupný znak hvězdička a jsou odděleny středníky v seznamu přípon souborů. |
    | **Zobrazit všechny soubory v Průzkumníku řešení** | Určuje, že všechny soubory v novém projektu budou viditelné a v zobrazené **Průzkumníka řešení** okna. Tato možnost je povolená ve výchozím nastavení. |

    ![Umístění projektu](media/location.png)

1. Zadejte nastavení projektu použít například prostředí pro sestavení nového projektu a nastavení sestavení tak, aby odpovídaly konkrétní typ nový projekt generovat. Zvolte **Další** pokračujte.

    | Nastavení | Popis |
    | --- | --- |
    | **Pomocí sady Visual Studio** | Určuje použití nástroje pro vytváření, které jsou zahrnuty v sadě Visual Studio pro vytváření nového projektu. Ve výchozím nastavení je vybraná tato možnost.<br/><br/>Vyberte **typu projektu** k určení typu projektu vygeneruje průvodce. Zvolte **projekt aplikace Windows**, **projekt konzolové aplikace**, **projektu dynamické knihovny (DLL)**, nebo **statická knihovna (LIB) projekt**.<br/><br/>Zkontrolujte **přidat podporu ATL** přidat podporu ATL do nového projektu.<br/><br/>Zkontrolujte **přidat podporu knihovny MFC** k přidání podpory MFC do nového projektu.<br/><br/>Zkontrolujte **přidání podpory pro modul Common Language Runtime** přidat do projektu podporu CLR programování. Zvolte **Common Language Runtime Support** pro typ dodržování předpisů, jako například **Common Language Runtime (stará syntaxe)** dodržování předpisů s spravovaných rozšíření syntaxe jazyka C++, CLR programování syntaxe před Visual C++ 2005. |
    | **Použití externího sestavovacího systému** | Určuje použití nástroje sestavení, které nejsou zahrnuty v sadě Visual Studio pro vytváření nového projektu. Pokud je vybraná tato možnost, můžete určit příkazové řádky sestavení na **zadat konfigurační nastavení ladění** a **zadejte konfigurační nastavení vydání** stránky. |

    ![Nastavení projektu](media/settings.png)

    > [!NOTE]
    > Když **použijte externí sestavovací systém** zaškrtnete políčko, rozhraní IDE nedaří sestavit projekt, proto /D, / jsem, /FI, /AI nebo možnosti /FU nejsou požadovány pro kompilaci. Však musí tyto možnosti nastavit správně, aby IntelliSense fungovat správně.

1. Zadejte nastavení konfigurace ladění k použití. Zvolte **Další** pokračujte.

    | Nastavení | Popis |
    | --- | --- |
    | **Sestavení příkazového řádku** | Určuje příkazový řádek, který vytvoří projekt. Zadejte název kompilátor (plus všechny přepínače nebo argumenty) nebo skripty sestavení, kterou chcete použít k sestavení projektu. |
    | **Opětovné sestavení příkazového řádku** | Určuje příkazový řádek, který znovu sestaví nový projekt. |
    | **Příkazový řádek vyčištění** | Určuje příkazový řádek odstranit podpůrné soubory generované nástroje sestavení pro projekt. |
    | **Výstup (ladění)** | Určuje cestu k adresáři výstupních souborů pro konfiguraci ladění projektu. |
    | **Definice preprocesoru (/ D)** | Definuje symboly preprocesoru projekt, naleznete v tématu [/D (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md). |
    | **Zahrnout cestu vyhledávání (/ I)** | Určuje cesty k adresářům kompilátor vyhledá soubor odkazy předané preprocesoru direktiv v projektu vyřešit, najdete v článku [/I (další vložené adresáře)](../build/reference/i-additional-include-directories.md). |
    | **Nuceně zahrnuté soubory (/FI)** | Určuje soubory hlaviček zpracování při sestavování projektu, přečtěte si téma [/FI (vynucené soubor zahrnutí názvu)](../build/reference/fi-name-forced-include-file.md). |
    | **Cesta pro vyhledávání sestavení .NET (/ AI)** | Určuje adresář cesty, které kompilátor vyhledá vyřešit .NET sestavení odkazy předané preprocesoru direktiv v projektu, naleznete v tématu [/AI (zadat adresáře metadat)](../build/reference/ai-specify-metadata-directories.md). |
    | **Vynuceně použitá sestavení .NET (/ FU)** | Určuje sestavení .NET pro zpracování při sestavování projektu, naleznete v tématu [/FU (vynuceným názvem #using souboru)](../build/reference/fu-name-forced-hash-using-file.md). |

    ![Konfigurace projektu](media/config.png)

    > [!NOTE]
    > **Sestavení**, **znovu sestavit**, **Vyčistit** příkazového řádku a **výstup (ladění)** nastavení jsou povoleny pouze v případě **použití externí sestavovací systém** výběru na **zadejte nastavení projektu** stránky.

1. Zadejte konfigurační nastavení vydání chcete použít, tato nastavení jsou stejné jako nastavení konfigurace ladění. Zvolte **Dokončit** k vygenerování nového projektu.

    > [!NOTE]
    > Tady můžete zkontrolovat **stejný jako konfigurace ladění** k určení, že průvodce bude generovat verze konfigurace nastavení projektu identické a ladit nastavení projektu. Tato možnost je ve výchozím nastavení zaškrtnuto. Další možnosti na této stránce jsou neaktivní, dokud nezrušíte zaškrtnutí tohoto políčka.
