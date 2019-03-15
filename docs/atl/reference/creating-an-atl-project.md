---
title: Vytvoření projektu ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.project
helpviewer_keywords:
- ATL projects, creating
- ATL70.DLL
- _ATL_MIN_CRT macro
- distributing files with ATL components
ms.assetid: 061d5f98-f669-440e-9380-42f017a0f9e8
ms.openlocfilehash: d44434a36c8d757fb8f79d36a672c4c77de64ade
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820322"
---
# <a name="creating-an-atl-project"></a>Vytvoření projektu ATL

Nejjednodušší způsob, jak vytvořit projekt knihovny ATL je použití Průvodce projektem ATL, umístěný ve **projekty Win32** složky **nový projekt** dialogové okno.

## <a name="to-create-an-atl-project-using-the-atl-project-wizard"></a>Chcete-li vytvořit projekt knihovny ATL pomocí Průvodce projektem ATL

1. V sadě Visual Studio, zvolte **soubor > Nový > projekt** z hlavní nabídky.

1. Vyberte **projekt knihovny ATL** ikonu **šablony** podokně otevřete **Průvodce projektem ATL**.

1. Definujte nastavení aplikace pomocí [nastavení aplikace](../../atl/reference/application-settings-atl-project-wizard.md) stránku **Průvodce projektem ATL**.

   > [!NOTE]
   > Přeskočení tohoto kroku zachová průvodce výchozí nastavení.

1. Klikněte na tlačítko **Dokončit** zavřete průvodce a otevření nového projektu ve vývojovém prostředí.

Po vytvoření projektu lze zobrazit vytvořené soubory v **Průzkumníka řešení**. Další informace o souborech Průvodce vytvoří pro váš projekt, naleznete v generovaném souboru ReadMe.txt. Další informace o typech souborů naleznete v tématu [typy souborů vytvořené pro projekty Visual C++](../../build/reference/file-types-created-for-visual-cpp-projects.md). Další informace o konfiguraci pro nový projekt knihovny ATL a jejich změny najdete v tématu [výchozí konfigurace projektu ATL](../../atl/reference/default-atl-project-configurations.md).

## <a name="see-also"></a>Viz také:

[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Stránky vlastností](../../build/reference/property-pages-visual-cpp.md)
