---
title: 'Postupy: Vytvoření projektu jazyka C++ z existujícího kódu'
ms.date: 05/06/2019
helpviewer_keywords:
- C++, creating projects from existing code
- Create New Project From Existing Code Files Wizard, project settings
f1_keywords:
- vc.appwiz.importwiz.location
- vc.appwiz.importwiz.appsettings
- vc.appwiz.importwiz.debugsettings
- vc.appwiz.importwiz.releasesettings
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
ms.openlocfilehash: 5e59230186380b787c95dbe08914bcd9d3ca2407
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078542"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Postupy: Vytvoření projektu jazyka C++ z existujícího kódu

V aplikaci Visual Studio můžete portovat existující soubory kódu do projektu C++ pomocí průvodce **vytvořením nového projektu z existujících souborů kódu** . Tento průvodce vytvoří řešení projektu, které používá systém MSBuild ke správě zdrojových souborů a konfigurace sestavení. Funguje nejlépe s relativně jednoduchými projekty, které nemají složité hierarchie složek. Průvodce není dostupný ve starších edicích Express sady Visual Studio.

Přenos stávajících souborů s kódem do projektu jazyka C++ umožňuje použití nativních funkcí správy projektů MSBuild integrovaných do rozhraní IDE. Pokud dáváte přednost použití stávajícího sestavovacího systému, jako jsou soubory pravidel NMAKE, CMake nebo alternativy, můžete místo toho použít možnost otevřít složku nebo CMake. Další informace najdete v tématu [otevřené složky projekty pro projekty C++](open-folder-projects-cpp.md) nebo [cmake v sadě Visual Studio](cmake-projects-in-visual-studio.md). Obě možnosti umožňují používat funkce rozhraní IDE, jako jsou například [technologie IntelliSense](/visualstudio/ide/using-intellisense) a [Vlastnosti projektu](working-with-project-properties.md).

### <a name="to-create-a-c-project-from-existing-code"></a>Vytvoření projektu jazyka C++ z existujícího kódu

1. V nabídce **soubor** vyberte **Nový** > **projekt z existujícího kódu**.

1. Zadejte umístění projektu, adresář pro zdrojové soubory a typy souborů, které průvodce importuje do nového projektu. Pokračujte výběrem položky **Další**.

    | Nastavení | Popis |
    | --- | --- |
    | **Umístění souboru projektu** | Určuje cestu k adresáři nového projektu. Do tohoto umístění průvodce uloží všechny soubory (a podadresáře) nového projektu.<br/><br/>Vyberte **Procházet** a zobrazte tak dialogové okno **umístění souboru projektu** . Přejděte do správné složky a zadejte adresář, který obsahuje nový projekt. |
    | **Název projektu** | Určuje název nového projektu. Soubory projektu, které mají přípony souborů, například. vcxproj, přijímají tento název a stávající soubory s kódem udržují původní název. |
    | **Přidat soubory do projektu z těchto složek** | Zaškrtněte, pokud chcete, aby průvodce kopíroval stávající soubory kódu z původních adresářů (které jsou uvedeny v seznamu pod tímto ovládacím prvkem) do nového projektu.<br/><br/>Pokud chcete určit kopírování souborů kódu ze všech podadresářů do projektu, vyberte **Přidat podsložky** . Adresáře jsou uvedeny ve sloupci **Složka** .<br/>– Vyberte **Přidat** , chcete-li zobrazit dialogové okno **Přidat soubory do projektu z této složky** , chcete-li zadat adresáře, které Průvodce vyhledá existující soubory kódu.<br/>– Vyberte **Odebrat** , pokud chcete odstranit cestu k adresáři, kterou jste vybrali v rozevíracím seznamu.<br/><br/>V okně **typy souborů, které chcete přidat do pole projekt** zadejte typy souborů, které průvodce přidá do nového projektu na základě daných přípon souborů. Příponám souborů předchází zástupný znak hvězdička a jsou odděleny v seznamu přípon souborů středníkem. |
    | **Zobrazit všechny soubory v Průzkumník řešení** | Určuje, že se všechny soubory v novém projektu budou zobrazovat a zobrazovat v okně **Průzkumník řešení** . Tato možnost je ve výchozím nastavení povolená. |

    ![Umístění projektu](media/location.png)

