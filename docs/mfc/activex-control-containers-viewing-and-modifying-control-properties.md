---
title: 'Kontejnery ovládacích prvků ActiveX: Zobrazení a úprava vlastností ovládacího prvku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- properties [MFC], viewing and modifying
- ActiveX control containers [MFC], viewing and modifying properties
- resource editors, viewing and modifying ActiveX controls
- ActiveX controls [MFC], properties
- controls [MFC], properties
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9614ecfcd23418f8b0abc08622e8c272bb5548a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388820"
---
# <a name="activex-control-containers-viewing-and-modifying-control-properties"></a>ActiveX – kontejnery ovládacích prvků: Zobrazení a úpravy vlastností ovládacích prvků

Když je do projektu vložit ovládací prvek ActiveX, je užitečný k zobrazení a změna vlastností podporuje ovládací prvek ActiveX. Tento článek popisuje, jak k tomu použít editor prostředků Visual C++.

Pokud vaše kontejnerové aplikace ovládacího prvku ActiveX používá vložené ovládací prvky, můžete zobrazit a upravit vlastnosti ovládacího prvku v editoru prostředků. Editor prostředků můžete také použít k nastavení hodnot vlastností v době návrhu. Editor prostředků pak automaticky ukládá tyto hodnoty v souboru prostředků projektu. Všechny instance ovládací prvek pak bude mít inicializován na tyto hodnoty vlastností.

Tento postup předpokládá, že jste tam vložili ovládací prvek do projektu. Informace najdete v tématu [ActiveX – kontejnery ovládacích prvků: vložení ovládacího prvku do ovládací prvek aplikace typu kontejner pro](../mfc/inserting-a-control-into-a-control-container-application.md).

Prvním krokem při zobrazení vlastností ovládacího prvku je do projektu šablony dialogového okna přidat instanci ovládacího prvku.

### <a name="to-view-the-properties-of-a-control"></a>Chcete-li zobrazit vlastnosti ovládacího prvku

1. V okně zobrazení prostředků, otevřete **dialogové okno** složky.

1. Otevření šablony vaší hlavní dialogového okna.

1. Vložit ovládací prvek ActiveX pomocí **vložit ovládací prvek ActiveX** dialogové okno. Další informace najdete v tématu [zobrazení a přidání ovládacích prvků ActiveX do dialogového okna](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md).

1. V dialogovém okně vyberte ovládací prvek ActiveX.

1. V okně Vlastnosti klikněte **vlastnosti** tlačítko.

Použití **vlastnosti** dialogové okno Upravit a hned ho otestujte nové vlastnosti.

## <a name="see-also"></a>Viz také

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

