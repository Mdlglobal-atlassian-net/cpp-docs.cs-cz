---
title: OLE ve MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
ms.openlocfilehash: 2594531df63bcd62cdaec44fbc3668ea68990922
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366901"
---
# <a name="ole-in-mfc"></a>OLE ve MFC

Tyto články vysvětlují základy programování OLE pomocí knihovny MFC. Knihovna MFC poskytuje nejjednodušší způsob psaní programů, které používají ole:

- Použití vizuálních úprav OLE (aktivace na místě).

- Chcete-li pracovat jako kontejnery OLE nebo servery.

- Chcete-li implementovat funkce přetažení myší.

- Práce s daty data a času.

- Chcete-li spravovat data stavu modulů knihovny MFC, včetně exportovaných vstupních bodů funkce knihovny DLL, vstupních bodů rozhraní OLE/COM a vstupních bodů procedury okna.

Můžete také použít [automatizaci](../mfc/automation.md).

> [!NOTE]
> Termín OLE označuje technologie spojené s propojením a vkládáním, včetně kontejnerů OLE, serverů OLE, položek OLE, aktivace (nebo vizuální úpravy), sledování, přetažení a slučování nabídek. Termín Aktivní se vztahuje na objekty com (COM) a objekty založené na modelu COM, jako jsou ovládací prvky ActiveX. Automatizace OLE se nyní nazývá Automatizace.

## <a name="in-this-section"></a>V tomto oddílu

[OLE – pozadí](../mfc/ole-background.md)<br/>
Popisuje OLE a poskytuje rámcové informace o tom, jak funguje.

[Aktivace](../mfc/activation-cpp.md)<br/>
Popisuje roli aktivace při úpravách položek OLE.

[Containers](../mfc/containers.md)<br/>
Obsahuje odkazy na použití kontejnerů v OLE.

[Datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-ole.md)<br/>
Obsahuje odkazy na témata, která `COleDataObject` `COleDataSource` popisují použití tříd a.

[Přetažení](../mfc/drag-and-drop-ole.md)<br/>
Popisuje použití kopírování a vkládání pomocí ole.

[Nabídky a zdroje OLE](../mfc/menus-and-resources-ole.md)<br/>
Vysvětluje použití nabídek a prostředků v dokumentových aplikacích knihovny MFC OLE.

[Registrace](../mfc/registration.md)<br/>
Popisuje instalaci a inicializaci serveru.

[Servery](../mfc/servers.md)<br/>
Popisuje, jak vytvořit položky OLE (nebo součásti) pro použití v aplikacích kontejneru.

[Snímače](../mfc/trackers.md)<br/>
Obsahuje informace `CRectTracker` o třídě, která poskytuje grafické rozhraní, které uživatelům umožňuje pracovat s položkami klienta OLE.

## <a name="related-sections"></a>Související oddíly

[Body připojení](../mfc/connection-points.md)<br/>
Vysvětluje, jak implementovat spojovací body (dříve označované jako ole `CCmdTarget` `CConnectionPoint`spojovací body) pomocí tříd knihovny MFC a .

[Komponenty com kontejneru/serveru](../mfc/containers-advanced-features.md)<br/>
Popisuje kroky nezbytné k začlenění volitelných pokročilých funkcí do existujících aplikací kontejneru.

[Objektový model komponenty](/windows/win32/com/the-component-object-model)<br/>
Popisuje použití ole bez knihovny MFC.

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)
