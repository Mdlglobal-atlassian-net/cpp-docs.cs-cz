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
ms.openlocfilehash: eab688022c311f3d20fc092736ee4c7d37232a43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508096"
---
# <a name="mfc-com"></a>MFC COM

Podmnožina knihovny MFC je navržena tak, aby podporovala model COM, zatímco většina knihoven ATL (Active Template Library) je navržena pro programování v modelu COM. Tato část témat popisuje podporu modelu COM v knihovně MFC.

Aktivní technologie (například ovládací prvky ActiveX, aktivní dokument, technologie OLE atd.) používají model COM (Component Object Model), který umožňuje softwarovým komponentám vzájemně komunikovat v síťovém prostředí, bez ohledu na jazyk, ve kterém byly vytvářejí. Aktivní technologie lze použít k vytváření aplikací, které běží na ploše nebo v Internetu. Další informace najdete v tématu [Úvod do modelu COM](../atl/introduction-to-com.md) nebo [model objektu součásti](/windows/win32/com/the-component-object-model).

Mezi aktivní technologie patří technologie klienta i serveru, včetně následujících:

- Ovládací prvky ActiveX jsou interaktivní objekty, které lze použít v kontejnerech, jako je například web. Další informace o ovládacích prvcích ActiveX najdete v těchto tématech:

   - [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

   - [Ovládací prvky ActiveX na internetu](../mfc/activex-controls-on-the-internet.md)

   - [Přehled Internet](../mfc/mfc-internet-programming-basics.md)

   - [Upgrade existujícího ovládacího prvku ActiveX pro použití na internetu](../mfc/upgrading-an-existing-activex-control.md)

   - [Ladění ovládacího prvku ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

- Aktivní skriptování řídí integrované chování jednoho nebo více ovládacích prvků ActiveX z prohlížeče nebo serveru. Další informace o aktivních skriptováních najdete v tématu [aktivní technologie na internetu](../mfc/active-technology-on-the-internet.md).

- [Automatizace](../mfc/automation.md) (dřív označované jako automatizace OLE) umožňuje jedné aplikaci manipulovat s objekty implementovanými v jiné aplikaci nebo "vystavovat" objekty, aby se mohly manipulovat.

   Automatický objekt může být místní nebo vzdálený (na jiném počítači, který je přístupný přes síť). Automatizace je k dispozici pro objekty OLE i COM.

- Tato část také poskytuje informace o tom, jak psát komponenty modelu COM pomocí knihovny MFC, například v [bodech připojení](../mfc/connection-points.md).

Diskuzi o tom, co se ještě říká technologii OLE a co se teď označuje jako aktivní technologie, najdete v tématech v tématu [OLE](../mfc/ole-in-mfc.md).

## <a name="in-this-section"></a>V tomto oddílu

[Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)

[Automatizace](../mfc/automation.md)

[Body připojení](../mfc/connection-points.md)

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Viz také:

[Charakteristiky](../mfc/mfc-concepts.md)
