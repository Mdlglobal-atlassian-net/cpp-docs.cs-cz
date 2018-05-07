---
title: Průvodce implementací bodu připojení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.impl.cp.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef2f7efa92de3714170e403ea50b5f486c8367d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="implement-connection-point-wizard"></a>Průvodce implementací bodu připojení
Tento průvodce implementuje bod připojení pro objekt COM. Objekt umožňující připojení (tedy zdroje) můžou zpřístupnit spojovací bod pro vlastní rozhraní nebo pro jakékoli odchozí rozhraní. Visual C++ i Windows poskytují knihovny typů, které mají odchozí rozhraní. Každý odchozí rozhraní může být implementováno klientem objektu (tj. jímka).  
  
 Další informace najdete v tématu [ATL – body připojení](../atl/atl-connection-points.md).  
  
 **Dostupné knihovny typů**  
 Zobrazí dostupné knihovny typů obsahující definice rozhraní, pro které můžete implementovat body připojení. Klikněte na tlačítko se třemi tečkami vyhledat soubor obsahující typ knihovnu, která má použít.  
  
 **Poloha**  
 Zobrazí umístění knihovny typů v aktuálně vybranou **dostupné knihovny typů** seznamu.  
  
 **Rozhraní**  
 Zobrazí rozhraní, jejichž definice jsou obsaženy v aktuálně vybrané v knihovně typů **dostupné knihovny typů** pole.  
  
|Tlačítko přenosu|Popis|  
|---------------------|-----------------|  
|**>**|Přidá **implementovat body připojení** název rozhraní aktuálně vybraného v seznamu **rozhraní** seznamu.|  
|**>>**|Přidá **implementovat body připojení** názvy všech rozhraní k dispozici v seznamu **rozhraní** seznamu.|  
|**<**|Odebere aktuálně vybraný v název rozhraní **implementovat body připojení** seznamu.|  
|**<<**|Odebere všechny názvy rozhraní **implementovat body připojení** seznamu.|  
  
 **Implementovat body připojení**  
 Zobrazuje názvy rozhraní, pro které můžete implementovat body připojení po kliknutí na tlačítko **Dokončit**.  
  
## <a name="see-also"></a>Viz také  
 [Implementace bodu připojení](../ide/implementing-a-connection-point-visual-cpp.md)