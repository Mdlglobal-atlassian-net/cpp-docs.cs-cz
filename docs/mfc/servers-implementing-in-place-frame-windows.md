---
title: 'Servery: Implementace oken s rámečkem na místě | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc26e2874921d30ef233509ee46b776ec8e3e9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="servers-implementing-in-place-frame-windows"></a>Servery: Implementace oken s rámečkem na místě
Tento článek vysvětluje, co musíte udělat implementovat okna s rámečkem na místě v aplikaci visual úpravy serveru, pokud použijete Průvodce aplikace k vytvoření aplikace serveru. Místo podle pokynů uvedených v tomto článku, můžete použít existující třídy oken s rámečkem na místě z aplikace generované v Průvodci aplikace nebo ukázku součástí Visual C++.  
  
#### <a name="to-declare-an-in-place-frame-window-class"></a>Deklarovat třídu oken s rámečkem na místě  
  
1.  Odvození třídu oken s rámečkem na místě z `COleIPFrameWnd`.  
  
    -   Použití `DECLARE_DYNCREATE` makro v záhlaví souboru třídy.  
  
    -   Použití `IMPLEMENT_DYNCREATE` makro v souboru třída implementace (sada). To umožňuje objekty z této třídy lze vytvořit pomocí rozhraní.  
  
2.  Deklarace `COleResizeBar` člena třídy oken s rámečkem. To je nutné, pokud chcete, aby podporovalo změnu velikosti na místě v serverových aplikacích.  
  
     Deklarovat `OnCreate` obslužné rutiny zpráv (pomocí **vlastnosti** okno) a volání **vytvořit** pro vaše `COleResizeBar` člen, pokud jste ji definovali.  
  
3.  Pokud máte panel nástrojů, deklarovat `CToolBar` člena třídy oken s rámečkem.  
  
     Přepsání `OnCreateControlBars` členské funkce k vytvořit panel nástrojů, když je na místě aktivní server. Příklad:  
  
     [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]  
  
     Přečtěte si diskuzi o tento kód následující krok 5.  
  
4.  Zahrňte soubor hlaviček, pro tuto třídu oken s rámečkem na místě v hlavní soubor.  
  
5.  V `InitInstance` třídě aplikace, volání `SetServerInfo` funkce objektu šablony dokumentu k určení prostředků a oken s rámečkem na místě mají být použity v otevřené a místní úpravy.  
  
 Volání metod řadu funkce **Pokud** příkaz vytvoří panelu nástrojů z prostředků zadaný server. Panel nástrojů v tomto okamžiku je součástí hierarchie kontejneru okno. Protože tento panel nástrojů je odvozený od `CToolBar`, předat jeho zprávy jeho vlastníka aplikace typu kontejner oken s rámečkem, není-li změnit vlastníka. To je důvod, proč volání `SetOwner` je nezbytné. Toto volání se změní okno, kde příkazy jsou odesílány být oken s rámečkem na místě serveru, způsobuje zprávy, které mají být předána na server. To umožňuje serveru reagování na operací na panelu nástrojů, který poskytuje.  
  
 ID pro rastrového obrázku panelu nástrojů musí být stejná jako ostatní prostředky v místě definované v aplikaci server. V tématu [nabídky a prostředky: serverové doplňky](../mfc/menus-and-resources-server-additions.md) podrobnosti.  
  
 Další informace najdete v tématu [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [COleResizeBar](../mfc/reference/coleresizebar-class.md), a [CDocTemplate::SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) v *knihovny tříd*.  
  
## <a name="see-also"></a>Viz také  
 [Servery](../mfc/servers.md)   
 [Servery: Implementace serveru](../mfc/servers-implementing-a-server.md)   
 [Servery: Implementace dokumentů serveru](../mfc/servers-implementing-server-documents.md)   
 [Servery: Serverové položky](../mfc/servers-server-items.md)

