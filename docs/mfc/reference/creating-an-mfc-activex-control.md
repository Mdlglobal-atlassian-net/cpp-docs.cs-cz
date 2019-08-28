---
title: Vytvoření ovládacího prvku ActiveX knihovny MFC
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.activex.project
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
ms.openlocfilehash: d35b788910b0c73a3b6da85faf119958ffbccea0
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108444"
---
# <a name="creating-an-mfc-activex-control"></a>Vytvoření ovládacího prvku ActiveX knihovny MFC

Programy ovládacích prvků ActiveX jsou modulární programy určené k poskytnutí konkrétního typu funkce nadřazené aplikaci. Můžete například vytvořit ovládací prvek, například tlačítko pro použití v dialogovém okně nebo panel nástrojů pro použití na webové stránce.

>[!IMPORTANT]
> ActiveX je starší verze technologie, která by se neměla používat pro nový vývoj. Další informace najdete v tématu [ovládací prvky ActiveX](../activex-controls.md).

Nejjednodušší způsob, jak vytvořit ovládací prvek ActiveX knihovny MFC, je použít [Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/mfc-activex-control-wizard.md).

### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>Vytvoření ovládacího prvku ActiveX knihovny MFC pomocí Průvodce ovládacím prvkem ActiveX knihovny MFC

1. Postupujte podle pokynů v tématu nápovědy [Vytvoření aplikace MFC](creating-an-mfc-application.md) , ale zvolte **ovládací prvek ActiveX knihovny MFC** ze seznamu dostupných šablon.

1. Definujte [nastavení aplikace](../../mfc/reference/application-settings-mfc-activex-control-wizard.md), [názvy ovládacích prvků](../../mfc/reference/control-names-mfc-activex-control-wizard.md)a [nastavení řízení](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) pomocí Průvodce ovládacím prvkem ActiveX knihovny MFC.

    > [!NOTE]
    >  Tento krok přeskočte, pokud chcete zachovat výchozí nastavení průvodce.

1. Kliknutím na tlačítko **Dokončit** zavřete průvodce a otevřete nový projekt ve vývojovém prostředí.

Po vytvoření projektu můžete zobrazit soubory vytvořené v **Průzkumník řešení**. Další informace o souborech, které průvodce vytvoří pro váš projekt, naleznete v souboru Readme. txt generovaného projektem. Další informace o typech souborů naleznete v tématu [typy souborů vytvořené pro projekty aplikace Visual C++ Studio](../../build/reference/file-types-created-for-visual-cpp-projects.md).

Po vytvoření projektu můžete pomocí průvodců kódem přidat [funkce](../../ide/add-member-function-wizard.md), [proměnné](../../ide/add-member-variable-wizard.md), [události](../../ide/add-event-wizard.md), [vlastnosti](../../ide/names-add-property-wizard.md)a [metody](../../ide/add-method-wizard.md). Další informace o přizpůsobení ovládacího prvku ActiveX naleznete v tématu [ovládací prvky MFC ActiveX](../../mfc/mfc-activex-controls.md).

## <a name="see-also"></a>Viz také:

[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Stránky vlastností](../../build/reference/property-pages-visual-cpp.md)

