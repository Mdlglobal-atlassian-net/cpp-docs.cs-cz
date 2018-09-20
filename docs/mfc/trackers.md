---
title: Snímače | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- trackers [MFC]
- OLE applications [MFC], trackers
- applications [OLE], trackers
- tracking OLE items [MFC]
- OLE containers [MFC], trackers
- CDC class [MFC], trackers
- CRectTracker class [MFC], implementing trackers
- OLE server applications [MFC], trackers
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 414a7c19292e154af0b6365b766d865dca0a7dd3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439864"
---
# <a name="trackers"></a>Snímače

[Crecttracker –](../mfc/reference/crecttracker-class.md) třída poskytuje uživatelské rozhraní mezi obdélníkové položek v aplikaci a uživatele tím, že poskytuje širokou škálu styly zobrazení. Tyto styly zahrnují plnou, šrafované nebo přerušované ohraničení; šrafované vzor, který obsahuje položky; a úchyty pro změnu velikosti, které mohou být umístěny na vnější nebo uvnitř ohraničení. Snímače jsou často používá ve spojení s položky OLE, to znamená, že objekty odvozené z `COleClientItem`. Sledování obdélníky poskytují vizuální upozornění na aktuální stav položky.

Ukázky knihovny MFC OLE [OCLIENT](../visual-cpp-samples.md) ukazuje obecné rozhraní pomocí analýzách a klientské položky OLE z hlediska aplikace typu kontejner. Ukázka různé styly a možnosti sledování objektu, najdete v ukázce MFC Obecné [sledování](../visual-cpp-samples.md).

Další informace o implementace snímačů ve vašich aplikacích OLE, naleznete v tématu [snímače: implementace snímačů ve OLE aplikace](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>Viz také

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleClientItem – třída](../mfc/reference/coleclientitem-class.md)
