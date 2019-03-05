---
title: 'Kontejnery ovládacích prvků ActiveX: Zobrazení a úpravy vlastností ovládacích prvků'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
ms.openlocfilehash: 0a03acfd880bcf63017eec9796315b98e5d5f4d9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326358"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>Kontejnery ovládacích prvků ActiveX: Zobrazení a úpravy vlastností ovládacích prvků

Když je do projektu vložit ovládací prvek ActiveX, je užitečný k zobrazení a změna vlastností podporuje ovládací prvek ActiveX. Tento článek popisuje, jak k tomu použít editor prostředků Visual C++.

Pokud vaše kontejnerové aplikace ovládacího prvku ActiveX používá vložené ovládací prvky, můžete zobrazit a upravit vlastnosti ovládacího prvku v editoru prostředků. Editor prostředků můžete také použít k nastavení hodnot vlastností v době návrhu. Editor prostředků pak automaticky ukládá tyto hodnoty v souboru prostředků projektu. Všechny instance ovládací prvek pak bude mít inicializován na tyto hodnoty vlastností.

Tento postup předpokládá, že jste tam vložili ovládací prvek do projektu. Informace najdete v tématu [ActiveX – kontejnery ovládacích prvků: Vložení ovládacího prvku do kontejnerové aplikace ovládacího prvku](../mfc/inserting-a-control-into-a-control-container-application.md).

Prvním krokem při zobrazení vlastností ovládacího prvku je do projektu šablony dialogového okna přidat instanci ovládacího prvku.

### <a name="to-view-the-properties-of-a-control"></a>Chcete-li zobrazit vlastnosti ovládacího prvku

1. V okně zobrazení prostředků, otevřete **dialogové okno** složky.

1. Otevření šablony vaší hlavní dialogového okna.

1. Vložit ovládací prvek ActiveX pomocí **vložit ovládací prvek ActiveX** dialogové okno. Další informace najdete v tématu [zobrazení a přidání ovládacích prvků ActiveX do dialogového okna](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

1. V dialogovém okně vyberte ovládací prvek ActiveX.

1. V okně Vlastnosti klikněte **vlastnosti** tlačítko.

Použití **vlastnosti** dialogové okno Upravit a hned ho otestujte nové vlastnosti.

## <a name="see-also"></a>Viz také:

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)
