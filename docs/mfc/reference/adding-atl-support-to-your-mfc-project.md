---
title: Přidání podpory knihovny ATL do projektu knihovny MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: 05c4e8ba54d9a573b422f136c9e8cf69e48d1c9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371686"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Přidání podpory knihovny ATL do projektu knihovny MFC

Pokud jste již vytvořili aplikaci založenou na knihovně MFC, můžete snadno přidat podporu pro knihovnu active template Library (ATL) pomocí ide.

> [!NOTE]
> Tato podpora platí pouze pro jednoduché objekty COM přidané do spustitelného souboru knihovny MFC nebo projektu knihovny DLL. Do projektů knihovny MFC můžete přidat další objekty COM (včetně ovládacích prvků ActiveX), ale objekty nemusí fungovat očekávaným způsobem.

::: moniker range=">=vs-2019"

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na uzel projektu.

1. V místní nabídce klikněte na **Přidat**a potom klikněte na **Nová položka**.

1. V levém podokně zvolte **atl** a v prostředním podokně zvolte **Podpora atl.**

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-add-atl-support-to-your-mfc-project"></a>Přidání podpory knihovny ATL do projektu knihovny MFC

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na uzel projektu.

1. V místní nabídce klikněte na **Přidat**a potom klikněte na **Přidat třídu**.

1. V levém podokně vyberte **knihovnu ATL** a v prostředním podokně zvolte **Přidat podporu knihovny ATL do projektu knihovny MFC.**

::: moniker-end

Další informace o tom, jak přidání podpory knihovny ATL změní kód projektu knihovny MFC, naleznete [v tématu Podrobnosti o podpoře knihovny ATL přidané průvodcem knihovny ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>Viz také

[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepsání virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Obslužná rutina zprávy knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigace ve struktuře třídy](../../ide/navigate-code-cpp.md)
