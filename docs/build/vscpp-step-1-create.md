---
title: Vytvoření projektu aplikace konzoly C++ | Microsoft Docs
description: Vytvořte aplikaci konzoly Hello World v jazyce Visual C++
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35b7b896dfb2a4c9dd37a9f59476cbc7f23c3902
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391230"
---
# <a name="create-a-c-console-app-project"></a>Vytvoření projektu aplikace konzoly C++

Obvyklým výchozím bodem pro programátory C++ text "Hello, world!" aplikace, která běží na příkazovém řádku. To je, co vytvoříte v sadě Visual Studio v tomto kroku.

## <a name="prerequisites"></a>Požadavky

- Visual Studio s vývoj aplikací máte C++ zatížení nainstalovaná a spuštěná v počítači. Pokud ještě není nainstalovaná, přečtěte si téma [podpory nainstalovat C++ v sadě Visual Studio](../build/vscpp-step-0-installation.md).

## <a name="create-your-app-project"></a>Vytvoření projektu aplikace

Visual Studio použije *projekty* k uspořádání kódu pro aplikace, a *řešení* k uspořádání vašich projektů. Projekt obsahuje možnosti, konfigurace a pravidel sloužící k vytvoření aplikace a spravuje vztah mezi soubory všechny projektu a externí soubory. Pokud chcete vytvořit aplikaci, nejprve vytvoříte nový projekt a řešení.

1. V sadě Visual Studio, otevřete **soubor** nabídky a zvolte **nový > projekt** otevřete **nový projekt** dialogové okno.

   ![Otevřete dialogové okno Nový projekt](../build/media/vscpp-file-new-project.gif "otevřete dialogové okno Nový projekt")

1. V **nový projekt** dialogovém okně, vyberte **nainstalovaná**, **Visual C++** Pokud již není vybrána a potom zvolte **prázdný projekt** Šablona. V **název** zadejte *HelloWorld*. Zvolte **OK** a vytvořte tak projekt.

   ![Název a vytvoření nového projektu](../build/media/vscpp-concierge-project-name-callouts.png "název a vytvoření nového projektu")

Visual Studio vytvoří nový, prázdný projekt, můžete se specializují pro typ aplikace, které chcete vytvořit a přidat zdrojové soubory vašeho kódu. Můžete to udělat tento další.

