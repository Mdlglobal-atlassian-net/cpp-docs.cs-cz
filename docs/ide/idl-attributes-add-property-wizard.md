---
title: "IDL – atributy, Průvodce přidáním vlastnosti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.prop.idlattributes
dev_langs:
- C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec158c117161c5a5c2ffd23cef0d5c79c312ae7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="idl-attributes-add-property-wizard"></a>IDL – atributy, Průvodce přidáním vlastnosti
Na této stránce Průvodce přidáním vlastnosti k určení nastavení rozhraní definice jazyka IDL () pro vlastnost.  
  
 **id**  
 Nastaví číselný Identifikátor, který identifikuje vlastnost. Tato možnost není k dispozici pro vlastnosti vlastního rozhraní. V tématu [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) v *MIDL odkazu*.  
  
 **helpcontext**  
 Určuje Identifikátor kontext, který umožňuje uživateli zobrazit informace o této vlastnosti v souboru nápovědy. V tématu [HelpContext –](http://msdn.microsoft.com/library/windows/desktop/aa366851) v *MIDL odkazu*.  
  
 **helpstring**  
 Určuje řetězec znaků, který se používá k popisu elementu, na který se vztahuje. Ve výchozím nastavení je nastavena na "vlastnost *název vlastnosti*." V tématu [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) v *MIDL odkazu*.  
  
## <a name="other-options"></a>Další možnosti  
 Ne všechny možnosti jsou k dispozici pro všechny typy vlastností.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**bindable**|Označuje, že vlastnost podporuje datovou vazbu. V tématu [vazbu](http://msdn.microsoft.com/library/windows/desktop/aa366738) v *MIDL odkazu*. Pro implementaci vlastnosti tato možnost je ve výchozím nastavení a neměnný.|  
|**defaultbind**|Označuje, že jeden, vazbu vlastnost nejlepší reprezentuje objekt. V tématu [defaultbind –](http://msdn.microsoft.com/library/windows/desktop/aa366790) v *MIDL odkazu*.|  
|**displaybind**|Označuje, že tato vlastnost by měla být zobrazena uživateli jako vazbu. V tématu [displaybind](http://msdn.microsoft.com/library/windows/desktop/aa366804) v *MIDL odkazu*.|  
|**immediatebind**|Označuje, že databáze bude okamžitě informováni o všechny změny na tuto vlastnost objektu vázané na data. V tématu [immediatebind](http://msdn.microsoft.com/library/windows/desktop/aa367045) v *MIDL odkazu*.|  
|**defaultcollelem**|Určuje, zda je vlastnost funkce přistupujícího objektu pro element výchozí kolekci. V tématu [defaultcollelem](http://msdn.microsoft.com/library/windows/desktop/aa366792) v *MIDL odkazu*.|  
|**nonbrowsable**|Značky člena rozhraní a odesílající rozhraní, které by se neměly zobrazovat v prohlížeči vlastnosti. V tématu [nonbrowsable](http://msdn.microsoft.com/library/windows/desktop/aa367117) v *MIDL odkazu*.|  
|**requestedit**|Označuje, že vlastnost podporuje **OnRequestEdit, viz** oznámení najdete [requestedit –](http://msdn.microsoft.com/library/windows/desktop/aa367155) v *MIDL odkazu*. Pro implementaci vlastnosti tato možnost je ve výchozím nastavení a neměnný.|  
|**zdroj**|Označuje, že je uživatel členem vlastnost Zdroj událostí systému. V tématu [zdroj](http://msdn.microsoft.com/library/windows/desktop/aa367166) v *MIDL odkazu*.|  
|**hidden**|Určuje, že vlastnost existuje, ale by se neměly zobrazovat v prohlížeči uživatele. V tématu [Skrytá](http://msdn.microsoft.com/library/windows/desktop/aa366861) v *MIDL odkazu*.|  
|**restricted**|Určuje, že vlastnost nelze volat libovolně. V tématu [s omezeným přístupem](http://msdn.microsoft.com/library/windows/desktop/aa367157) v *MIDL odkazu*.|  
|`local`|MIDL kompilátoru Určuje, že vlastnost není vzdálená. V tématu [místní](http://msdn.microsoft.com/library/windows/desktop/aa367071) v *MIDL odkazu*.|  
  
## <a name="see-also"></a>Viz také  
 [Přidání vlastnosti](../ide/adding-a-property-visual-cpp.md)   
 [Názvy, Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md)   
 [Implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md)   
 [Uložené vlastnosti](../ide/stock-properties.md)