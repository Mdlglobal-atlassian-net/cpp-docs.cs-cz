---
title: Průvodce implementací rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.impl.interface.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Interface Wizard [C++]
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf2ddf83b7a03f8d4e01b61f82e46e0d26a5547b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33340538"
---
# <a name="implement-interface-wizard"></a>Průvodce implementací rozhraní
Tento průvodce implementuje rozhraní pro objekt COM. Implementace mnoho rozhraní jsou součástí knihovny COM, která je k dispozici v sadě Visual Studio a Windows. Implementace rozhraní je přidružená objektu, když je vytvořena instance tohoto objektu, a poskytuje služby, které nabízí objekt.  
  
 Informace o rozhraní a implementace, najdete v části [rozhraní a implementace rozhraní](http://msdn.microsoft.com/library/windows/desktop/ms694356) ve Windows SDK.  
  
 **Implementace rozhraní**  
 Určuje umístění knihovny typů, ze kterého je vytvořen rozhraní.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Projekt**|Knihovny typů je součástí projektu.|  
|**Registru**|Knihovny typů je zaregistrován v systému. Registrovaného typu knihovny jsou uvedeny v **dostupné knihovny typů**.|  
|**Soubor**|Knihovny typů není nutně zaregistrována v systému, ale je obsažený v souboru. Je nutné zadat umístění souboru v **umístění**.|  
  
 **Dostupné knihovny typů**  
 Zobrazí dostupné knihovny typů obsahující definice rozhraní, které můžete implementovat. Pokud kliknete na tlačítko **soubor** pod **implementovat rozhraní z**, toto políčko není možné měnit.  
  
 **Poloha**  
 Zobrazí umístění knihovny typů v aktuálně vybranou **dostupné knihovny typů** seznamu. Pokud jste vybrali **soubor** pod **implementovat rozhraní z**, klikněte na tlačítko se třemi tečkami vyhledat soubor obsahující typ knihovnu, která má použít.  
  
 **Rozhraní**  
 Zobrazí rozhraní, jejichž definice jsou obsaženy v aktuálně vybrané v knihovně typů **dostupné knihovny typů** pole.  
  
> [!NOTE]
>  Rozhraní, které mají stejný název jako již implementované vybraný objekt nejsou zobrazeny v **rozhraní** pole.  
  
|Tlačítko přenosu|Popis|  
|---------------------|-----------------|  
|**>**|Přidá **implementovat rozhraní** název rozhraní aktuálně vybraného v seznamu **rozhraní** seznamu.|  
|**>>**|Přidá **implementovat rozhraní** názvy všech rozhraní k dispozici v seznamu **rozhraní** seznamu.|  
|**<**|Odebere aktuálně vybraný v název rozhraní **implementovat rozhraní** seznamu.|  
|**<\<**|Odebere všechny názvy rozhraní **implementovat rozhraní** seznamu.|  
  
 **Implementace rozhraní**  
 Zobrazuje názvy rozhraní, které jste vybrali k implementaci v objektu.  
  
> [!NOTE]
>  Pokud zahrnete více než jedno rozhraní, která je odvozena z `IDispatch`, nebo pokud chcete implementovat rozhraní, které je odvozený od jiného rozhraní již na vaší třídě, pak musíte odstranit nejednoznačnost položek COM_MAP. V tématu [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md)