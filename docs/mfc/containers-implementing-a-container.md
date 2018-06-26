---
title: 'Kontejnery: Implementace kontejneru | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 066c032a18b2fedc88884b7e6eee55f07fcf43ad
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930072"
---
# <a name="containers-implementing-a-container"></a>Kontejnery: Implementace kontejneru
Tento článek shrnuje postup pro implementace kontejneru a bodů na další články, které poskytují podrobnější vysvětlení o implementaci kontejnery. Jsou také uvedeny některé volitelné funkce OLE, které chcete implementovat a články popisující tyto funkce.  
  
#### <a name="to-prepare-your-cwinapp-derived-class"></a>Příprava vlastní třídy odvozené CWinApp  
  
1.  Inicializace knihovny OLE voláním `AfxOleInit` v `InitInstance` – členská funkce.  
  
2.  Volání `CDocTemplate::SetContainerInfo` v `InitInstance` k přiřazení nabídky a akcelerátoru prostředky používá při vložené položky aktivovat na místě. Další informace v tomto tématu najdete v tématu [aktivace](../mfc/activation-cpp.md).  
  
 Pro vás jsou dostupné tyto funkce: automaticky při použití Průvodce aplikací MFC k vytvoření aplikace kontejnerů. V tématu [vytváření aplikace MFC EXE](../mfc/reference/mfc-application-wizard.md).  
  
#### <a name="to-prepare-your-view-class"></a>Příprava třídě zobrazení  
  
1.  Sledovat udržováním ukazatel jednotlivé vybrané položky nebo seznamu ukazatelů pokud podporujete vícenásobný výběr k vybrané položky. Vaše `OnDraw` funkce musí kreslení všechny položky OLE.  
  
2.  Přepsání `IsSelected` ke kontrole, jestli aktuálně vybranou položku do ní předán.  
  
3.  Implementace `OnInsertObject` popisovač zpráv se má zobrazit **vložit objekt** dialogové okno.  
  
4.  Implementace `OnSetFocus` zpráva obslužná rutina přenos fokus ze zobrazení do místní službě active OLE vložených položek.  
  
5.  Implementace `OnSize` popisovač zpráv, které informují OLE vložených položek, že je nutné změnit jeho obdélníku, aby odrážely změny velikosti jeho obsahující zobrazení.  
  
 Protože implementace tyto funkce se značně liší z jedné aplikace na další, Průvodce aplikací poskytuje jenom základní implementaci. Budete pravděpodobně muset upravit tyto funkce pro uvedení aplikace fungovat správně. Příklady, najdete v článku [KONTEJNERU](../visual-cpp-samples.md) ukázka.  
  
#### <a name="to-handle-embedded-and-linked-items"></a>Pro zpracování vložené a propojené položky  
  
1.  Odvození třídy z [COleClientItem](../mfc/reference/coleclientitem-class.md). Objekty této třídy představují položky, které součástí nebo k vaší OLE dokumentu.  
  
2.  Přepsání `OnChange`, `OnChangeItemPosition`, a `OnGetItemPosition`. Tyto funkce zpracovávat změny velikosti, umístění a úprava vložené a propojené položky.  
  
 Průvodce aplikace odvodí třídy pro vás, ale budete pravděpodobně muset přepsat `OnChange` a dalších funkcí uvedený s ním v kroku 2 v předchozím postupu. Kostru implementace nutné přizpůsobit pro většinu aplikací, protože tyto funkce jsou implementované jinak z jedné aplikace na další. Příklady tohoto najdete v tématu ukázky MFC [DRAWCLI](../visual-cpp-samples.md) a [KONTEJNERU](../visual-cpp-samples.md).  
  
 Počet položek, které je nutné přidat do kontejneru aplikace nabídky struktury pro podporu OLE. Další informace naleznete v tématu [nabídky a prostředky: kontejnerové doplňky](../mfc/menus-and-resources-container-additions.md).  
  
 Můžete také podporují některé z následujících funkcí v aplikaci kontejneru:  
  
-   Aktivace na místě při úpravě vložené položky.  
  
     Další informace najdete v tématu [aktivace](../mfc/activation-cpp.md).  
  
-   Vytvoření z OLE položky podle přetahování výběr ze serverové aplikace.  
  
     Další informace najdete v tématu [přetažení a Drop (OLE)](../mfc/drag-and-drop-ole.md).  
  
-   Odkazy na vložené objekty nebo kombinace kontejneru nebo serverové aplikace.  
  
     Další informace najdete v tématu [kontejnery: pokročilé funkce](../mfc/containers-advanced-features.md).  
  
## <a name="see-also"></a>Viz také  
 [Kontejnery](../mfc/containers.md)   
 [Kontejnery: Klientské položky](../mfc/containers-client-items.md)

