---
title: 'OLE – pozadí: Strategie implementace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE [MFC], development strategy
- OLE applications [MFC], implementing OLE
- applications [OLE], implementing OLE
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe15690b50c9398d660ca53effbec23cc35f49e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ole-background-implementation-strategies"></a>OLE – pozadí: Strategie implementace
V závislosti na vaší aplikace jsou čtyři možné implementace strategie pro přidání podpory OLE:  
  
-   Vytváříte novou aplikaci.  
  
     Tato situace obvykle vyžaduje nejmenší fungovat. Spusťte Průvodce aplikací knihovny MFC a vyberte pro vytvoření kostru aplikace rozšířené funkce nebo složené podporu dokumentu. Informace o těchto možnostech a co dělají, najdete v článku [vytváření aplikace MFC EXE](../mfc/reference/mfc-application-wizard.md).  
  
-   Máte program napsané v knihovně tříd Foundation Microsoft verze 2.0 nebo vyšší, nepodporuje OLE.  
  
     Vytvořte novou aplikaci pomocí Průvodce aplikací MFC jak už jsme zmínili a pak zkopírujte a vložte kód z novou aplikaci do existující aplikace. To bude fungovat pro servery, kontejnery nebo automatizované aplikací. Najdete v článku MFC [KLIKYHÁKY](../visual-cpp-samples.md) ukázku příklad této strategie.  
  
-   Máte Microsoft Foundation Class Library program, který implementuje podporu OLE verze 1.0.  
  
     V tématu [MFC Technická poznámka 41](../mfc/tn041-mfc-ole1-migration-to-mfc-ole-2.md) pro tento převod strategie.  
  
-   Máte aplikaci, která nebyla zapsána pomocí třídy Microsoft Foundation a který může nebo nemusí mít implementována podpora OLE.  
  
     Tato situace vyžaduje nejvíce práce. Jeden ze způsobů je vytvoření nové aplikace, jako první strategie a pak zkopírujte a vložte do něj váš stávající kód. Pokud váš stávající kód je napsán v jazyce C, budete muset upravit tak, že ji můžete zkompilovat jako C++ – kód. Pokud váš kód C volá rozhraní API systému Windows, není nutné změňte ji na použití třídy Microsoft Foundation. Tento přístup pravděpodobně bude vyžadovat některé změnu struktury vašeho programu pro podporu architektury dokument/zobrazení používané verze 2.0 a vyšší třídy Microsoft Foundation. Další informace o této architektury, najdete v části [Technická poznámka 25](../mfc/tn025-document-view-and-frame-creation.md).  
  
 Jakmile jste se rozhodli strategie, měli byste buď pro čtení [kontejnery](../mfc/containers.md) nebo [servery](../mfc/servers.md) články (v závislosti na typu aplikace, které jsou zápisu) nebo prozkoumat ukázkové aplikace nebo obojí. Ukázky MFC OLE [OCLIENT](../visual-cpp-samples.md) a [HIERSVR](../visual-cpp-samples.md) ukazují, jak implementovat různé aspekty kontejnery a servery, v uvedeném pořadí. V různých okamžicích v těchto článcích budeme označovat na určité funkce v tyto ukázky jako příklady probíhá popsané postupy.  
  
## <a name="see-also"></a>Viz také  
 [OLE – pozadí](../mfc/ole-background.md)   
 [Kontejnery: Implementace kontejneru](../mfc/containers-implementing-a-container.md)   
 [Servery: Implementace serveru](../mfc/servers-implementing-a-server.md)   
 [MFC – průvodce aplikací](../mfc/reference/mfc-application-wizard.md)

