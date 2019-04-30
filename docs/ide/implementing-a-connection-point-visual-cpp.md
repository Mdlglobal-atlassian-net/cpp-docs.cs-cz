---
title: Implementace bodu připojení
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.cp.overview
helpviewer_keywords:
- connection points [C++], implementing
- implement connection point wizard [C++]
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
ms.openlocfilehash: 7afa61246c5251936967e281f7237dc37e5be045
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344256"
---
# <a name="implement-a-connection-point"></a>Implementace bodu připojení

Implementace bodu připojení pomocí Průvodce bodem připojení implementovat, musí vytvoříte projekt knihovny ATL modelu COM aplikace nebo jako aplikace knihovny MFC, která obsahuje podporu ATL. Můžete použít [Průvodce projektem ATL](../atl/reference/atl-project-wizard.md) k vytvoření aplikace knihovny ATL nebo [přidat objekt ATL do aplikace knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) k implementaci podpory knihovny ATL pro aplikaci knihovny MFC.

> [!NOTE]
> Informace o implementaci spojovací body pro projekt knihovny MFC naleznete v tématu [spojovací body](../mfc/connection-points.md).

Po vytvoření projektu, implementace bodu připojení, musíte nejprve přidat objekt ATL. V tématu [přidání objektů a ovládacích prvků do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) seznam průvodcích, které přidat objekty do projektu ATL s Knihovnami.

> [!NOTE]
> Průvodce nepodporuje dialogová okna ATL, webové služby XML vytvořené pomocí knihovny ATL Server, objekty výkonu a čítače výkonu.

Objekt umožňující připojení k (tedy zdrojový) můžete zobrazit bod připojení pro každou odchozí rozhraní. Každý odchozí rozhraní je možné implementovat klientem na objekt (tj. jímka). Další informace najdete v tématu [ATL – body připojení](../atl/atl-connection-points.md).

**Implementovat bod připojení:**

1. V zobrazení tříd klikněte pravým tlačítkem myši na název třídy pro váš objekt knihovny ATL.

1. Zvolte **přidat** z místní nabídky a klikněte na tlačítko **přidat bod připojení** zobrazíte [Průvodce implementací bodu připojení](#implement-connection-point-wizard).

1. Vyberte rozhraní bod připojení k implementaci z knihovny příslušného typu a vyberte **Dokončit**.

1. V zobrazení tříd prozkoumejte třídy proxy vytvořené pro každý bod připojení. Třídy se zobrazí jako CProxy*InterfaceName*\<T > a jsou odvozeny z [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).

1. Dvakrát klikněte na panel třída bodu připojení pro zobrazení definice třídy bodu připojení.

   - Pokud se rozhodnete implementovat bod připojení pro svůj projekt rozhraní, zobrazí se následující definice:

     ```cpp
     template< class T >
     class CProxyInterfaceName :
     public IConnectionPointImpl< T, &IID_InterfaceName >
     {
     public:
     };
     ```

   - Pokud se rozhodnete implementovat místní rozhraní, metody a vlastnosti vložit do těla třídy.

   - Pokud se rozhodnete implementovat bod připojení pro jiné rozhraní, definice obsahuje metody rozhraní, každý předchází `Fire_`.

## <a name="in-this-section"></a>V tomto oddílu

- [Průvodce implementací bodu připojení](#implement-connection-point-wizard)

## <a name="implement-connection-point-wizard"></a>Průvodce implementací bodu připojení

Tento průvodce implementuje bod připojení pro objekt modelu COM. Objekt umožňující připojení k (tedy zdrojový) můžete zobrazit spojovací bod pro vlastní rozhraní nebo pro všechny odchozí rozhraní. Visual C++ i Windows poskytují knihovny typů, které mají odchozí rozhraní. Každý odchozí rozhraní je možné implementovat klientem na objekt (tj. jímka).

Další informace najdete v tématu [ATL – body připojení](../atl/atl-connection-points.md).

- **Dostupné knihovny typů**

  Zobrazí dostupné knihovny typů obsahující definice rozhraní, pro které můžete implementovat spojovací body. Vyberte tlačítko se třemi tečkami vyhledejte soubor, který má knihovnu typů použitou.

- **Poloha**

  Zobrazí umístění aktuálně vybrané v knihovně typů **dostupné knihovny typů** seznamu.

- **Rozhraní**

  Zobrazí rozhraní, jejichž definice jsou uložené v aktuálně vybrané v knihovně typů **dostupné knihovny typů** pole.

  |Tlačítka převodu|Popis|
  |---------------------|-----------------|
  |**>**|Přidá **body připojení implementovat** rozhraní název aktuálně vybraného v seznamu **rozhraní** seznamu.|
  |**>>**|Přidá **body připojení implementovat** názvy všech rozhraní k dispozici v seznamu **rozhraní** seznamu.|
  |**\<**|Odebere aktuálně vybrané v název rozhraní **body připojení implementovat** seznamu.|
  |**\<\<**|Odebere všechny názvy teď uvedená v rozhraní **body připojení implementovat** seznamu.|

- **Body připojení implementovat**

  Zobrazuje názvy rozhraní, pro které můžete implementovat spojovací body při výběru **Dokončit**.
