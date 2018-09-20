---
title: Implementace bodu připojení (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9bba7fdfd44b0a0a97a6d110d2a44b492e1ca449
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429328"
---
# <a name="implementing-a-connection-point-visual-c"></a>Implementace bodu připojení (Visual C++)

Implementace bodu připojení pomocí Průvodce bodem připojení implementovat, musí vytvoříte projekt knihovny ATL modelu COM aplikace nebo jako aplikace knihovny MFC, která obsahuje podporu ATL. Můžete použít [Průvodce projektem ATL](../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt ATL do aplikace knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) k implementaci podpory knihovny ATL pro aplikaci knihovny MFC.

> [!NOTE]
>  Informace o implementaci spojovací body pro projekt knihovny MFC naleznete v tématu [spojovací body](../mfc/connection-points.md).

Po vytvoření projektu, implementace bodu připojení, musíte nejprve přidat objekt ATL. V tématu [přidání objektů a ovládacích prvků do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) seznam průvodcích, které přidat objekty do projektu ATL s Knihovnami.

> [!NOTE]
>  Průvodce nepodporuje dialogová okna ATL, webové služby XML vytvořené pomocí knihovny ATL Server, objekty výkonu a čítače výkonu.

Objekt umožňující připojení k (tedy zdrojový) můžete zveřejnit bod připojení pro každou odchozí rozhraní. Každý odchozí rozhraní je možné implementovat klientem na objekt (tj. jímka). Další informace najdete v tématu [ATL – body připojení](../atl/atl-connection-points.md).

### <a name="to-implement-a-connection-point"></a>Implementace bodu připojení

1. V zobrazení tříd klikněte pravým tlačítkem myši na název třídy pro váš objekt knihovny ATL.

1. Klikněte na tlačítko **přidat** z místní nabídky a pak klikněte na tlačítko **přidat bod připojení** zobrazíte [Průvodce implementací bodu připojení](../ide/implement-connection-point-wizard.md).

1. Vyberte rozhraní bod připojení k implementaci z příslušného typu knihovny a klikněte na tlačítko **Dokončit**.

1. V zobrazení tříd prozkoumejte třídy proxy vytvořené pro každý bod připojení. Třídy se zobrazí jako CProxy*InterfaceName*\<T > a jsou odvozeny z [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).

1. Dvakrát klikněte na panel třída bodu připojení pro zobrazení definice třídy bodu připojení.

   - Pokud se rozhodnete implementovat bod připojení pro svůj projekt rozhraní, zobrazí se následující definice

        ```
        template< class T >
        class CProxyInterfaceName :
           public IConnectionPointImpl< T, &IID_InterfaceName >
        {
        public:
        };
        ```

         If you implement a local interface, methods and properties appear in the class body.

   - Pokud se rozhodnete implementovat bod připojení pro jiné rozhraní, definice obsahuje metody rozhraní, každý předchází `Fire_`.

## <a name="see-also"></a>Viz také

[Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Přidání bodů připojení objektu](../atl/adding-connection-points-to-an-object.md)