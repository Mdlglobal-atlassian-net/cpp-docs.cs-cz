---
title: 'Kontejnery: Oznámení klientských položek'
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: b59ba84c27d9ed4c964bd308cf69f9f729eb3c39
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528892"
---
# <a name="containers-client-item-notifications"></a>Kontejnery: Oznámení klientských položek

Tento článek popisuje přepisovatelné funkce, které rozhraní MFC volá, když aplikace serveru upravit položky v dokumentu klientské aplikace.

[COleClientItem](../mfc/reference/coleclientitem-class.md) definuje několik přepisovatelné funkce, které jsou volány v reakci na žádosti z komponenty aplikace, což se označuje taky jako serverové aplikace. Tyto k přepisovatelným obvykle fungují jako oznámení. Informují aplikace typu kontejner různé události, jako je například posouvání, aktivace nebo změna pozice a změn, které uživatel provede při úpravách nebo jinak manipulace s položky.

Rozhraní framework oznámí svou aplikaci typu kontejner změn přímo pomocí volání `COleClientItem::OnChange`, přepisovatelné funkce, jejichž implementace se vyžaduje. Tato funkce chráněné přijímá dva argumenty. Určuje první důvodem že ke změně serveru položky:

|Oznámení|Význam|
|------------------|-------------|
|**OLE_CHANGED**|Vzhled položky OLE se změnila.|
|**OLE_SAVED**|Položky OLE se uložil.|
|**OLE_CLOSED**|Položky OLE se zavřel.|
|**OLE_RENAMED**|Server dokument obsahující položky OLE se přejmenoval.|
|**OLE_CHANGED_STATE**|Položky OLE se změnil z jednoho stavu do druhého.|
|**OLE_CHANGED_ASPECT**|Aspekt příkazu pro vykreslení položky OLE se změnil v rámci rozhraní.|

Tyto hodnoty jsou od **OLE_NOTIFICATION** výčet, který je definován v AFXOLE. H.

Druhý argument pro tuto funkci určuje, jak položka se změnila nebo stavu, přechodu:

|Pokud je první argument|Druhý argument|
|----------------------------|---------------------|
|**OLE_SAVED** nebo **OLE_CLOSED**|Se nepoužívá.|
|**OLE_CHANGED**|Určuje aspekt položky OLE, které se změnily.|
|**OLE_CHANGED_STATE**|Popisuje stav zadání (*emptyState*, *loadedState*, *openState*, *activeState*, nebo  *activeUIState*).|

Další informace o stavech klientské položky, můžete předpokládat, naleznete v tématu [kontejnery: stavy klientských položek](../mfc/containers-client-item-states.md).

Rámec volá `COleClientItem::OnGetItemPosition` když se položka aktivuje pro místní úpravy. Implementace je vyžadována pro aplikace, které podporují místní úpravy. Průvodce aplikací MFC poskytuje základní implementaci, která přiřadí položky souřadnice, kde `CRect` objekt, který je předán jako argument `OnGetItemPosition`.

Pokud během místní úpravy se změní umístění a velikost položky OLE, musí být aktualizováno kontejneru informace o umístění a obdélníky výstřižek položky a server musí přijímat informace o změnách. Rámec volá `COleClientItem::OnChangeItemPosition` pro tento účel. Průvodce aplikací MFC poskytuje přepsání, která volá funkci základní třídy. Byste měli upravovat funkce, která zapisuje Průvodce aplikace pro vaše `COleClientItem`-odvozené třídy tak, aby funkce aktualizuje všechny informace, které uchovávají objektem klientských položek.

## <a name="see-also"></a>Viz také

[Kontejnery](../mfc/containers.md)<br/>
[Kontejnery: Stavy klientských položek](../mfc/containers-client-item-states.md)<br/>
[COleClientItem::OnChangeItemPosition](../mfc/reference/coleclientitem-class.md#onchangeitemposition)

