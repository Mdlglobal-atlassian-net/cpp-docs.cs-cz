---
title: OLE ve MFC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2a7fcd7db19d9dcc6e12c351a3fd55f0e67b118
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ole-in-mfc"></a>OLE ve MFC
Tyto články vysvětlují základní informace o použití prostředí MFC programování OLE. MFC poskytuje nejjednodušší způsob, jak psát programy, které používají OLE:  
  
-   Chcete-li použít OLE visual úpravy (místní aktivace).  
  
-   Pracovat jako kontejnery OLE nebo servery.  
  
-   K implementaci funkcí přetahování myší.  
  
-   Práce s daty datum a čas.  
  
-   Správa dat stavu MFC moduly, včetně exportovat vstupní body funkce DLL rozhraní OLE/COM – vstupní body a body vstupu procedury oken.  
  
 Můžete také použít [automatizace](../mfc/automation.md) nebo [vzdálené automatizace](../mfc/remote-automation.md) provoz jiný program z vaší aplikace.  
  
> [!NOTE]
>  Termín, který označuje OLE technologie související s propojování a vkládání, včetně kontejnery OLE, serverů OLE, OLE – položky, aktivace na místě (nebo úpravy s náhledem), snímačů, přetažení a slučování nabídek. Termín Active se vztahuje na modelu COM (Component Object) a objektů na základě modelu COM, jako je ovládací prvky ActiveX. OLE – automatizace nyní nazývá automatizace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [OLE – pozadí](../mfc/ole-background.md)  
 Popisuje OLE a obsahuje koncepční informace o tom, jak funguje.  
  
 [Aktivace](../mfc/activation-cpp.md)  
 Popisuje roli aktivace k úpravám OLE – položky.  
  
 [Kontejnery](../mfc/containers.md)  
 Obsahuje odkazy na použití kontejnerů v prostředí OLE.  
  
 [Datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-ole.md)  
 Obsahuje odkazy na témata pojednávající o použití `COleDataObject` a `COleDataSource` třídy.  
  
 [Přetažení](../mfc/drag-and-drop-ole.md)  
 Popisuje použití, kopírování a vkládání s OLE.  
  
 [OLE – nabídky a prostředky](../mfc/menus-and-resources-ole.md)  
 Popisuje použití nabídky a prostředky v aplikacích MFC OLE dokumentu.  
  
 [Registrace](../mfc/registration.md)  
 Popisuje instalaci serveru a inicializace.  
  
 [Servery](../mfc/servers.md)  
 Popisuje postup vytvoření OLE položky (nebo součásti) pro použití aplikacemi kontejneru.  
  
 [Snímače](../mfc/trackers.md)  
 Poskytuje informace o `CRectTracker` třídy, která poskytuje grafické rozhraní pro povolit uživatelům interakci s OLE klientské položky.  
  
## <a name="related-sections"></a>Související oddíly  
 [Body připojení](../mfc/connection-points.md)  
 Vysvětluje, jak implementovat spojovací body (dříve označované jako OLE spojovací body) pomocí třídy MFC `CCmdTarget` a `CConnectionPoint`.  
  
 [Součásti Server/kontejner modelu COM](../mfc/containers-advanced-features.md)  
 Popisuje kroky potřebné k začlenit volitelné pokročilých funkcí do existující aplikace typu kontejner.  
  
 [Komponentový objektový Model](http://msdn.microsoft.com/library/windows/desktop/ms694363)  
 Popisuje použití OLE bez MFC.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../mfc/mfc-concepts.md)
