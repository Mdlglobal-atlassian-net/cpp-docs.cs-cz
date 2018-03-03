---
title: "Přehled ovládacích prvků pro úpravy s formátováním | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bffab7b72e99dc6587f1d2cbff84407949dd374b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-the-rich-edit-control"></a>Přehled ovládacích prvků pro úpravy s formátováním
> [!IMPORTANT]
>  Pokud používáte ovládacího prvku RichEdit v dialogovém okně (bez ohledu na to, jestli je vaše aplikace SDI, MDI, nebo na základě dialogové okno), musí volat [afxinitrichedit –](../mfc/reference/application-information-and-management.md#afxinitrichedit) po před dialogové okno se zobrazí pole. Je typické pro volání této funkce se ve vašem programu `InitInstance` – členská funkce. Není nutné volat pokaždé, když je zobrazit dialogové okno, pouze při prvním spuštění. Není nutné volat `AfxInitRichEdit` při práci s `CRichEditView`.  
  
 Ovládací prvky Rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) nabízí programovací rozhraní pro formátování textu. Aplikace musí implementovat však potřeba zpřístupnit operací formátování uživateli žádné uživatelské rozhraní komponenty. To znamená bohaté upravit podporuje ovládací prvek změna atributů znak nebo odstavce vybraného textu. Některé příklady znaku, který atributy jsou tučné, kurzíva, rodinu písem a velikost bodu. Příklady atributy odstavce: zarovnání, okraje a zarážek tabulátoru. Je však až poskytovat uživatelské rozhraní, jestli který tlačítka panelu nástrojů, položky nabídky nebo dialogové okno znak formátu. Existují také funkce dotazování ovládacího prvku RichEdit pro atributy aktuální výběr. Pomocí těchto funkcí zobrazte aktuální nastavení pro atributy, například nastavení zaškrtnutí na příkaz uživatelského rozhraní, pokud výběru formátování atribut tučné znaků.  
  
 Další informace o znak a formátování odstavce, najdete v části [formátování znaků](../mfc/character-formatting-in-rich-edit-controls.md) a [formátování odstavce](../mfc/paragraph-formatting-in-rich-edit-controls.md) dál v tomto tématu.  
  
 Bohaté upravit ovládací prvky podporu téměř všechny operace a zprávy s oznámením použít s ovládacími prvky pro úpravy víceřádkový. Ovládací prvky úprav proto, že již ovládacích prvcích pro úpravy použití lze snadno změnit používat bohaté aplikace. Další zprávy a oznámení umožňují aplikacím přístup k funkci jedinečné pro bohaté ovládací prvky. Informace o ovládacích prvcích pro úpravy najdete v tématu [CEdit](../mfc/reference/cedit-class.md).  
  
 Další informace o oznámeních najdete v tématu [oznámení z ovládacího prvku upravit bohaté](../mfc/notifications-from-a-rich-edit-control.md) dál v tomto tématu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

