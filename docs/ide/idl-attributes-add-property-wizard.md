---
title: IDL – atributy, Průvodce přidáním vlastnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.idlattributes
dev_langs:
- C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7da654321dfae520f458374654a21a9e8ebb98f5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706646"
---
# <a name="idl-attributes-add-property-wizard"></a>IDL – atributy, Průvodce přidáním vlastnosti
Na této stránce Průvodce přidáním vlastnosti k určení nastavení jakékoli interface definition language (IDL) pro vlastnost.  
  
- **id**

   Nastaví číselné ID identifikující vlastnosti. Tato možnost není k dispozici pro vlastnosti vlastního rozhraní. Zobrazit [id](/windows/desktop/Midl/id) v *MIDL odkazu*.  
  
- **helpcontext**

   Určuje ID kontextu, který umožňuje uživateli zobrazit informace o této vlastnosti v souboru nápovědy. Zobrazit [helpcontext](/windows/desktop/Midl/helpcontext) v *MIDL odkazu*.  
  
- **helpstring**

   Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje. Ve výchozím nastavení, je nastavena "vlastnost *název vlastnosti*." Zobrazit [helpstring](/windows/desktop/Midl/helpstring) v *MIDL odkazu*.  
  
## <a name="other-options"></a>Další možnosti  

Některé možnosti jsou k dispozici pro všechny typy vlastností.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**bindable**|Označuje, že vlastnost podporuje datové vazby. Zobrazit [umožňujících vazbu](/windows/desktop/Midl/bindable) v *MIDL odkazu*. Pro implementaci vlastnosti tato možnost je ve výchozím nastavení a nejde změnit.|  
|**defaultbind**|Označuje, že vlastnost podporující vazby, jeden je nejlepší reprezentuje objekt. Zobrazit [defaultbind](/windows/desktop/Midl/defaultbind) v *MIDL odkazu*.|  
|**displaybind**|Indikuje, že tato vlastnost se má zobrazovat uživateli jako s možností vazby. Zobrazit [displaybind](/windows/desktop/Midl/displaybind) v *MIDL odkazu*.|  
|**immediatebind**|Označuje, že databázi budou okamžitě oznamovat všechny změny této vlastnosti objektu vázané na data. Zobrazit [immediatebind](/windows/desktop/Midl/immediatebind) v *MIDL odkazu*.|  
|**defaultcollelem**|Označuje, že je vlastnost přístupovou funkci pro prvek výchozí kolekce. Zobrazit [defaultcollelem](/windows/desktop/Midl/defaultcollelem) v *MIDL odkazu*.|  
|**nonbrowsable**|Značky na rozhraní nebo dispinterface člena, který nebude se zobrazovat v prohlížeči vlastností. Zobrazit [nonbrowsable](/windows/desktop/Midl/nonbrowsable) v *MIDL odkazu*.|  
|**requestedit**|Označuje, že vlastnost podporuje **OnRequestEdit** oznámení najdete v tématu [requestedit –](/windows/desktop/Midl/requestedit) v *MIDL odkazu*. Pro implementaci vlastnosti tato možnost je ve výchozím nastavení a nejde změnit.|  
|**Zdroj**|Označuje, že je člen vlastnost Zdroj událostí. Zobrazit [zdroj](/windows/desktop/Midl/source) v *MIDL odkazu*.|  
|**hidden**|Označuje, že vlastnost existuje, ale nebude se zobrazovat v prohlížeči uživatele. Zobrazit [skryté](/windows/desktop/Midl/hidden) v *MIDL odkazu*.|  
|**restricted**|Určuje, že vlastnost se nedá volat libovolně. Zobrazit [s omezeným přístupem](/windows/desktop/Midl/restricted) v *MIDL odkazu*.|  
|`local`|Určuje kompilátor MIDL o tom, že vlastnost není vzdálený. Zobrazit [místní](/windows/desktop/Midl/local) v *MIDL odkazu*.|  
  
## <a name="see-also"></a>Viz také  
 [Přidání vlastnosti](../ide/adding-a-property-visual-cpp.md)   
 [Názvy, Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md)   
 [Implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md)   
 [Uložené vlastnosti](../ide/stock-properties.md)