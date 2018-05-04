---
title: Testování ovládací prvek DHTML upravené ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b140788cd409aa5a11f93689e96fa40c1a167dfe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="testing-the-modified-atl-dhtml-control"></a>Testování ovládacího prvku upravené ATL jazyka DHTML
Vyzkoušejte nový ovládací prvek a zkontrolujte, jak funguje teď.  
  
#### <a name="to-build-and-test-the-modified-control"></a>Pro sestavení a otestování upravené ovládacího prvku  
  
1.  Znovu sestavte projekt a otevřete jej v testu kontejneru. V tématu [testování vlastností a událostí pomocí testovacího kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak přístup – kontejner testů.  
  
     Změnit velikost ovládacího prvku a zobrazit všechny tlačítek, které jste přidali.  
  
2.  Zkontrolujte dvě tlačítka, které jste vložili změnou kódu HTML. Každé tlačítko nenese popisek, který jste určili v [úprava ovládací prvek DHTML ATL](../atl/modifying-the-atl-dhtml-control.md): **aktualizovat** a **HelloHTML**.  
  
3.  Otestujte dvě nová tlačítka, které chcete zobrazit, jak pracují.  
  
 Nyní otestujte metody, které nejsou součástí uživatelského rozhraní.  
  
1.  Zvýrazněte ovládacího prvku, tak se aktivuje ohraničení.  
  
2.  Na **řízení** nabídky, klikněte na tlačítko **vyvolání metody**.  
  
 Metody v seznamu s názvem bez přípony **název metody** jsou metody, které můžete volat kontejneru: `MethodInvoked` a `GoToURL`. Všechny ostatní metody jsou řízeny uživatelského rozhraní.  
  
1.  Vyberte metodu invoke a klikněte na tlačítko `Invoke` zobrazit okno se zprávou metody nebo přejděte na www.microsoft.com.  
  
2.  V **vyvolání metody** dialogové okno, klikněte na tlačítko **Zavřít**.  
  
 Další informace o různých elementy a soubory, které tvoří ovládací prvek ATL DHTML najdete v tématu [identifikace prvky jazyka DHTML řízení projektu](../atl/identifying-the-elements-of-the-dhtml-control-project.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora pro ovládací prvek DHTML](../atl/atl-support-for-dhtml-controls.md)

