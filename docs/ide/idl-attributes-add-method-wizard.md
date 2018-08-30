---
title: IDL – atributy, Průvodce přidáním metody | Dokumentace Microsoftu
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
ms.openlocfilehash: 2c7f7784e57f0dc66b6a4c77565016d17420eb55
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219119"
---
# <a name="idl-attributes-add-method-wizard"></a>IDL – atributy, Průvodce přidáním metody
Na této stránce Průvodce přidáním metody k určení nastavení jakékoli interface definition language (IDL) pro metodu.  
  
 **id**  
 Nastaví číselný Identifikátor, který identifikuje metodu. Zobrazit [id](/windows/desktop/Midl/id) v *MIDL odkazu*.  
  
 Toto pole není k dispozici pro vlastní rozhraní a není k dispozici pro odesílající rozhraní knihovny MFC.  
  
 **call_as**  
 Určuje název vzdálené metody, do které je možné mapovat tato metoda místní. Zobrazit [call_as](/windows/desktop/Midl/call-as) v *MIDL odkazu*.  
  
 Není k dispozici pro odesílající rozhraní knihovny MFC.  
  
 **helpcontext**  
 Určuje ID kontextu, který umožňuje uživateli zobrazit informace o této metodě v souboru nápovědy. Zobrazit [helpcontext](/windows/desktop/Midl/helpcontext) v *MIDL odkazu*.  
  
 Není k dispozici pro odesílající rozhraní knihovny MFC.  
  
 **helpstring**  
 Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje. Ve výchozím nastavení, je nastavena "metoda *název metody*." Zobrazit [helpstring](/windows/desktop/Midl/helpstring) v *MIDL odkazu*.  
  
 Není k dispozici pro odesílající rozhraní knihovny MFC.  
  
 **Další atributy**  
 Není k dispozici pro odesílající rozhraní knihovny MFC.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**hidden**|Označuje, jestli metoda existuje, ale nebude se zobrazovat v prohlížeči uživatele. Zobrazit [skryté](/windows/desktop/Midl/hidden) v *MIDL odkazu*.|  
|**Zdroj**|Označuje, že člen metoda je zdrojem událostí. Zobrazit [zdroj](/windows/desktop/Midl/source) v *MIDL odkazu*.|  
|`local`|Určuje kompilátor MIDL o tom, že metoda není vzdálený. Zobrazit [místní](/windows/desktop/Midl/local) v *MIDL odkazu*.|  
|**restricted**|Určuje metodu nejde volat libovolně. Zobrazit [s omezeným přístupem](/windows/desktop/Midl/restricted) v *MIDL odkazu*.|  
|**vararg**|Určuje, že tato metoda přebírá proměnný počet argumentů. Jak toho dosáhnout, musí být posledním argumentem bezpečné pole **VARIANT** typ, který obsahuje všechny zbývající argumenty. Zobrazit [vararg](/windows/desktop/Midl/vararg) v *MIDL odkazu*.|  
  
## <a name="see-also"></a>Viz také  
 [Přidání metody](../ide/adding-a-method-visual-cpp.md)   
 [Průvodce přidáním metody](../ide/add-method-wizard.md)