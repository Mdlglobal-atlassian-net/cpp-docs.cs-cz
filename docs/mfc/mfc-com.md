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
ms.openlocfilehash: a3da9e437dc9ca20aa2a02977b1c8653d68930f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645156"
---
# <a name="mfc-com"></a>MFC COM

Podmnožinu knihovny MFC je navržena pro podporu modelu COM, zatímco většina aktivní šablony knihovny (ATL) je určena k programování v modelu. Témata v této části popisuje podporu knihovny MFC pro modelu COM.

Aktivní technologie (například ActiveX ovládací prvky, zahrnutí aktivního dokumentu, OLE a tak dále) povolit softwarové komponenty komunikovat mezi sebou v síťovém prostředí, bez ohledu na jazyk, pomocí kterého byly pomocí modelu COM (Component Object) vytvořit. Technologie Active lze použít k vytvoření aplikace, které běží na ploše nebo na Internet. Další informace najdete v části [Úvod do modelu COM](../atl/introduction-to-com.md) nebo [The Component Object Model](/windows/desktop/com/the-component-object-model).

Aktivní technologie patří klientských i serverových technologií, včetně následujících:

- Ovládací prvky ActiveX jsou interaktivní objekty, které lze použít v kontejnery, jako jsou webové stránky. Další informace o ovládacích prvků ActiveX naleznete v tématu:

   - [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

   - [Ovládací prvky ActiveX na internetu](../mfc/activex-controls-on-the-internet.md)

   - [Přehled: Internet](../mfc/mfc-internet-programming-basics.md)

   - [Upgrade existujícího ovládacího prvku ActiveX pro použití na Internetu](../mfc/upgrading-an-existing-activex-control.md)

   - [Ladění ovládacího prvku ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

- Aktivní skriptování řídí chování integrované jeden nebo více ovládacích prvků ActiveX z prohlížeče nebo serveru. Další informace o aktivní skriptování najdete v tématu [technologie Active na Internetu](../mfc/active-technology-on-the-internet.md).

- [Automatizace](../mfc/automation.md) (dříve označované jako automatizace OLE) umožňuje pro jednu aplikaci k manipulaci s objekty, které jsou implementovány v jiné aplikaci, nebo "vystavit" objekty, lze manipulovat.

   Automatizované objekt může být místní nebo vzdálené (na jiném počítači dostupný přes síť). Služba Automation je dostupná pro OLE a modelu COM objekty.

- Tato část také obsahuje informace o tom, jak napsat komponenty modelu COM pomocí knihovny MFC, například v [spojovací body](../mfc/connection-points.md).

Diskuzi o co stále nazývá OLE a co se teď nazývá technologie active, naleznete v tématech na [OLE](../mfc/ole-in-mfc.md).

## <a name="in-this-section"></a>V tomto oddílu

[Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)

[Automatizace](../mfc/automation.md)

[Body připojení](../mfc/connection-points.md)

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)

