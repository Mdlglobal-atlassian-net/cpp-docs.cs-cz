---
title: "Přidání body připojení k objektu | Microsoft Docs"
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
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f63ec5bd9029302192e640e42a3d012df347219d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-connection-points-to-an-object"></a>Přidání body připojení k objektu
[ATL – tutoriál](../atl/active-template-library-atl-tutorial.md) ukazuje postup vytvoření ovládacího prvku s podporou pro spojovací body, přidat události a implementovat spojovacího bodu. ATL implementuje spojovací body se [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) třídy.  
  
 Pokud chcete implementovat spojovací bod, máte dvě možnosti:  
  
-   Implementujte vlastní odchozí zdroj události přidáním bod připojení ovládací prvek nebo objekt.  
  
-   Znovu použít bod připojení rozhraní definované v jiné knihovny typů.  
  
 V obou případech používá Průvodce implementací bodu připojení knihovny typů ke své práci.  
  
### <a name="to-add-a-connection-point-to-a-control-or-object"></a>Chcete-li přidat bod připojení na ovládací prvek nebo objekt  
  
1.  Definování dispinterface v bloku knihovny .idl souboru. Pokud jste povolili podporu pro spojovací body, když jste vytvořili ovládacího prvku pomocí Průvodce ovládacím prvkem ATL, bude dispinterface již vytvořen. Pokud jste nepovolili podporu pro spojovací body při vytvoření ovládacího prvku, je třeba ručně přidat dispinterface do souboru IDL. Následuje příklad odesílajícím rozhraním. Odchozí rozhraní nejsou nemusí být odesílání rozhraní ale skriptování například VBScript a JScript WDS, takže tento příklad používá dva odesílající rozhraní:  
  
     [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]  
  
     Pomocí nástroje buď uuidgen.exe nebo guidgen.exe generovat identifikátor GUID.  
  
2.  Přidat dispinterface jako `[default,source]` rozhraní v třída typu coclass pro objekt v souboru projektu. Znovu, pokud jste povolili podporu pro spojovací body při vytvoření ovládacího prvku, Průvodce ovládacím prvkem ATL se vytvoří `[default,source`] položku. Ruční přidání této položky, přidejte řádek tučným písmem:  
  
     [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]  
  
     Naleznete v souboru .idl v [str](../visual-cpp-samples.md) ATL ukázka příkladu.  
  
3.  Pomocí zobrazení tříd přidejte metody a vlastnosti události rozhraní. Klikněte pravým tlačítkem na třídu v zobrazení tříd, přejděte na **přidat** na místní nabídky a klikněte na **přidat bod připojení**.  
  
4.  V **zdroje rozhraní** pole se seznamem z Průvodce implementací bodu připojení, vyberte **rozhraní projektu**. Pokud zvolíte rozhraní pro řízení a stiskněte klávesu **OK**, které budete:  
  
    -   Generovat soubor hlaviček pomocí třídy proxy událostí, který implementuje kód, který bude provádět odchozí volání pro událost.  
  
    -   Přidejte záznam do bodu mapy připojení.  
  
     Zobrazí se také seznam všech knihoven typů ve vašem počítači. Byste měli používat jenom jednu z těchto knihoven typů k definování spojovací bod, pokud chcete implementovat přesný stejné odchozí rozhraní v jiné knihovny typů nalezena.  
  
### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>Chcete-li znovu použít rozhraní bodu připojení definované v jiné knihovny typů  
  
1.  V zobrazení tříd, klikněte pravým tlačítkem na třídu, která implementuje **BEGIN_COM_MAP** makro, přejděte na příkaz **přidat** na místní nabídky a klikněte na **přidat bod připojení**.  
  
2.  V průvodce implementací bodu připojení vyberte knihovny typů a rozhraní v knihovně typů a klikněte na tlačítko **přidat**.  
  
3.  Upravte soubor .idl buď:  
  
    -   Zkopírujte dispinterface ze souboru .idl pro objekt, jehož zdroj události se používá.  
  
    -   Použití **importlib –** instrukcí na této knihovny typů.  
  
## <a name="see-also"></a>Viz také  
 [Spojovací bod](../atl/atl-connection-points.md)

