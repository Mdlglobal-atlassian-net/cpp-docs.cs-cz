---
title: 'ActiveX – kontejnery ovládacích prvků: Zobrazení a úprava vlastností ovládacího prvku'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
ms.openlocfilehash: 1d42820efd06c2ae52f5d1b22b0bdfb6335c4a89
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907808"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>ActiveX – kontejnery ovládacích prvků: Zobrazení a úprava vlastností ovládacího prvku

Při vložení ovládacího prvku ActiveX do projektu je užitečné zobrazit a změnit vlastnosti podporované ovládacím prvkem ActiveX. Tento článek popisuje, jak k tomu použít C++ Editor vizuálních prostředků.

Pokud vaše aplikace kontejneru ovládacího prvku ActiveX používá vložené ovládací prvky, můžete zobrazit a upravit vlastnosti ovládacího prvku v editoru prostředků. Editor prostředků můžete také použít k nastavení hodnot vlastností během doby návrhu. Editor prostředků pak tyto hodnoty automaticky uloží do souboru prostředků projektu. Všechny instance ovládacího prvku budou mít do těchto hodnot inicializovány jeho vlastnosti.

Tento postup předpokládá, že jste do svého projektu vložili ovládací prvek. Informace najdete v tématu [kontejnery ovládacích prvků ActiveX: Vložení ovládacího prvku do aplikace](../mfc/inserting-a-control-into-a-control-container-application.md)kontejneru ovládacího prvku.

Prvním krokem při prohlížení vlastností ovládacího prvku je přidání instance ovládacího prvku do šablony dialogového okna projektu.

### <a name="to-view-the-properties-of-a-control"></a>Zobrazení vlastností ovládacího prvku

1. V Prostředky otevřete složku **dialogového okna** .

1. Otevřete svou hlavní šablonu dialogového okna.

1. Vložení ovládacího prvku ActiveX pomocí dialogového okna **Vložit ovládací prvek ActiveX** . Další informace najdete v tématu [zobrazení a přidání ovládacích prvků ActiveX do dialogového okna](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

1. V dialogovém okně vyberte ovládací prvek ActiveX.

1. V okně **vlastnosti** klikněte na tlačítko **vlastnosti** .

Pomocí dialogového okna **vlastnosti** můžete okamžitě upravit a otestovat nové vlastnosti.

## <a name="see-also"></a>Viz také:

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)
