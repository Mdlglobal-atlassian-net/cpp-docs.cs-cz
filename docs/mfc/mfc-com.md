---
title: MFC COM
ms.date: 09/12/2018
f1_keywords:
- MFC COM (MFC)
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
ms.openlocfilehash: 514251475050e728be1959417ead1dbdf96e4800
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358203"
---
# <a name="mfc-com"></a>MFC COM

Podmnožina knihovny MFC je navržena tak, aby podporovala model COM, zatímco většina knihovny active template Library (ATL) je určena pro programování modelové služby COM. Tato část témat popisuje podporu knihovny MFC pro model COM.

Aktivní technologie (například ovládací prvky ActiveX, Aktivní zadržování dokumentů, OLE a tak dále) používají model COM (Com) k tomu, aby softwarové součásti mohly vzájemně komunikovat v síťovém prostředí bez ohledu na jazyk, se kterým byly vytvořeny. Aktivní technologie lze použít k vytváření aplikací spuštěných na ploše nebo v Internetu. Další informace naleznete [v tématu Úvod do modelu COM](../atl/introduction-to-com.md) nebo Model [com](/windows/win32/com/the-component-object-model).

Aktivní technologie zahrnují klientské i serverové technologie, včetně následujících:

- Ovládací prvky ActiveX jsou interaktivní objekty, které lze použít v kontejnerech, jako je například web. Další informace o ovládacích prvcích ActiveX naleznete v tématu:

  - [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

  - [Ovládací prvky ActiveXna Internetu](../mfc/activex-controls-on-the-internet.md)

  - [Přehled: Internet](../mfc/mfc-internet-programming-basics.md)

  - [Upgrade existujícího ovládacího prvku ActiveX, který má být použit v Síti Internet](../mfc/upgrading-an-existing-activex-control.md)

  - [Ladění ovládacího prvku ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

- Aktivní skriptování řídí integrované chování jednoho nebo více ovládacích prvků ActiveX z prohlížeče nebo serveru. Další informace o aktivním skriptování naleznete v [tématu Active Technology on the Internet](../mfc/active-technology-on-the-internet.md).

- [Automatizace](../mfc/automation.md) (dříve označované jako AUTOMATIZACE OLE) umožňuje jedné aplikaci manipulovat s objekty implementovanými v jiné aplikaci nebo "vystavit" objekty, aby s nimi bylo možné manipulovat.

   Automatizovaný objekt může být místní nebo vzdálený (v jiném počítači přístupném v síti). Automatizace je k dispozici pro objekty OLE i COM.

- Tato část také obsahuje informace o tom, jak psát komponenty modelu COM pomocí knihovny MFC, například v [spojovacích bodech](../mfc/connection-points.md).

Diskuse o tom, co se stále nazývá OLE versus co se nyní nazývá aktivní technologie, naleznete v tématech na [OLE](../mfc/ole-in-mfc.md).

## <a name="in-this-section"></a>V tomto oddílu

[Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)

[Automation](../mfc/automation.md)

[Body připojení](../mfc/connection-points.md)

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)
