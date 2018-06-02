---
title: IDL – atributy, Průvodce přidáním metody | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.method.idlattrib
dev_langs:
- C++
helpviewer_keywords:
- Add Method Wizard [C++]
- IDL attributes, Add Method Wizard
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a7a1e8fe89f64ad5909e7c1415545e3b3d80196
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33337766"
---
# <a name="idl-attributes-add-method-wizard"></a>IDL – atributy, Průvodce přidáním metody
Tato stránka Průvodce přidáním metody použijte k určení nastavení rozhraní definice jazyka IDL () pro metodu.  
  
 **id**  
 Nastaví číselný Identifikátor, který identifikuje metodu. V tématu [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) v *MIDL odkazu*.  
  
 Toto políčko není dostupná pro vlastní rozhraní a není k dispozici pro odesílající MFC rozhraní.  
  
 **call_as**  
 Určuje název vzdálené metody, ke kterému se dá namapovat tato metoda místní. V tématu [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) v *MIDL odkazu*.  
  
 Není k dispozici pro odesílající MFC rozhraní.  
  
 **helpcontext**  
 Určuje Identifikátor kontext, který umožňuje uživateli zobrazit informace o této metodě v souboru nápovědy. V tématu [HelpContext –](http://msdn.microsoft.com/library/windows/desktop/aa366851) v *MIDL odkazu*.  
  
 Není k dispozici pro odesílající MFC rozhraní.  
  
 **helpstring**  
 Určuje řetězec znaků, který se používá k popisu elementu, na který se vztahuje. Ve výchozím nastavení je nastavena na "metoda *název metody*." V tématu [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) v *MIDL odkazu*.  
  
 Není k dispozici pro odesílající MFC rozhraní.  
  
 **Další atributy**  
 Není k dispozici pro odesílající MFC rozhraní.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**hidden**|Určuje, že metoda existuje, ale by se neměly zobrazovat v prohlížeči uživatele. V tématu [Skrytá](http://msdn.microsoft.com/library/windows/desktop/aa366861) v *MIDL odkazu*.|  
|**Zdroj**|Označuje, že je uživatel členem metodu zdroj událostí systému. V tématu [zdroj](http://msdn.microsoft.com/library/windows/desktop/aa367166) v *MIDL odkazu*.|  
|`local`|Kompilátoru MIDL Určuje, že metoda není vzdálená. V tématu [místní](http://msdn.microsoft.com/library/windows/desktop/aa367071) v *MIDL odkazu*.|  
|**restricted**|Určuje metodu nelze volat libovolně. V tématu [s omezeným přístupem](http://msdn.microsoft.com/library/windows/desktop/aa367157) v *MIDL odkazu*.|  
|**vararg**|Určuje, že metoda přijímá proměnný počet argumentů. K tomu, poslední argument musí být typu bezpečné pole **VARIANT** typ, který obsahuje všechny zbývající argumenty. V tématu [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304) v *MIDL odkazu*.|  
  
## <a name="see-also"></a>Viz také  
 [Přidání metody](../ide/adding-a-method-visual-cpp.md)   
 [Průvodce přidáním metody](../ide/add-method-wizard.md)