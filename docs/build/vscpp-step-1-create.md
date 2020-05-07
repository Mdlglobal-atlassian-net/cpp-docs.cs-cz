---
title: Vytvoření projektu aplikace konzoly C++
description: Pomocí Microsoft C++ v aplikaci Visual Studio vytvořte Hello World konzolovou aplikaci.
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

Obvyklým výchozím bodem pro programátory v jazyce C++ je "Hello, World!" aplikace, která běží na příkazovém řádku. To je to, co vytvoříte v aplikaci Visual Studio v tomto kroku.

## <a name="prerequisites"></a>Požadavky

- Máte aplikaci Visual Studio s nainstalovanou a spuštěnou úlohou vývoj desktopových aplikací v jazyce C++. Pokud ještě není nainstalován, přečtěte si téma [Instalace podpory C++ v aplikaci Visual Studio](vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Vytvoření projektu aplikace

Visual Studio používá *projekty* k uspořádání kódu pro aplikaci a *řešení* pro uspořádání vašich projektů. Projekt obsahuje všechny možnosti, konfigurace a pravidla používaná k sestavování aplikací. Spravuje vztah mezi všemi soubory projektu a všemi externími soubory. Chcete-li vytvořit aplikaci, nejprve vytvořte nový projekt a řešení.

::: moniker range=">=vs-2019"

1. V aplikaci Visual Studio otevřete nabídku **soubor** a výběrem možnosti **Nový > projekt** otevřete dialog **vytvořit nový projekt** . Vyberte šablonu **aplikace konzoly** , která obsahuje značky **C++**, **Windows**a **Console** , a pak klikněte na tlačítko **Další**.

   ![Vytvoření nového projektu](media/vs2019-choose-console-app.png "Otevření dialogového okna vytvořit nový projekt")

1. V dialogovém okně **Konfigurovat nový projekt** zadejte do textového pole **název projektu** *HelloWorld* . Vyberte **vytvořit** a vytvořte projekt.

   ![Název a vytvořit nový projekt](media/vs2019-configure-new-project-hello-world.png "Název a vytvořit nový projekt")

   Visual Studio vytvoří nový projekt. Je připravený na přidání a úpravu zdrojového kódu. Ve výchozím nastavení Šablona Konzolová aplikace vyplní ve zdrojovém kódu aplikaci Hello World:

   ![Hello World projektu v prostředí IDE](media/vs2019-hello-world-code.png "Hello World projektu v prostředí IDE")

   Když kód v editoru vypadá takto, jste připraveni přejít k dalšímu kroku a sestavit aplikaci.

[Narazili jsme na problém.](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. V aplikaci Visual Studio otevřete nabídku **soubor** a výběrem možnosti **Nový > projekt** otevřete dialogové okno **Nový projekt** .

   ![Otevření dialogového okna Nový projekt](media/vscpp-file-new-project.gif "Otevření dialogového okna Nový projekt")

1. V dialogovém okně **Nový projekt** vyberte možnost **nainstalované > Visual C++** , pokud již není vybrána, a pak zvolte **prázdnou šablonu projektu** . Do pole **název** zadejte *HelloWorld*. Kliknutím na **tlačítko OK** vytvořte projekt.

   ![Název a vytvořit nový projekt](media/vscpp-concierge-project-name-callouts.png "Název a vytvořit nový projekt")

Visual Studio vytvoří nový prázdný projekt. Je připraven, abyste se mohli specializovat na druh aplikace, kterou chcete vytvořit, a přidat soubory zdrojového kódu. Uděláte to za chvíli.

[Narazili jsme na problém.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Nastavení projektu jako konzolové aplikace

Visual Studio může vytvářet nejrůznější aplikace a komponenty pro Windows a další platformy. **Prázdná šablona projektu** není specifická pro typ aplikace, kterou vytvoří. *Konzolová aplikace* je jedna, která běží v okně konzoly nebo příkazového řádku. Chcete-li ho vytvořit, musíte aplikaci Visual Studio sdělit, aby používala podsystém konzoly.

1. V aplikaci Visual Studio otevřete nabídku **projekt** a kliknutím na možnost **vlastnosti** otevřete dialogové okno **stránky vlastností HelloWorld** .

1. V dialogovém okně **stránky vlastností** vyberte **Vlastnosti konfigurace > linker > systém**a potom zvolte pole pro úpravy vedle vlastnosti **subsystému** . V rozevírací nabídce, která se zobrazí, vyberte **Konzola (/SUBSYSTEM: Console)**. Kliknutím na **tlačítko OK** uložte změny.

   ![Otevřete dialogové okno stránky vlastností.](media/vscpp-properties-linker-subsystem.gif "Otevřete dialogové okno stránky vlastností.")

Visual Studio nyní ví, že má sestavit projekt pro spuštění v okně konzoly. Dále přidáte soubor zdrojového kódu a zadáte kód vaší aplikace.

[Narazili jsme na problém.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Přidat soubor zdrojového kódu

1. V **Průzkumník řešení**vyberte projekt HelloWorld. V panelu nabídek vyberte položky **projekt**, **Přidat novou položku** a otevřete tak dialogové okno **Přidat novou položku** .

1. V dialogovém okně **Přidat novou položku** vyberte v části **nainstalováno** **Visual C++** , pokud už není vybraná. V prostředním podokně vyberte **soubor C++ (. cpp)**. Změňte **název** na *HelloWorld. cpp*. Kliknutím na tlačítko **Přidat** zavřete dialogové okno a vytvořte soubor.

   ![Přidat zdrojový soubor pro HelloWorld. cpp](media/vscpp-add-new-item.gif "Přidat zdrojový soubor pro HelloWorld. cpp")

Visual Studio vytvoří nový prázdný soubor zdrojového kódu a otevře ho v okně editoru, které jste připraveni k zadání zdrojového kódu.

[Narazili jsme na problém.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Přidat kód do zdrojového souboru

1. Zkopírujte tento kód do okna editoru HelloWorld. cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Kód by měl vypadat jako v okně editoru:

   ![Kód Hello World v editoru](media/vscpp-hello-world-editor.png "Kód Hello World v editoru")

Když kód v editoru vypadá takto, jste připraveni přejít k dalšímu kroku a sestavit aplikaci.

[Narazili jsme na problém.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Sestavení a spuštění projektu C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Průvodce odstraňováním potíží

Zde najdete řešení běžných problémů při vytváření prvního projektu v jazyce C++.

### <a name="create-your-app-project-issues"></a>Vytvoření projektu aplikace: problémy

::: moniker range="vs-2019"

V dialogovém okně **Nový projekt** by se měla zobrazit Šablona **konzolové aplikace** , která obsahuje tagy **C++**, **Windows**a **Console** . Pokud ho nevidíte, existují dvě možné příčiny. Může být vyfiltrováno ze seznamu nebo nemusí být nainstalováno. Nejprve v horní části seznamu šablon ověřte rozevírací seznamy filtru. Nastavte je na **C++**, **Windows**a **konzolu**. Měla by se zobrazit Šablona **konzolové aplikace** jazyka C++. v opačném případě není nainstalovaná úloha **vývoj desktopových aplikací v C++** .

Pro instalaci **desktopového vývoje pomocí C++** můžete spustit instalační program přímo z dialogového okna **Nový projekt** . V dolní části seznamu šablon klikněte na odkaz **instalovat další nástroje a funkce a** spusťte instalační program. Pokud se v dialogu **řízení uživatelských účtů** požaduje oprávnění, vyberte **Ano**. V instalačním programu se ujistěte, že je zaškrtnuté políčko **vývoj desktopových aplikací v jazyce C++** . Pak zvolte **Upravit** a aktualizujte instalaci sady Visual Studio.

Pokud již existuje jiný projekt se stejným názvem, vyberte jiný název projektu. Případně odstraňte existující projekt a akci opakujte. Chcete-li odstranit existující projekt, odstraňte složku řešení (ve složce, která obsahuje soubor *HelloWorld. sln* ) v Průzkumníkovi souborů.

[Vraťte](#create-your-app-project)se.

::: moniker-end

::: moniker range="vs-2017"

Pokud se v dialogovém okně **Nový projekt** nezobrazí položka **Visual C++** v části **nainstalováno**, vaše kopie sady Visual Studio pravděpodobně nemá nainstalovanou úlohu **vývoj desktopových aplikací v jazyce C++** . Instalační program můžete spustit přímo v dialogovém okně **Nový projekt** . Kliknutím na odkaz **otevřít instalační program pro Visual Studio** spusťte instalační program znovu. Pokud se v dialogu **řízení uživatelských účtů** požaduje oprávnění, vyberte **Ano**. V případě potřeby aktualizujte instalační program. V instalačním programu se ujistěte, že je zaškrtnuté políčko **vývoj desktopových aplikací v jazyce C++** , a kliknutím na **tlačítko OK** aktualizujte instalaci sady Visual Studio.

::: moniker-end

::: moniker range="<=vs-2017"

Pokud již existuje jiný projekt se stejným názvem, vyberte jiný název projektu. Případně odstraňte existující projekt a akci opakujte. Chcete-li odstranit existující projekt, odstraňte složku řešení (ve složce, která obsahuje soubor *HelloWorld. sln* ) v Průzkumníkovi souborů.

[Vraťte](#create-your-app-project)se.

### <a name="make-your-project-a-console-app-issues"></a>Vytvoření projektu konzolové aplikace: problémy

Pokud nevidíte **linker** uvedený v části **Vlastnosti konfigurace**, klikněte na **tlačítko Storno** , čímž zavřete dialogové okno **stránky vlastností** . Než to zkusíte znovu, ujistěte se, že je v **Průzkumník řešení** vybraný projekt **HelloWorld** . Nevybírejte řešení **HelloWorld** nebo jinou položku v **Průzkumník řešení**.

Ovládací prvek rozevírací seznam se nezobrazí v poli pro úpravu vlastností **subsystému** , dokud nevyberete vlastnost. Kliknutím do pole pro úpravy ho vyberte. Nebo můžete stisknout klávesu **TAB** , abyste mohli cyklicky procházet ovládací prvky dialogu, dokud se nezvýrazní **podsystém** . Zvolte ovládací prvek rozevíracího seznamu nebo stiskněte klávesy **ALT + Šipka dolů** a otevřete jej.

[Přejít zpátky](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Přidat soubor zdrojového kódu: problémy

Je v pořádku, pokud poskytnete souboru zdrojového kódu jiný název. Nepřidávejte ale do projektu více než jeden soubor, který obsahuje stejný kód.

Pokud jste do projektu přidali nesprávný typ souboru, jako je například hlavičkový soubor, odstraňte jej a akci opakujte. Pokud chcete soubor odstranit, vyberte ho v **Průzkumník řešení**. Pak stiskněte klávesu **Delete** .

[Vraťte](#add-a-source-code-file)se.

### <a name="add-code-to-the-source-file-issues"></a>Přidat kód do zdrojového souboru: problémy

Pokud omylem zavřete okno Editor souborů zdrojového kódu, můžete ho snadno otevřít znovu. Otevřete ho tak, že dvakrát kliknete na HelloWorld. cpp v okně **Průzkumník řešení** .

Pokud se červené vlnovky zobrazují pod cokoli v editoru zdrojového kódu, zkontrolujte, že váš kód odpovídá příkladu v pravopisu, interpunkci a velikosti písmen. Případ je v kódu jazyka C++ významný.

[Vraťte](#add-code-to-the-source-file)se.

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