1. Zadejte nastavení projektu, které se má použít, například prostředí sestavení pro nový projekt a nastavení sestavení tak, aby odpovídalo určitému typu nového projektu, který se má vygenerovat. Pokračujte výběrem položky **Další**.

    | Nastavení | Popis |
    | --- | --- |
    | **Použití sady Visual Studio** | Určuje použití nástrojů sestavení, které jsou součástí sady Visual Studio pro sestavení nového projektu. Tato možnost je ve výchozím nastavení zaškrtnutá.<br/><br/>Vyberte **typ projektu** a zadejte typ projektu, který průvodce vygeneruje. Vyberte **projekt aplikace systému Windows**, **projekt konzolové aplikace**, **projekt dynamické knihovny (DLL)** nebo **projekt statické knihovny (lib)**.<br/><br/>Pokud chcete přidat podporu ATL do nového projektu, podívejte se do **Přidat podporu pro ATL** .<br/><br/>Chcete-li přidat podporu knihovny MFC do nového projektu, je nutné zaškrtnout **Přidat podporu knihovny MFC** .<br/><br/>Pokud chcete přidat podporu programování CLR do projektu, podívejte se do **části přidat podporu pro modul CLR (Common Language Runtime)** . Zvolit podporu modulu CLR ( **Common Language** Runtime) pro typ dodržování předpisů, jako je například **Common Language Runtime (stará syntaxe)** pro dodržování předpisů pomocí syntaxe spravovaná rozšíření jazyka C++, před sadou Visual Studio 2005 se syntaxí programování CLR. |
    | **Použít externí sestavovací systém** | Určuje použití nástrojů sestavení, které nejsou součástí sady Visual Studio pro sestavení nového projektu. Pokud je vybrána tato možnost, můžete zadat příkazové řádky sestavení na stránce **zadat nastavení konfigurace ladění** a **zadat konfigurační nastavení vydání** . |

    ![Nastavení projektu](media/settings.png)

    > [!NOTE]
    > Pokud je zaškrtnuta možnost **použít externí sestavovací systém** , rozhraní IDE nevytvoří projekt, takže možnosti/D,/I,/Fi,/AI nebo/Fu nejsou pro kompilaci požadovány. Tyto možnosti je však nutné nastavit správně, aby technologie IntelliSense správně fungovala.

1. Zadejte nastavení konfigurace ladění, které se má použít. Pokračujte výběrem položky **Další**.

    | Nastavení | Popis |
    | --- | --- |
    | **Příkazový řádek sestavení** | Určuje příkazový řádek, který sestaví projekt. Zadejte název kompilátoru (spolu s přepínači nebo argumenty) nebo skripty sestavení, které chcete použít k sestavení projektu. |
    | **Příkazový řádek pro opětovné sestavení** | Určuje příkazový řádek, který znovu sestaví nový projekt. |
    | **Příkazový řádek vyčištění** | Určuje příkazový řádek, který má odstranit podpůrné soubory generované nástroji sestavení pro projekt. |
    | **Výstup (pro ladění)** | Určuje cestu k adresáři výstupních souborů pro konfiguraci ladění projektu. |
    | **Definice preprocesoru (/D)** | Definuje symboly preprocesoru pro projekt, viz [/d (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md). |
    | **Cesta hledání zahrnutí (/I)** | Určuje cesty k adresářům, které kompilátor hledá, aby vyřešil odkazy na soubory předané do direktiv preprocesoru v projektu, viz [/i (další adresáře k zahrnutí)](../build/reference/i-additional-include-directories.md). |
    | **Nuceně zahrnuté soubory (/FI)** | Určuje soubory hlaviček, které se mají zpracovat při sestavování projektu, viz [/Fi (soubor vynuceného zahrnutí názvu)](../build/reference/fi-name-forced-include-file.md). |
    | **Cesta pro vyhledávání sestavení .NET (/AI)** | Určuje cesty k adresářům, které kompilátor vyhledává pro překlad odkazů na sestavení .NET předaných do direktiv preprocesoru v projektu, viz [/AI (určení adresářů metadat)](../build/reference/ai-specify-metadata-directories.md). |
    | **Vynucené používání sestavení .NET (/FU)** | Určuje sestavení .NET, která se mají zpracovat při sestavování projektu, viz [/Fu (název vynuceného #using souboru)](../build/reference/fu-name-forced-hash-using-file.md). |

    ![Konfigurace projektu](media/config.png)

    > [!NOTE]
    > Nastavení **sestavit**, **znovu sestavit**, **vyčistit** příkazový řádek a **výstup (pro ladění)** jsou povolena pouze v případě, že je vybrána možnost **použít externí sestavovací systém** na stránce **zadat nastavení projektu** .

1. Zadejte nastavení konfigurace verze, která se mají použít. Tato nastavení jsou stejná jako nastavení konfigurace ladění. Kliknutím na tlačítko **Dokončit** Vygenerujte nový projekt.

    > [!NOTE]
    > Tady můžete stejnou kontrolu **jako konfigurace ladění** , abyste určili, že průvodce generuje nastavení projektu konfigurace vydané verze shodná s nastavením ladění projektu konfigurace. Tato možnost je ve výchozím nastavení zaškrtnutá. Všechny ostatní možnosti na této stránce jsou neaktivní, pokud zrušíte jeho zrušení.
