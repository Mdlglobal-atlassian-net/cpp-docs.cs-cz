---
title: 'Kontejnery: Oznámení klientských položek | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d76717e68e37769cf55dceb4492ed78031c49e10
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928221"
---
# <a name="containers-client-item-notifications"></a>Kontejnery: Oznámení klientských položek
Tento článek popisuje přepisovatelné funkce, které volá rozhraní MFC framework, pokud server aplikace upravovat položky v dokumentu klientské aplikace.  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md) definuje několik přepisovatelné funkce, které se nazývají v reakci na požadavky ze součásti aplikace, což se označuje taky jako serverové aplikace. Tyto k přepisovatelným obvykle fungují jako oznámení. Informují aplikace kontejneru různé události, jako je například posouvání, aktivaci nebo změně pozice a změny, které uživatel provede při úpravách nebo jinak manipulace s položky.  
  
 Rozhraní framework upozorní aplikace kontejneru změn prostřednictvím volání `COleClientItem::OnChange`, jejíž implementace je vyžadován přepisovatelné funkce. Tato funkce chráněné přijímá dva argumenty. Určuje první z důvodu, že server změněn položky:  
  
|Oznámení|Význam|  
|------------------|-------------|  
|**OLE_CHANGED**|Došlo ke změně vzhledu položky OLE.|  
|**OLE_SAVED**|Položka OLE se uložila.|  
|**OLE_CLOSED**|Položka OLE bylo ukončeno.|  
|**OLE_RENAMED**|Server dokument obsahující položky OLE byl přejmenován.|  
|**OLE_CHANGED_STATE**|Tato položka OLE změněna z jednoho stavu do jiného.|  
|**OLE_CHANGED_ASPECT**|Aspekt kreslení OLE položka byla změněna rozhraní.|  
  
 Tyto hodnoty jsou od **OLE_NOTIFICATION** výčtu, která je definována v AFXOLE. H.  
  
 Druhým argumentem této funkce určuje, jak se změnila položka nebo co stavu, že má zadali:  
  
|Po prvním argumentem|Druhý argument|  
|----------------------------|---------------------|  
|**OLE_SAVED** nebo **OLE_CLOSED**|Se nepoužívá.|  
|**OLE_CHANGED**|Určuje aspekt OLE položky, které se změnily.|  
|**OLE_CHANGED_STATE**|Popisuje stav, který vkládáte (*emptyState*, *loadedState*, *openState*, *activeState*, nebo  *activeUIState*).|  
  
 Další informace o stavy klientských položek můžete předpokládat, najdete v tématu [kontejnery: stavy klientských položek](../mfc/containers-client-item-states.md).  
  
 Volání framework `COleClientItem::OnGetItemPosition` při položku aktivování pro úpravy na místě. Implementace je vyžadována pro aplikace, které podporují úpravy na místě. Průvodce aplikací MFC poskytuje základní implementaci, která přiřadí souřadnice položky k `CRect` objekt, který se předá jako argument k `OnGetItemPosition`.  
  
 Pokud položku OLE pozici nebo velikost změní během úprav na místě, musí být aktualizované kontejneru informace o umístění a obdélníky výstřižek položky a server musí obdržet informace o změnách. Volání framework `COleClientItem::OnChangeItemPosition` pro tento účel. Průvodce aplikací MFC poskytuje přepsání, která volá funkce základní třídy. Upravíte funkce, která zapisuje Průvodce aplikací pro vaše `COleClientItem`-odvozené třídy tak, aby funkce aktualizuje všechny informace o zachována objektu klientských položek.  
  
## <a name="see-also"></a>Viz také  
 [Kontejnery](../mfc/containers.md)   
 [Kontejnery: Stavy klientských položek](../mfc/containers-client-item-states.md)   
 [COleClientItem::OnChangeItemPosition](../mfc/reference/coleclientitem-class.md#onchangeitemposition)

