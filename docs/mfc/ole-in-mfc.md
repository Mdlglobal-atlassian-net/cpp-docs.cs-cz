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
ms.openlocfilehash: 2668d35c24e9d95440a96c5b3eda1fab7bbf3891
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507988"
---
# <a name="ole-in-mfc"></a>OLE ve MFC

Tyto články vysvětlují základy programování OLE pomocí knihovny MFC. Knihovna MFC poskytuje nejjednodušší způsob psaní programů, které používají technologii OLE:

- Použití úprav vizuálů OLE (místní aktivace).

- Pro práci jako kontejnery OLE nebo servery.

- Implementuje funkci přetažení myší.

- Pro práci s daty data a času.

- Pro správu dat stavu modulů knihovny MFC, včetně vstupních bodů funkce exportovaných knihoven DLL, vstupních bodů rozhraní OLE/COM a vstupních bodů procedury okna.

Můžete také použít [automatizaci](../mfc/automation.md).

> [!NOTE]
>  Pojem OLE označuje technologie spojené s propojením a vkládáním, včetně kontejnerů OLE, serverů OLE, položek OLE, místní aktivace (nebo úprav vizuálů), sledovacích, přetahování a slučování nabídek. Pojem aktivní platí pro objekty modelu COM (Component Object Model) a COM, jako jsou například ovládací prvky ActiveX. Automatizace OLE se teď nazývá automatizace.

## <a name="in-this-section"></a>V tomto oddílu

[OLE – pozadí](../mfc/ole-background.md)<br/>
Popisuje technologii OLE a poskytuje koncepční informace o tom, jak funguje.

[Aktivace](../mfc/activation-cpp.md)<br/>
Popisuje roli aktivace při úpravách položek OLE.

[Kontejnery](../mfc/containers.md)<br/>
Obsahuje odkazy na používání kontejnerů v technologii OLE.

[Datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-ole.md)<br/>
Obsahuje odkazy na témata pojednávající o použití `COleDataObject` tříd a. `COleDataSource`

[Přetažení](../mfc/drag-and-drop-ole.md)<br/>
Popisuje použití kopírování a vkládání pomocí technologie OLE.

[OLE – nabídky a prostředky](../mfc/menus-and-resources-ole.md)<br/>
Vysvětluje použití nabídek a prostředků v aplikacích knihovny MFC technologie OLE.

[Registrace](../mfc/registration.md)<br/>
Popisuje instalaci a inicializaci serveru.

[Servery](../mfc/servers.md)<br/>
Popisuje, jak vytvořit položky OLE (nebo komponenty) pro použití v aplikacích kontejneru.

[Snímače](../mfc/trackers.md)<br/>
Poskytuje informace o `CRectTracker` třídě, která poskytuje grafické rozhraní umožňující uživatelům interakci s klientskými položkami OLE.

## <a name="related-sections"></a>Související oddíly

[Body připojení](../mfc/connection-points.md)<br/>
Vysvětluje, jak implementovat body připojení (dříve označované jako spojovací body OLE) pomocí tříd `CCmdTarget` knihovny MFC a. `CConnectionPoint`

[Komponenty COM kontejneru/serveru](../mfc/containers-advanced-features.md)<br/>
Popisuje kroky nutné k začlenění volitelných pokročilých funkcí do stávajících aplikací kontejneru.

[Objektový model součásti](/windows/win32/com/the-component-object-model)<br/>
Popisuje použití technologie OLE bez knihovny MFC.

## <a name="see-also"></a>Viz také:

[Charakteristiky](../mfc/mfc-concepts.md)
