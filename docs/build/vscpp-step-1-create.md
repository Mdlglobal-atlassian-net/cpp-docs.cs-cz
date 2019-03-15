---
title: Vytvoření projektu aplikace konzoly C++
description: Vytvoření konzolové aplikace Hello World v jazyce Visual C++
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 3bbbd40534e3e429d68dbb6205134c57db40c851
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817722"
---
# <a name="create-a-c-console-app-project"></a>Vytvoření projektu aplikace konzoly C++

Obvyklým výchozím bodem pro programátor C++ je "Hello, world!" aplikace, která běží na příkazovém řádku. To je, co vytvoříte v sadě Visual Studio v tomto kroku.

## <a name="prerequisites"></a>Požadavky

- Sada Visual Studio s vývoj desktopových aplikací pomocí úlohy pro C++ nainstalovaný a spuštěný ve vašem počítači. Pokud ještě není nainstalovaný, přečtěte si téma [podpora instalace jazyka C++ v sadě Visual Studio 2017](vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Vytvoření projektu aplikace

Visual Studio používá *projekty* organizaci kódu pro aplikace, a *řešení* k uspořádání vašich projektů. Projekt obsahuje všechny možnosti, konfigurace a pravidla používaná k vytváření aplikací a spravuje vztah mezi všechny projektových souborů a externí soubory. Pokud chcete vytvořit aplikaci, nejprve vytvoříte nový projekt a řešení.

1. V sadě Visual Studio, otevřete **souboru** nabídku a zvolte **nový > projekt** otevřete **nový projekt** dialogového okna.

   ![Otevřete dialogové okno Nový projekt](media/vscpp-file-new-project.gif "otevřete dialogové okno Nový projekt")

1. V **nový projekt** dialogového okna, vyberte **nainstalováno**, **Visual C++** Pokud již není vybraná a klikněte na tlačítko **prázdný projekt** Šablona. V **název** zadejte *HelloWorld*. Zvolte **OK** pro vytvoření projektu.

   ![Název a vytvořte nový projekt](media/vscpp-concierge-project-name-callouts.png "název a vytvořte nový projekt")

Visual Studio vytvoří nový, prázdný projekt, můžete specializovat pro typ aplikace, kterou chcete vytvořit a přidat soubory zdrojového kódu. Uděláte to teď.

[Můžu narazili na problém.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Ujistěte se, váš projekt konzolové aplikace

Visual Studio můžete vytvářet všechny typy aplikací a součástí pro Windows a jiné platformy. **Prázdný projekt** šablony není konkrétní o jaký druh aplikace vytvoří. Chcete-li vytvořit *konzolovou aplikaci*, jeden, který běží v konzole nebo okna příkazového řádku, je zapotřebí sdělit Visual Studio k vytvoření aplikace pro použití konzoly subsystému.

1. V sadě Visual Studio, otevřete **projektu** nabídku a zvolte **vlastnosti** otevřete **stránky vlastností HelloWorld** dialogového okna.

1. V **stránky vlastností** dialogového okna, v části **vlastnosti konfigurace**vyberte **Linkeru**, **systému**a pak zvolte textové pole vedle **subsystému** vlastnost. V rozevírací nabídce vyberte **konzoly (/ SUBSYSTEM: CONSOLE)**. Zvolte **OK** uložte provedené změny.

   ![Otevřete dialogové okno stránky vlastností](media/vscpp-properties-linker-subsystem.gif "otevřete dialogové okno stránky vlastností")

Visual Studio nyní ví k sestavení projektu pro spuštění v okně konzoly. Budete v dalším kroku přidáte soubor zdrojového kódu a zadejte kód pro vaši aplikaci.

[Můžu narazili na problém.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Přidat soubor zdrojového kódu

1. V **Průzkumníka řešení**, vyberte projekt Hello World. V panelu nabídky zvolte **projektu**, **přidat novou položku** otevřít **přidat novou položku** dialogového okna.

1. V **přidat novou položku** dialogového okna, vyberte **Visual C++** pod **nainstalováno** Pokud již není vybraná. V prostředním podokně vyberte **soubor C++ (.cpp)**. Změnit **název** k *HelloWorld.cpp*. Zvolte **přidat** a zavřete dialogové okno pro vytvoření souboru.

   ![Přidání zdrojového souboru pro HelloWorld.cpp](media/vscpp-add-new-item.gif "Přidání zdrojového souboru pro HelloWorld.cpp")

Visual studio vytvoří nový, prázdný zdrojový soubor kódu a otevře jej v okně editoru zadejte zdrojový kód jste připravení.

[Můžu narazili na problém.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Přidejte kód do zdrojového souboru

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

   ![Hello World kódu v editoru](media/vscpp-hello-world-editor.png "kódu Hello World v editoru")

Když kód vypadá takto v editoru, jste připraveni přejít další krok a sestavení aplikace.

[Můžu narazili na problém.](#add-a-source-code-file-issues)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Sestavit a spustit projekt jazyka C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Průvodce odstraňováním potíží

Jsou zde pro řešení běžných potíží s když vytvoříte svůj první projekt C++.

### <a name="create-your-app-project-issues"></a>Vytvoření aplikace pro projekt problémy

Pokud **nový projekt** nezobrazí dialogové okno **Visual C++** položku **nainstalováno**, vaše kopie sady Visual Studio pravděpodobně nemá **Desktop vývoj aplikací pomocí C++** nainstalovaná úloha. Můžete spustit instalační program přímo **nový projekt** dialogového okna. Zvolte **otevřít instalační program Visual Studio** odkaz na instalační program spusťte znovu. Pokud **řízení uživatelských účtů** dialogové okno požádá o oprávnění, zvolte **Ano**. V instalačním programu, ujistěte se, že **vývoj desktopových aplikací pomocí C++** úlohy je zaškrtnuté políčko a zvolte **OK** k aktualizaci instalace Visual Studio.

Pokud jiný projekt se stejným názvem už existuje, zvolte jiný název projektu, nebo odstranit existující projekt a zkuste to znovu. Pokud chcete odstranit existující projekt, odstraňte složku řešení (složka, která obsahuje soubor helloworld.sln) v Průzkumníku souborů.

[Přejděte zpět](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Ujistěte se, váš projekt problémů s aplikací konzoly

Pokud nevidíte **Linkeru** uvedené v části **vlastnosti konfigurace**, zvolte **zrušit** zavřete **stránky vlastností** dialogové okno a potom Ujistěte se, že **HelloWorld** projekt určený v **Průzkumníka řešení**, ne řešení nebo jiného souboru nebo složky, před dalším pokusem.

Ovládací prvek dropdown se nezobrazují v **subsystému** vlastnost textové pole, dokud nevyberete vlastnost. Můžete určit pomocí ukazatele nebo stisknete klávesu Tab k cyklování skrze ovládací prvky dialogového okna do **subsystému** je zvýrazněn. Zvolte ovládací prvek dropdown nebo stisknutím klávesy Alt + Šipka dolů a otevřete ho.

[Vrať se](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Přidat potíže s zdrojový kód souboru

Je v pořádku, pokud zadejte jiný název souboru se zdrojovým kódem. Není však přidat více než jeden zdrojový soubor kódu, který obsahuje stejný kód do vašeho projektu.

Pokud přidáte nesprávný typ souboru do projektu, například soubor hlaviček, odstraňte ho a zkuste to znovu. Pokud chcete odstranit soubor, vyberte ho v **Průzkumníka řešení** a stiskněte klávesu Delete.

[Přejděte zpět](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Přidání kódu do zdrojového souboru problémy

Pokud jste omylem zavřeli zdrojového souboru oknem editoru kódu, otevřete znovu, dvakrát klikněte na HelloWorld.cpp v **Průzkumníka řešení** okna.

Pokud v části všechno v editoru zdrojového kódu se zobrazí červenou vlnovkou, zkontrolujte, jestli váš kód odpovídá příklad v pravopisu, interpunkce a případ. Případ je důležité v kódu jazyka C++.

[Přejděte zpět](#add-code-to-the-source-file).

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
