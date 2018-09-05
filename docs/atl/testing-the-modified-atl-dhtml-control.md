---
title: Testování ovládacího prvku ATL DHTML upravené | Dokumentace Microsoftu
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
ms.openlocfilehash: 9730f8ef9bfc89d65ffb89ddbbfe67ce247138e9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755592"
---
# <a name="testing-the-modified-atl-dhtml-control"></a>Testování ovládacího prvku ATL DHTML upravené

Vyzkoušejte si nového ovládacího prvku abyste viděli, jak funguje teď.

#### <a name="to-build-and-test-the-modified-control"></a>Pro vytváření a testování upravený ovládací prvek

1. Znovu sestavte projekt a otevřete ho v kontejneru testů. Zobrazit [testování vlastností a událostí pomocí testovacího kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak získat přístup ke kontejneru testů.

     Změnit velikost ovládacího prvku a zobrazit všechny tlačítek, které jste přidali.

2. Zkontrolujte dvě tlačítka, které jste vložili změnou kódu HTML. Každé tlačítko nese popisek, který jste určili v [úprav ovládacího prvku ATL DHTML](../atl/modifying-the-atl-dhtml-control.md): **aktualizovat** a **HelloHTML**.

3. Testování dvě nová tlačítka, které chcete zobrazit, jak fungují.

Teď otestujte metody, které nejsou součástí uživatelského rozhraní.

1. Zvýrazněte ovládacího prvku, tak se aktivuje ohraničení.

2. Na **ovládací prvek** nabídky, klikněte na tlačítko **vyvolání metody**.

Metody v seznamu s názvem **název metody** jsou metody, které můžete volat kontejneru: `MethodInvoked` a `GoToURL`. Všechny ostatní metody se řídí uživatelské rozhraní.

1. Vyberte metodu invoke a klikněte na tlačítko `Invoke` zobrazit okno se zprávou metody nebo přejděte na www.microsoft.com.

2. V **vyvolání metody** dialogové okno, klikněte na tlačítko **Zavřít**.

Další informace o různých prvků a soubory, které tvoří ovládacího prvku ATL DHTML, naleznete v tématu [identifikace prvků projektu ovládací prvek DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).

## <a name="see-also"></a>Viz také

[Podpora pro ovládací prvek DHTML](../atl/atl-support-for-dhtml-controls.md)

