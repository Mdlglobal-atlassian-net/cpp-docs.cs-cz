---
title: 'OLE – pozadí: Strategie implementace'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE [MFC], development strategy
- OLE applications [MFC], implementing OLE
- applications [OLE], implementing OLE
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
ms.openlocfilehash: 83a1089ecaaaa9bd0dd1d928cd3d1869e5017a4a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774383"
---
# <a name="ole-background-implementation-strategies"></a>OLE – pozadí: Strategie implementace

V závislosti na vaší aplikace jsou čtyři možnou implementaci strategie pro přidání podpory OLE:

- Vytváříte nové aplikace.

   Tato situace obvykle vyžaduje nejméně fungovat. Spusťte Průvodce aplikací knihovny MFC a vyberte vytvoření kostru aplikace rozšířené funkce nebo Podpora složených dokumentů. Informace o těchto možnostech a co dělají, najdete v článku [vytvoření aplikace MFC EXE](../mfc/reference/mfc-application-wizard.md).

- Je nutné programu, vytvořeném pomocí knihovny tříd Foundation Microsoft verze 2.0 nebo novější, který nepodporuje OLE.

   Vytvoření nové aplikace pomocí Průvodce aplikací MFC, jak už jsme zmínili a pak zkopírujte a vložte kód z nové aplikace do existující aplikace. To bude fungovat pro servery, kontejnery nebo automatizované aplikací. Knihovny MFC naleznete v tématu [SCRIBBLE](../overview/visual-cpp-samples.md) Vzorový příklad této strategie.

- Máte knihovny Microsoft Foundation Class program, který implementuje podporu verze 1.0 OLE.

   Zobrazit [41 Technická poznámka MFC](../mfc/tn041-mfc-ole1-migration-to-mfc-ole-2.md) pro tato strategie převodu.

- Když máte aplikaci, který nebyl zapsán pomocí tříd Microsoft Foundation a který může nebo nemusí mít implementované podporu technologie OLE.

   Tato situace vyžaduje nejvíce práce. Jedním z přístupů je vytvoření nové aplikace, stejně jako v prvním strategie a pak zkopírujte a vložte do něj existující kód. Pokud váš stávající kód je napsán v jazyce C, budete muset upravit ho tak lze kompilovat jako kód jazyka C++. Pokud váš kód C volá rozhraní Windows API, není nutné změňte ji na použití tříd Microsoft Foundation. Tento postup, pravděpodobně bude vyžadovat některé restrukturalizaci programu pro podporu architektury dokument/zobrazení používané verze 2.0 a vyšší tříd Microsoft Foundation. Další informace na této architektuře, najdete v části [Technická poznámka 25](../mfc/tn025-document-view-and-frame-creation.md).

Jakmile jste se rozhodli strategii, měli byste buď čtení [kontejnery](../mfc/containers.md) nebo [servery](../mfc/servers.md) články (v závislosti na typu aplikace, kterou píšete) nebo prozkoumat ukázkové aplikace, nebo obojí. Ukázky knihovny MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) a [HIERSVR](../overview/visual-cpp-samples.md) ukazují, jak provádět různé aspekty kontejnery a servery, v uvedeném pořadí. V různých okamžicích v těchto článcích bude odkazovat na určité funkce v těchto ukázkách jako příklady techniky diskutovány.

## <a name="see-also"></a>Viz také:

[OLE – pozadí](../mfc/ole-background.md)<br/>
[Kontejnery: Implementace kontejneru](../mfc/containers-implementing-a-container.md)<br/>
[Servery: Implementace serveru](../mfc/servers-implementing-a-server.md)<br/>
[MFC – průvodce aplikací](../mfc/reference/mfc-application-wizard.md)
