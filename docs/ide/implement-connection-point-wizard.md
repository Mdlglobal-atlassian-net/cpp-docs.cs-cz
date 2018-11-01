---
title: Průvodce implementací bodu připojení
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.impl.cp.overview
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
ms.openlocfilehash: b818a1a149e95805a8694f6c8d8d1325b33211b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531531"
---
# <a name="implement-connection-point-wizard"></a>Průvodce implementací bodu připojení

Tento průvodce implementuje bod připojení pro objekt modelu COM. Objekt umožňující připojení k (tedy zdrojový) můžete zveřejnit spojovací bod pro vlastní rozhraní nebo pro všechny odchozí rozhraní. Visual C++ i Windows poskytují knihovny typů, které mají odchozí rozhraní. Každý odchozí rozhraní je možné implementovat klientem na objekt (tj. jímka).

Další informace najdete v tématu [ATL – body připojení](../atl/atl-connection-points.md).

- **Dostupné knihovny typů**

   Zobrazí dostupné knihovny typů obsahující definice rozhraní, pro které můžete implementovat spojovací body. Klikněte na tlačítko se třemi tečkami vyhledejte soubor, který obsahuje knihovnu typů použitou.

- **Poloha**

   Zobrazí umístění aktuálně vybrané v knihovně typů **dostupné knihovny typů** seznamu.

- **Rozhraní**

   Zobrazí rozhraní, jejichž definice jsou obsaženy v aktuálně vybrané v knihovně typů **dostupné knihovny typů** pole.

   |Tlačítka převodu|Popis|
   |---------------------|-----------------|
   |**>**|Přidá **body připojení implementovat** rozhraní název aktuálně vybraného v seznamu **rozhraní** seznamu.|
   |**>>**|Přidá **body připojení implementovat** názvy všech rozhraní k dispozici v seznamu **rozhraní** seznamu.|
   |**\<**|Odebere aktuálně vybrané v název rozhraní **body připojení implementovat** seznamu.|
   |**\<\<**|Odebere všechny názvy teď uvedená v rozhraní **body připojení implementovat** seznamu.|

- **Body připojení implementovat**

   Zobrazuje názvy rozhraní, pro které můžete implementovat přípojných bodů po kliknutí na **Dokončit**.

## <a name="see-also"></a>Viz také

[Implementace bodu připojení](../ide/implementing-a-connection-point-visual-cpp.md)