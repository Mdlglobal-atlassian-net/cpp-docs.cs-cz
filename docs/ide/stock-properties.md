---
title: Stock vlastnosti | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- stock properties, about stock properties
- stock properties
ms.assetid: a89fc454-0b8e-447a-9033-4c8af46a24d9
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9bbc721669d51860c01c760a8d1f9fb899e019e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="stock-properties"></a>Uložené vlastnosti
Pokud přidáváte vlastnost dispinterface MFC pomocí [Průvodce přidáním vlastnosti](../ide/idl-attributes-add-property-wizard.md), můžete uložených vlastností z **název vlastnosti** v seznamu [názvy](../ide/names-add-property-wizard.md) stránky Průvodce. Tyto vlastnosti jsou následující:  
  
|Název vlastnosti|Popis|  
|-------------------|-----------------|  
|**Vzhled**|Vrací nebo nastavuje hodnotu, která určuje vzhled ovládacího prvku. Ovládacího prvku **vzhled** vlastnosti můžete zahrnout nebo vypustit efekty trojrozměrné zobrazení. Jde o vlastnost vedlejším pro čtení a zápis.|  
|`BackColor`|Vrací nebo nastavuje ovládacího prvku vedlejším `BackColor` vlastnost palety barev (RGB) nebo barvu předdefinovaného systému. Ve výchozím nastavení jeho hodnota odpovídá barvu popředí kontejneru ovládacího prvku. Jde o vlastnost vedlejším pro čtení a zápis.|  
|`BorderStyle`|Vrátí nebo nastaví styl ohraničení ovládacího prvku. Toto je vlastnost pro čtení a zápis.|  
|**Popisek**|Vrací nebo nastavuje ovládacího prvku **popisek** vlastnost. Popisek je název okna. **Popisek** neobsahuje žádné **členské proměnné** typ implementace.|  
|**Povoleno**|Vrací nebo nastavuje ovládacího prvku **povoleno** vlastnost. Ovládací prvek povoleno může reagovat na uživatelem generovaný události.|  
|**Písma**|Vrátí nebo nastaví písmo ovládacího prvku. Hodnota Null, pokud ovládací prvek nemá žádné písmo.|  
|`ForeColor`|Vrací nebo nastavuje ovládacího prvku vedlejším `ForeColor` vlastnost.|  
|**hWnd**|Vrací nebo nastavuje ovládacího prvku **hWnd** vlastnost. **hWnd** neobsahuje žádné **členské proměnné** typ implementace.|  
|**ReadyState**|Vrací nebo nastavuje ovládacího prvku **ReadyState** vlastnost. Ovládací prvek může být neinicializovaný, inicializovaný, načítání, interaktivní nebo dokončení. V tématu [READYSTATE](https://msdn.microsoft.com/en-us/library/aa768362.aspx) v *Internet SDK* Další informace.|  
|**Text**|Vrátí nebo nastaví text, obsažené v ovládacím prvku. **Text** neobsahuje žádné **členské proměnné** typ implementace.|  
  
## <a name="see-also"></a>Viz také  
 [Přidání vlastnosti](../ide/adding-a-property-visual-cpp.md)   
 [IDL – atributy, Průvodce přidáním vlastnosti](../ide/idl-attributes-add-property-wizard.md)