---
title: "Implementace bodu připojení (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2e377b3945f85d1c5759344992046e9fafb16103
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-a-connection-point-visual-c"></a>Implementace bodu připojení (Visual C++)
Implementace bodu připojení pomocí Průvodce bodu připojení implementovat, musí jste vytvořili projekt jako aplikace ATL COM nebo jako aplikace knihovny MFC, který obsahuje podpory knihovny ATL. Můžete použít [ATL – Průvodce projektem](../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt knihovny ATL do aplikace knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) implementovat ATL – podpora pro aplikace MFC.  
  
> [!NOTE]
>  Informace o implementaci bodu připojení pro projekt knihovny MFC najdete v tématu [spojovací body](../mfc/connection-points.md).  
  
 Po vytvoření projektu, k implementaci bod připojení je nejprve nutno přidat objekt knihovny ATL. V tématu [přidávání objektů a ovládacích prvků do projektu knihovny ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) seznam průvodců, které přidat objekty do projektu knihovny ATL.  
  
> [!NOTE]
>  Průvodce nepodporuje dialogy knihovny ATL, webové služby XML vytvořené pomocí serveru ATL, objekty výkonu a čítače výkonu.  
  
 Objekt umožňující připojení (tedy zdroje) můžete vystavit bod připojení pro každou z odchozí rozhraní. Každý odchozí rozhraní může být implementováno klientem objektu (tj. jímka). Další informace najdete v tématu [ATL – body připojení](../atl/atl-connection-points.md).  
  
### <a name="to-implement-a-connection-point"></a>Implementace bodu připojení  
  
1.  V zobrazení tříd klikněte pravým tlačítkem na název třídy pro ATL objektu.  
  
2.  Klikněte na tlačítko **přidat** z místní nabídky a pak klikněte na tlačítko **přidat bod připojení** zobrazíte [Průvodce implementací bodu připojení](../ide/implement-connection-point-wizard.md).  
  
3.  Vyberte rozhraní bodu připojení k implementaci z příslušného typu knihoven a klikněte na tlačítko **Dokončit**.  
  
4.  V zobrazení tříd prozkoumejte třídy proxy vytvořené pro každý bod připojení. Třídy se zobrazí jako CProxy*InterfaceName*\<T > a jsou odvozené z [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).  
  
5.  Dvakrát klikněte na třídu bodu připojení pro zobrazení definice třídy spojovacího bodu.  
  
    -   Pokud budete implementovat spojovací bod pro vlastní projektu rozhraní, zobrazí se následující definice  
  
        ```  
        template< class T >  
        class CProxyInterfaceName :  
           public IConnectionPointImpl< T, &IID_InterfaceName >  
        {  
        public:  
        };  
        ```  
  
         Pokud budete implementovat místního rozhraní, metod a vlastností vložit do těla třídy.  
  
    -   Pokud implementujete bod připojení pro jiné rozhraní, definice zahrnuje metody rozhraní, každý před sebou `Fire_`.  
  
## <a name="see-also"></a>Viz také  
 [Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Přidání body připojení k objektu](../atl/adding-connection-points-to-an-object.md)