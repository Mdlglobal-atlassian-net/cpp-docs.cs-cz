---
title: 'Servery: Implementace Windows rámečkem na místě'
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
ms.openlocfilehash: 887de747ced25d427b82e528a3b85634fabff4d9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278987"
---
# <a name="servers-implementing-in-place-frame-windows"></a>Servery: Implementace Windows rámečkem na místě

Tento článek vysvětluje, co musíte udělat, abyste implementace oken s rámečkem na místě v vizuální úpravy serverové aplikace, pokud použijete Průvodce aplikací nejsou k vytvoření serverové aplikace. Místo podle postupu uvedeného v tomto článku, můžete použít existující třídy oken s rámečkem na místě z aplikace vygenerované průvodcem aplikací nebo ukázku v jazyce Visual C++ k dispozici.

#### <a name="to-declare-an-in-place-frame-window-class"></a>Chcete-li deklarovat třídu oken s rámečkem na místě

1. Odvodit třídu oken s rámečkem na místě ze `COleIPFrameWnd`.

   - DECLARE_DYNCREATE – makro Použíjte v záhlaví souboru třídy.

   - Použijte IMPLEMENT_DYNCREATE – makro v souboru implementace (.cpp) třídy. Objekty této třídy, který se má vytvořit v rámci rozhraní díky tomu.

1. Deklarace `COleResizeBar` člen třídy oken s rámečkem. To je potřeba, pokud chcete, aby podporovalo změnu velikosti na místě v serverových aplikacích.

   Deklarovat `OnCreate` obslužná rutina zprávy (pomocí **vlastnosti** okno) a volat `Create` pro vaše `COleResizeBar` člen, pokud jste ji definovali.

1. Pokud máte panel nástrojů, deklarujte `CToolBar` člen třídy oken s rámečkem.

   Přepsat `OnCreateControlBars` členská funkce k vytvoření panelu nástrojů, když je na místě aktivní server. Příklad:

   [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]

   Přečtěte si diskuzi o tento kód po kroku 5.

1. Zahrňte soubor hlaviček pro této třídy oken s rámečkem na místě hlavní soubor.

1. V `InitInstance` třídě aplikace, zavolejte `SetServerInfo` funkce objektu šablony dokumentu k určení prostředků a v místní okno rámce pro použití v otevřené a místní úpravy.

Řadu funkce volání **Pokud** příkaz vytvoří panel nástrojů z prostředků serveru k dispozici. Panel nástrojů v tomto okamžiku je součástí hierarchie okno kontejneru. Protože tento panel nástrojů je odvozený z `CToolBar`, předat své zprávy na jeho vlastníka, okno rámce aplikace kontejneru, není-li změnit vlastníka. To je důvod, proč volání `SetOwner` je nezbytné. Toto volání se změní v okně, kde příkazy jsou odesílány být okno rámečkem na místě serveru, což způsobí zprávy, které mají být předána serveru. To umožňuje, aby react pro operace na panelu nástrojů, které poskytuje server.

Identifikátor rastrového obrázku panelu nástrojů by měla být stejná jako ostatní prostředky v místě definované v serveru aplikaci. Zobrazit [nabídky a prostředky: Serverové doplňky](../mfc/menus-and-resources-server-additions.md) podrobnosti.

Další informace najdete v tématu [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [coleresizebar –](../mfc/reference/coleresizebar-class.md), a [CDocTemplate::SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) v *odkazy na knihovnu tříd*.

## <a name="see-also"></a>Viz také:

[Servery](../mfc/servers.md)<br/>
[Servery: Implementace serveru](../mfc/servers-implementing-a-server.md)<br/>
[Servery: Implementace dokumentů serveru](../mfc/servers-implementing-server-documents.md)<br/>
[Servery: Serverové položky](../mfc/servers-server-items.md)
