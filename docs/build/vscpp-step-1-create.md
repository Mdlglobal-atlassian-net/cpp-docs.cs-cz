---
title: Vytvoření projektu aplikace konzoly C++
description: Vytvořte konzolovou aplikaci Hello World pomocí Microsoft C++ v Sadě Visual Studio.
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 07e88da9a8a3712e1d37e319c29fd25aebce8ea7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749310"
---
# <a name="create-a-c-console-app-project"></a>Vytvoření projektu aplikace konzoly C++

Obvyklým výchozím bodem pro programátor c++ je "Hello, world!" aplikace, která běží na příkazovém řádku. To je to, co vytvoříte v sadě Visual Studio v tomto kroku.

## <a name="prerequisites"></a>Požadavky

- Mít Visual Studio s desktopvývoj s c++ úlohy nainstalované a spuštěné v počítači. Pokud ještě není nainstalovaná, přečtěte si informace [o instalaci podpory C++ v sadě Visual Studio](vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Vytvoření projektu aplikace

Visual Studio používá *projekty* k uspořádání kódu pro aplikaci a *řešení* pro uspořádání projektů. Projekt obsahuje všechny možnosti, konfigurace a pravidla používaná k vytváření aplikací. Spravuje vztah mezi všemi soubory projektu a všechny externí soubory. Chcete-li vytvořit aplikaci, nejprve vytvoříte nový projekt a řešení.

::: moniker range=">=vs-2019"

1. V Sadě Visual Studio otevřete nabídku **Soubor** a zvolte **Nový > Project,** **chcete-li** otevřít dialogové okno Vytvořit nový projekt. Vyberte šablonu **konzolové aplikace** se značkami **C++,** **Windows**a **Console** a pak zvolte **Další**.

   ![Vytvoření nového projektu](media/vs2019-choose-console-app.png "Otevření dialogového okna Vytvořit nový projekt")

1. V dialogovém **okně Konfigurovat nový projekt** zadejte *HelloWorld* do pole pro **úpravy názvu projektu.** Chcete-li vytvořit projekt, zvolte **Vytvořit.**

   ![Pojmenování a vytvoření nového projektu](media/vs2019-configure-new-project-hello-world.png "Pojmenování a vytvoření nového projektu")

   Visual Studio vytvoří nový projekt. Je připraven pro přidání a úpravu zdrojového kódu. Ve výchozím nastavení šablona Konzolové aplikace vyplní váš zdrojový kód aplikací "Hello World":

   ![Hello World projekt v IDE](media/vs2019-hello-world-code.png "Hello World projekt v IDE")

   Když kód vypadá takto v editoru, jste připraveni přejít k dalšímu kroku a vytvořit aplikaci.

[Narazil jsem na problém.](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. V Sadě Visual Studio otevřete nabídku **Soubor** a zvolte **Nový > Project,** chcete-li otevřít dialogové okno **Nový projekt.**

   ![Otevření dialogového okna Nový projekt](media/vscpp-file-new-project.gif "Otevření dialogového okna Nový projekt")

1. V dialogovém okně **Nový projekt** vyberte Nainstalovat > **Visual C++,** pokud ještě není vybraný, a pak zvolte **šablonu Prázdný projekt.** Do pole **Název** zadejte *HelloWorld*. Chcete-li vytvořit projekt, zvolte **OK.**

   ![Pojmenování a vytvoření nového projektu](media/vscpp-concierge-project-name-callouts.png "Pojmenování a vytvoření nového projektu")

Visual Studio vytvoří nový, prázdný projekt. Je připraven pro vás specializovat na druh aplikace, kterou chcete vytvořit, a přidat soubory zdrojového kódu. Uděláte to za chvíli.

[Narazil jsem na problém.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Nastavení aplikace pro konzolu v projektu

Visual Studio můžete vytvářet všechny druhy aplikací a komponent pro Windows a další platformy. Šablona **Prázdný projekt** není konkrétní o tom, jaký druh aplikace vytvoří. *Konzolová aplikace* je aplikace, která běží v okně konzoly nebo příkazového řádku. Chcete-li vytvořit, musíte říct Visual Studio vytvořit aplikaci používat podsystém konzoly.

1. V Sadě Visual Studio otevřete nabídku **Projekt** a zvolte **Vlastnosti,** chcete-li otevřít dialogové okno **Stránky vlastností HelloWorld.**

1. V dialogovém okně **Stránky vlastností** vyberte **Vlastnosti konfigurace > propojovací > systéma**a pak zvolte textové pole vedle vlastnosti **Subsystem.** V rozevírací nabídce, která se zobrazí, vyberte **Console (/SUBSYSTEM:CONSOLE)**. Chcete-li uložit změny, zvolte **OK.**

   ![Otevření dialogového okna Stránky vlastností](media/vscpp-properties-linker-subsystem.gif "Otevření dialogového okna Stránky vlastností")

Visual Studio teď ví, že může vytvořit projekt, který bude spuštěn v okně konzoly. Dále přidáte soubor zdrojového kódu a zadáte kód pro vaši aplikaci.

[Narazil jsem na problém.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Přidání souboru zdrojového kódu

1. V **Průzkumníku řešení**vyberte projekt HelloWorld. Na řádku nabídek zvolte **Projekt**, **Přidat novou položku** a otevřete dialogové okno **Přidat novou položku.**

1. V dialogovém okně **Přidat novou položku** vyberte **Visual C++** v části **Nainstalováno,** pokud ještě není vybrané. V prostředním podokně vyberte **soubor C++ (.cpp)**. Změňte **název** na *HelloWorld.cpp*. Zvolte **Přidat,** chcete-li dialog zavřít a vytvořit soubor.

   ![Přidání zdrojového souboru pro soubor HelloWorld.cpp](media/vscpp-add-new-item.gif "Přidání zdrojového souboru pro soubor HelloWorld.cpp")

Visual Studio vytvoří nový prázdný soubor zdrojového kódu a otevře jej v okně editoru, připravený k zadání zdrojového kódu.

[Narazil jsem na problém.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Přidání kódu do zdrojového souboru

1. Zkopírujte tento kód do okna editoru HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Kód by měl vypadat takto v okně editoru:

   ![Hello World kód v editoru](media/vscpp-hello-world-editor.png "Hello World kód v editoru")

Když kód vypadá takto v editoru, jste připraveni přejít k dalšímu kroku a vytvořit aplikaci.

[Narazil jsem na problém.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Sestavení a spuštění projektu Jazyka C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Průvodce odstraňováním potíží

Přijďte sem pro řešení běžných problémů při vytváření prvního projektu C++.

### <a name="create-your-app-project-issues"></a>Vytvoření projektu aplikace: problémy

::: moniker range="vs-2019"

Dialogové okno **Nový projekt** by mělo zobrazovat šablonu **konzolové aplikace,** která obsahuje značky **C++,** **Windows**a **Console.** Pokud to nevidíte, existují dvě možné příčiny. Může být odfiltrován ze seznamu nebo není nainstalován. Nejprve zkontrolujte rozevírací seznamy filtrů v horní části seznamu šablon. Nastavte je na **C++**, **Windows**a **Console**. Měla by se zobrazit šablona **konzolové aplikace** jazyka C++; v opačném případě není nainstalován vývoj plochy s úlohami **C++.**

Chcete-li nainstalovat **vývoj plochy s c++**, můžete spustit instalační program přímo z dialogového okna **Nový projekt.** Chcete-li spustit instalační program, zvolte v dolní části seznamu šablon odkaz **Instalovat další nástroje a funkce.** Pokud dialogové okno **Řízení uživatelských účtů** požaduje oprávnění, zvolte **Ano**. V instalačním programu zkontrolujte, zda je kontrolován vývoj plochy s úlohami **Jazyka C++.** Pak zvolte **Změnit,** chcete-li aktualizovat instalaci sady Visual Studio.

Pokud jiný projekt se stejným názvem již existuje, zvolte jiný název projektu. Nebo odstraňte existující projekt a akci opakujte. Chcete-li odstranit existující projekt, odstraňte složku řešení (složku, která obsahuje soubor *helloworld.sln)* v Průzkumníkovi souborů.

[Vrať se.](#create-your-app-project)

::: moniker-end

::: moniker range="vs-2017"

Pokud dialogové okno **Nový projekt** nezobrazuje položku **Visual C++** v části **Nainstalováno**, vaše kopie Sady Visual Studio pravděpodobně nemá nainstalovaný vývoj plochy s úlohami **C++.** Instalační program můžete spustit přímo z dialogového okna **Nový projekt.** Chcete-li instalační program znovu spustit, zvolte odkaz **Otevřít instalační program sady Visual Studio.** Pokud dialogové okno **Řízení uživatelských účtů** požaduje oprávnění, zvolte **Ano**. V případě potřeby aktualizujte instalační program. V instalačním programu zkontrolujte, zda je zkontrolován vývoj plochy s úlohami **jazyka C++,** a zvolte **OK,** chcete-li aktualizovat instalaci sady Visual Studio.

::: moniker-end

::: moniker range="<=vs-2017"

Pokud jiný projekt se stejným názvem již existuje, zvolte jiný název projektu. Nebo odstraňte existující projekt a akci opakujte. Chcete-li odstranit existující projekt, odstraňte složku řešení (složku, která obsahuje soubor *helloworld.sln)* v Průzkumníkovi souborů.

[Vrať se.](#create-your-app-project)

### <a name="make-your-project-a-console-app-issues"></a>Nastavení aplikace pro konzolu v projektu: problémy

Pokud **linker** v části **Vlastnosti konfigurace**nevidíte , zvolte **Storno** a zavřete dialogové okno **Stránky vlastností.** Ujistěte se, že projekt **HelloWorld** je vybrán v **Průzkumníku řešení,** než to zkusíte znovu. Nevybírejte v **Průzkumníku řešení**řešení **helloworld** ani jinou položku.

Ovládací prvek rozevíracího kódu se nezobrazí v poli úprav vlastností **SubSystem,** dokud vlastnost nevyberete. Klepnutím do textového pole ho vyberte. Nebo můžete stisknutím **klávesy Tab** cykinožovat ovládací prvky dialogu, dokud nebude zvýrazněn **subsystém.** Zvolte ovládací prvek rozevírací nebo ho otevřete stisknutím **kláves Alt+Down.**

[Přejít zpátky](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Přidání souboru zdrojového kódu: problémy

Je to v pořádku, pokud dáte souborzdrojového kódu jiný název. Nepřidávejte však do projektu více než jeden soubor, který obsahuje stejný kód.

Pokud jste do projektu přidali nesprávný typ souboru, například soubor záhlaví, odstraňte jej a zkuste to znovu. Chcete-li soubor odstranit, vyberte jej v **Průzkumníku řešení**. Pak stiskněte klávesu **Delete.**

[Vrať se.](#add-a-source-code-file)

### <a name="add-code-to-the-source-file-issues"></a>Přidání kódu do zdrojového souboru: problémy

Pokud jste omylem zavřeli okno editoru souborů zdrojového kódu, můžete jej snadno znovu otevřít. Chcete-li jej otevřít, poklepejte na HelloWorld.cpp v okně **Průzkumník řešení.**

Pokud se pod čímkoli v editoru zdrojového kódu zobrazí červené vlnovky, zkontrolujte, zda se váš kód shoduje s příkladem pravopisu, interpunkce a velikosti písmen. Případ je významný v kódu jazyka C++.

[Vrať se.](#add-code-to-the-source-file)

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
