---
title: "Přejmenujte | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8e4152a1c920a243be9d4aa23712420893e29f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rename"></a>přejmenování
**Co:** umožňuje přejmenovat identifikátory pro kód symboly, například pole, místní proměnné, metody, obory názvů, vlastnosti a typy.

**Kdy:** chcete bezpečně něco přejmenovat bez nutnosti vyhledáte všechny instance a zkopírujte a vložte nový název.  

**Důvod:** kopírování a vkládání nový název napříč celý projekt by pravděpodobně vést k chybám.  Tento nástroj refaktoringu přesně provede přejmenování akce.

**Postupy:**

1. Zvýrazněte nebo umístěte kurzor textu uvnitř položky k přejmenování:

   ![Zvýrazněný kód](images/rename_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stiskněte klávesu **Ctrl + R**, pak **Ctrl + R**.  (Všimněte si, že klávesové zkratky se může lišit na základě na profilu, které jste vybrali.)
   * **Myš**
     * Vyberte **Upravit > Refaktorovat > přejmenujte**.
     * Klikněte pravým tlačítkem na kód a vyberte **přejmenovat**.

1. V **přejmenovat** okna, která se objeví, zadejte nový název pro vybranou položku a klikněte na tlačítko **Preview** tlačítko.  Změna **obor vyhledávání** Pokud potřebujete rozšířit nebo zúžit rozsah přejmenováním.

   ![Dialogové okno Přejmenovat](images/rename_dialog.png)

   > [!TIP]
   > Ve verzi preview, můžete přeskočit kontrolou **přeskočit preview změny, pokud odkazy na všechny potvrzena** možnost.

1. Když **přejmenovat zobrazení náhledu změn -** zobrazí se okno, ujistěte se, že jste požádali změny se provádějí správně.  Pomocí zaškrtávacích políček k povolení nebo zakázání přejmenování libovolnou položku v horní polovině okna.

   ![Přejmenujte preview](images/rename_preview.png)

1. Pokud se vše spokojeni, klikněte na tlačítko **použít** tlačítko a položka se přejmenuje ve zdrojovém kódu.