[Byl spuštěn na problém.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Zkontrolujte váš projekt konzolové aplikace

Visual Studio můžete vytvořit všechny typy aplikací a součástí systému Windows a jiné platformy. **Prázdný projekt** šablony není konkrétní o jaký typ aplikace vytvoří. Chcete-li vytvořit *konzolovou aplikaci*, jeden spuštěného v konzole nebo v okně příkazového řádku, se musí zjistit Visual Studio k sestavení aplikace používat subsystém konzoly.

1. V sadě Visual Studio, otevřete **projektu** nabídky a zvolte **vlastnosti** otevřete **stránky vlastností HelloWorld** dialogové okno.

1. V **stránky vlastností** dialogové okno, v části **vlastnosti konfigurace**, vyberte **Linkeru**, **systému**a potom zvolte pole vedle položky **subsystému** vlastnost. V rozevírací nabídce vyberte **konzoly (nebo subsystému: KONZOLA)**. Zvolte **OK** uložte provedené změny.

   ![Otevřete dialogové okno stránky vlastností](../build/media/vscpp-properties-linker-subsystem.gif "otevřete dialogové okno stránky vlastností")

Visual Studio teď zná k sestavení projektu ke spuštění v okně konzoly. Dále budete přidávat souboru zdrojového kódu a zadejte kód pro vaši aplikaci.

[Byl spuštěn na problém.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Přidání souboru zdrojového kódu

1. V **Průzkumníku**, vyberte projektu Hello World. Na řádku nabídek zvolte **projektu**, **přidat novou položku** otevřete **přidat novou položku** dialogové okno.

1. V **přidat novou položku** dialogovém okně, vyberte **Visual C++** pod **nainstalovaná** Pokud ještě není zaškrtnuto. V prostředním podokně vyberte **soubor C++ ()**. Změna **název** k *HelloWorld.cpp*. Zvolte **přidat** a zavřete dialogové okno vytvořit soubor.

   ![Přidání zdrojového souboru pro HelloWorld.cpp](../build/media/vscpp-add-new-item.gif "Přidání zdrojového souboru pro HelloWorld.cpp")

Visual studio vytvoří soubor nový, prázdný zdrojového kódu a otevře v okně editor, připraveno k zadání vašeho zdrojového kódu.

[Byl spuštěn na problém.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Přidejte kód ke zdrojovému souboru

1. Zkopírujte tento kód do okna editoru HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Kód by měl vypadat jako v okně editoru:

   ![Hello World kódu v editoru](../build/media/vscpp-hello-world-editor.png "Hello, World kódu v editoru")

Pokud kód vypadá takto v editoru, jste připravení přejděte k dalšímu kroku a sestavení aplikace.

[Byl spuštěn na problém.](#add-a-source-code-file-issues)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Sestavení a spuštění projektu jazyka C++](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Průvodce odstraňováním potíží s

Tohoto prostoru pro řešení pro běžné problémy při vytvoření prvního projektu C++.

### <a name="create-your-app-project-issues"></a>Vytvoření aplikace problémy projektu

Pokud **nový projekt** nezobrazí v dialogovém okně **Visual C++** položky v rámci **nainstalovaná**, vaší kopie Visual Studio pravděpodobně nemá **plochy vývoj s jazykem C++** zatížení nainstalována. Spuštěním instalačního programu přímo z **nový projekt** dialogové okno. Vyberte **otevřete instalační program Visual Studio** odkaz se znovu spustit instalační program. Pokud **řízení uživatelských účtů** dialogu vyžaduje oprávnění, zvolte **Ano**. V instalačním programu, ujistěte se, **vývoj aplikací s jazykem C++** zatížení je zaškrtnuté políčko a zvolte **OK** k aktualizaci instalace sady Visual Studio.

Pokud jiný projekt se stejným názvem již existuje, zvolte jiný název pro svůj projekt, nebo odstraňte existující projekt a zkuste to znovu. Pokud chcete odstranit existující projekt, odstraňte složku řešení (složka, která obsahuje soubor helloworld.sln) v Průzkumníku souborů.

[Přejděte zpět](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Zkontrolujte váš projekt problémů aplikace konzoly

Pokud nevidíte **Linkeru** uvedené v části **vlastnosti konfigurace**, zvolte **zrušit** zavřete **stránky vlastností** dialogové okno a potom Ujistěte se, že **HelloWorld** je vybrán projekt v **Průzkumníku řešení**, není řešení nebo jiného souboru nebo složky, teprve pak zkuste znovu.

V rozevíracím seznamu nezobrazí **subsystému** vlastnosti textového pole, dokud nevyberete vlastnost. Můžete ji vybrat pomocí ukazatele nebo stisknutím klávesy Tab cyklicky přepínat mezi ovládací prvky dialogového okna, dokud **subsystému** zvýrazní. Vyberte ovládací prvek rozevírací seznam nebo stiskněte klávesu Alt + Šipka dolů ho otevřete.

[Vrať se](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Přidat problémy souboru zdrojového kódu

Je to v pořádku Pokud zadejte jiný název souboru se zdrojovým kódem. Není ale přidat více než jeden souboru zdrojového kódu, který obsahuje stejný kód do projektu.

Pokud jste přidali chybný typ souboru do projektu, například soubor hlaviček odstraňte ji a zkuste to znovu. Chcete-li odstranit soubor, vyberte ho v **Průzkumníku řešení** a stiskněte klávesu Delete.

[Přejděte zpět](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Přidání kódu do problémům zdrojového souboru

Pokud jste omylem zavřeli zdrojového souboru okně editoru kódu, otevřete znovu, dvakrát klikněte na HelloWorld.cpp v **Průzkumníku řešení** okno.

Pokud se zobrazí červený podtržení vlnovkou pod nic v editoru zdrojového kódu, zkontrolujte, jestli odpovídá kódu v příkladu v pravopis a interpunkce a písmena. Případem je důležité v kódu jazyka C++.

[Přejděte zpět](#add-code-to-the-source-file).

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />