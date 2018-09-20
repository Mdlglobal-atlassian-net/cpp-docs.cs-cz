---
title: OLE ve MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e43484e5f30191c604f43a2280a8deab6eddd93c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434944"
---
# <a name="ole-in-mfc"></a>OLE ve MFC

Tyto články vysvětlují základní informace o použití prostředí MFC programování technologie OLE. Knihovna MFC poskytuje nejjednodušší způsob, jak psát programy, které používají OLE:

- Použití OLE vizuální úpravy (aktivace na místě).

- Chcete-li fungují jako kontejnery OLE nebo servery.

- K implementaci funkcí přetahování myší.

- Pro práci s data a času.

- Abyste mohli spravovat data stavu knihovny MFC moduly, včetně exportovat vstupní body DLL – funkce rozhraní OLE/COM – vstupní body a body vstupu procedury oken.

Můžete také použít [automatizace](../mfc/automation.md).

> [!NOTE]
>  Termín, který označuje OLE technologie přidružené propojování a vkládání, jako jsou kontejnery OLE, serverů OLE, položky OLE, aktivace na místě (nebo vizuální úpravy), snímače, přetáhnout a slučováním nabídek. Termín Active se vztahuje na modelu COM (Component Object) a založený na modelu COM objektů, jako je ovládací prvky ActiveX. Automatizace OLE se teď nazývá automatizace.

## <a name="in-this-section"></a>V tomto oddílu

[OLE – pozadí](../mfc/ole-background.md)<br/>
Tento článek popisuje OLE a obsahuje koncepční informace o tom, jak funguje.

[Aktivace](../mfc/activation-cpp.md)<br/>
Popisuje role aktivace v úpravách položky OLE.

[Kontejnery](../mfc/containers.md)<br/>
Obsahuje odkazy na použití kontejnerů v prostředí OLE.

[Datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-ole.md)<br/>
Obsahuje odkazy na témata popisující použití `COleDataObject` a `COleDataSource` třídy.

[Přetažení](../mfc/drag-and-drop-ole.md)<br/>
Popisuje použití, kopírování a vkládání technologií OLE.

[OLE – nabídky a prostředky](../mfc/menus-and-resources-ole.md)<br/>
Vysvětluje použití nabídky a prostředky v aplikacích MFC OLE dokumentu.

[Registrace](../mfc/registration.md)<br/>
Tento článek popisuje instalaci serveru a inicializace.

[Servery](../mfc/servers.md)<br/>
Popisuje, jak vytvořit OLE položky (nebo komponent) pro použití aplikací typu kontejner.

[Snímače](../mfc/trackers.md)<br/>
Poskytuje informace o `CRectTracker` třídu, která poskytuje grafické rozhraní pro povolení uživatelům interakci s klientské položky OLE.

## <a name="related-sections"></a>Související oddíly

[Body připojení](../mfc/connection-points.md)<br/>
Vysvětluje, jak implementovat spojovací body (dříve OLE spojovací body) pomocí tříd knihovny MFC `CCmdTarget` a `CConnectionPoint`.

[Komponenty modelu COM Server/kontejner](../mfc/containers-advanced-features.md)<br/>
Popisuje kroky potřebné k začlenit volitelné pokročilé funkce do stávajících aplikací typu kontejner.

[Component Object Model](/windows/desktop/com/the-component-object-model)<br/>
Popisuje použití OLE bez knihovny MFC.

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)

