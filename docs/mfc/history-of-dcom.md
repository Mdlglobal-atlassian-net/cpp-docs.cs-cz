---
title: Historie modelu DCOM | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Remote Automation, DCOM
- DCOM, about DCOM
- DCOM
ms.assetid: c21aa0ea-1396-4b52-b77f-88fb0fdd2a5c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6ef567c39c93c3d43fdfc0fa63886144b03cd474
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="history-of-dcom"></a>Historie modelu DCOM
Když automatizace bylo poprvé dostupné ve časná 1993, se mohou být použity pouze mezi aplikací, které běží na stejném počítači. Ale protože ji sdílet stejnou podchycení jako zbytek OLE, který je COM (nebo Component Object Model), je vždy zamýšleno "učinit vzdáleným" jej by stane, když COM sám aktualizoval zahrnout možnosti vzdálené komunikace. Technická dokumentace se také plánované, přechod z čistě místní operace distribuované operace by vyžadovaly žádné nebo téměř žádné změny existujícího kódu.  
  
 Takže co "vzdálenou komunikaci" znamená místní COM závisí, zda jsou umístěny příjemce rozhraní a provést ve stejném počítači jako zprostředkovatel tohoto rozhraní. Například Microsoft Visual Basicu může řídit kopie aplikace Microsoft Excel na stolního počítače, ale nebyla umožňující směrování spuštění Excelu na jiném počítači. S rozvojem modelu distributed COM příjemce rozhraní již musí nacházet na stejném počítači jako, na kterém se spouští zprostředkovatele rozhraní.  
  
 Jakmile COM byla přizpůsobena pro práci v síti, pak všechny rozhraní které nebyl vázaný na místní provádění modelu (některé rozhraní mají vyplývajících spoléhat na místním počítači zařízení, jako jsou ty kreslení rozhraní, jehož metody mají popisovače kontexty zařízení jako parametry) by měla mít schopnosti produktu probíhá distribuce. Příjemce rozhraní by může požádat o příslušném rozhraní; Toto rozhraní může poskytovat instanci objektu systémem (nebo ke spuštění) na jiný počítač. Mechanismus distribuce v modelu COM by příjemce připojení k poskytovateli tak, že metoda volání uživatelem se zobrazí na konci poskytovatele, kde by byl proveden. Všechny návratové hodnoty by se pak odešlou zpět k příjemce. Na všechny úmyslům a účelům je v rámci distribučních transparentní k příjemce a zprostředkovatele.  
  
 Takové celou řadu COM teď neexistuje. Modelu DCOM ("distributed COM") má dodávané s verzemi počínaje systému Windows NT verze 4.0 a včetně systému Windows 2000. Od pozdní 1996 ho byl k dispozici také pro systém Windows 9 x. V obou případech DCOM zahrnuje sadu nahrazení a další knihovny DLL, s některé nástroje, které poskytují možnosti místní i vzdálené COM. Je proto nyní nedílnou součástí na základě Win32 platformy a bude k dispozici na jiných platformách jiné organizace v čase.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Kde se uplatní Vzdálená automatizace?](where-does-remote-automation-fit-in-q.md)  
  
 [Co přínosy vzdálené automatizace](what-does-remote-automation-provide-q.md)  
  
## <a name="see-also"></a>Viz také  
 [Vzdálená automatizace](../mfc/remote-automation.md)
