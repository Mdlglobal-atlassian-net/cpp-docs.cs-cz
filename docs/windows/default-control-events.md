---
title: "Výchozí události ovládacích prvků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Dialog editor, default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls, events
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a8f85e534892cf45987cf563f968ca5e1ec28262
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="default-control-events"></a>Výchozí události ovládacích prvků
Následující názvy ovládacích prvků mají doprovodné výchozí události:  
  
|Název ovládacího prvku|Výchozí události|  
|------------------|-------------------|  
|Animace|**ACN_START**|  
|Zaškrtávací políčko|**BN_CLICKED**|  
|Pole se seznamem|**CBN_SELCHANGE**|  
|Vlastní|**TTN_GETDISPINFO**|  
|Výběr data a času|**DTN_DATETIMECHANGE –**|  
|Textové pole|**EN_CHANGE**|  
|Skupinový rámeček|(Není k dispozici)|  
|Klávesové zkratky|**NM_OUTOFMEMORY –**|  
|IP adresa|**IPN_FIELDCHANGED**|  
|Seznam|**LVN_ITEMCHANGE**|  
|Pole se seznamem|**LBN_SELCHANGE**|  
|Měsíční kalendář|**MCN_SELCHANGE**|  
|Obrázek ovládacího prvku|(Není k dispozici)|  
|Průběh|**NM_CUSTOMDRAW**|  
|Tlačítko|**BN_CLICKED**|  
|Přepínač|**BN_CLICKED**|  
|Pro úpravy s formátováním|**EN_CHANGE**|  
|Posuvník|**NM_THEMECHANGED**|  
|Posuvník|**NM_CUSTOMDRAW**|  
|Typu číselník|**UDN_DELTAPOS**|  
|Statický Text|(Není k dispozici)|  
|Tabulátor|**TCN_SELCHANGE**|  
|Strom|**TVN_SELCHANGE**|  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Definování členských proměnných pro ovládací prvky dialogového okna](../windows/defining-member-variables-for-dialog-controls.md)   
 [Typy zpráv přidružených objektů uživatelského rozhraní](../mfc/reference/message-types-associated-with-user-interface-objects.md)   
 [Úpravy obslužné rutiny zpráv](../mfc/reference/editing-a-message-handler.md)   
 [Definování obslužné rutiny zpráv pro zrcadlené zprávy](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)   
 [Deklarace proměnné založené na nové třídě ovládacího prvku](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)   
 [Přepisování virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)

