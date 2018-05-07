---
title: Přejmenujte | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a064527f6afcbf91be3fb4e51180be647c1f506
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
