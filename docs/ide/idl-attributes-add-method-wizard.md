---
title: "IDL – atributy, Průvodce přidáním metody | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.method.idlattrib
dev_langs: C++
helpviewer_keywords:
- Add Method Wizard [C++]
- IDL attributes, Add Method Wizard
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 583b2c0ec67c4799753fe52d74131e7238b11d46
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="idl-attributes-add-method-wizard"></a>IDL – atributy, Průvodce přidáním metody
Tato stránka Průvodce přidáním metody použijte k určení nastavení rozhraní definice jazyka IDL () pro metodu.  
  
 **ID**  
 Nastaví číselný Identifikátor, který identifikuje metodu. V tématu [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) v *MIDL odkazu*.  
  
 Toto políčko není dostupná pro vlastní rozhraní a není k dispozici pro odesílající MFC rozhraní.  
  
 **call_as –**  
 Určuje název vzdálené metody, ke kterému se dá namapovat tato metoda místní. V tématu [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) v *MIDL odkazu*.  
  
 Není k dispozici pro odesílající MFC rozhraní.  
  
 **HelpContext –**  
 Určuje Identifikátor kontext, který umožňuje uživateli zobrazit informace o této metodě v souboru nápovědy. V tématu [HelpContext –](http://msdn.microsoft.com/library/windows/desktop/aa366851) v *MIDL odkazu*.  
  
 Není k dispozici pro odesílající MFC rozhraní.  
  
 **helpstring –**  
 Určuje řetězec znaků, který se používá k popisu elementu, na který se vztahuje. Ve výchozím nastavení je nastavena na "metoda *název metody*." V tématu [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) v *MIDL odkazu*.  
  
 Není k dispozici pro odesílající MFC rozhraní.  
  
 **Další atributy**  
 Není k dispozici pro odesílající MFC rozhraní.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**skryté**|Určuje, že metoda existuje, ale by se neměly zobrazovat v prohlížeči uživatele. V tématu [Skrytá](http://msdn.microsoft.com/library/windows/desktop/aa366861) v *MIDL odkazu*.|  
|**zdroj**|Označuje, že je uživatel členem metodu zdroj událostí systému. V tématu [zdroj](http://msdn.microsoft.com/library/windows/desktop/aa367166) v *MIDL odkazu*.|  
|`local`|Kompilátoru MIDL Určuje, že metoda není vzdálená. V tématu [místní](http://msdn.microsoft.com/library/windows/desktop/aa367071) v *MIDL odkazu*.|  
|**omezený**|Určuje metodu nelze volat libovolně. V tématu [s omezeným přístupem](http://msdn.microsoft.com/library/windows/desktop/aa367157) v *MIDL odkazu*.|  
|**vararg**|Určuje, že metoda přijímá proměnný počet argumentů. K tomu, poslední argument musí být typu bezpečné pole **VARIANT** typ, který obsahuje všechny zbývající argumenty. V tématu [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304) v *MIDL odkazu*.|  
  
## <a name="see-also"></a>Viz také  
 [Přidání metody](../ide/adding-a-method-visual-cpp.md)   
 [Průvodce přidáním metody](../ide/add-method-wizard.md)