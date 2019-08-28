---
title: Přidání podpory knihovny ATL do projektu knihovny MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: fba79db013cd9f4cc62ba5826b53e5fa9b15c83a
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108419"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Přidání podpory knihovny ATL do projektu knihovny MFC

Pokud jste již vytvořili aplikaci založenou na knihovně MFC, můžete snadno přidat podporu pro knihovnu ATL (Active Template Library) pomocí integrovaného vývojového prostředí (IDE).

> [!NOTE]
>  Tato podpora se týká pouze jednoduchých objektů COM přidaných do spustitelného souboru MFC nebo projektu knihovny DLL. Do projektů knihovny MFC lze přidat další objekty COM (včetně ovládacích prvků ActiveX), ale objekty nemusí fungovat podle očekávání.

::: moniker range=">=vs-2019"

1. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu.

1. V místní nabídce klikněte na tlačítko **Přidat**a poté klikněte na položku **Nová položka**.

1. V levém podokně zvolte **ATL** a pak v prostředním podokně zvolte **Podpora ATL** .

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-add-atl-support-to-your-mfc-project"></a>Přidání podpory knihovny ATL do projektu knihovny MFC

1. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu.

1. V místní nabídce klikněte na **Přidat**a pak klikněte na **Přidat třídu**.

1. V levém podokně vyberte **ATL** a pak zvolte **Přidat podporu ATL do projektu MFC** v prostředním podokně.

::: moniker-end

Další informace o tom, jak Přidání podpory knihovny ATL změny kódu projektu knihovny MFC, naleznete v podrobnostech o [podpoře ATL přidané průvodcem knihovnou ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>Viz také:

[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepsání virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Obslužná rutina zpráv MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigace ve struktuře třídy](../../ide/navigate-code-cpp.md)
