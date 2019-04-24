---
title: Testování ovládacího prvku ATL DHTML upravené
ms.date: 11/06/2018
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
ms.openlocfilehash: 55cdaba64ccb95ee5695c082a5e146b1e7dc2cf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196571"
---
# <a name="testing-the-modified-atl-dhtml-control"></a>Testování ovládacího prvku ATL DHTML upravené

Vyzkoušejte si nového ovládacího prvku abyste viděli, jak funguje teď.

## <a name="to-build-and-test-the-modified-control"></a>Pro vytváření a testování upravený ovládací prvek

1. Znovu sestavte projekt a otevřete ho v **kontejner testu**. Zobrazit [testování vlastností a událostí pomocí testovacího kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak získat přístup k **kontejner testu**.

   Změnit velikost ovládacího prvku a zobrazit všechny tlačítek, které jste přidali.

1. Zkontrolujte dvě tlačítka, které jste vložili změnou kódu HTML. Každé tlačítko nese popisek, který jste určili v [úprav ovládacího prvku ATL DHTML](../atl/modifying-the-atl-dhtml-control.md): **Aktualizovat** a **HelloHTML**.

1. Testování dvě nová tlačítka, které chcete zobrazit, jak fungují.

Teď otestujte metody, které nejsou součástí uživatelského rozhraní.

1. Zvýrazněte ovládacího prvku, tak se aktivuje ohraničení.

1. Na **ovládací prvek** nabídce zvolte **vyvolání metody**.

   Metody v seznamu s názvem **název metody** jsou metody, které můžete volat kontejneru: `MethodInvoked` a `GoToURL`. Všechny ostatní metody se řídí uživatelské rozhraní.

1. Vyberte metodu invoke, a zvolte **Invoke** zobrazit okno se zprávou metody nebo přejděte na `www.microsoft.com`.

1. V **vyvolání metody** dialogového okna zvolte **Zavřít**.

Další informace o různých prvků a soubory, které tvoří ovládacího prvku ATL DHTML, naleznete v tématu [identifikace prvků projektu ovládací prvek DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).

## <a name="see-also"></a>Viz také:

[Podpora pro ovládací prvek DHTML](../atl/atl-support-for-dhtml-controls.md)
