---
title: Přejmenovat | Dokumentace Microsoftu
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
ms.openlocfilehash: 7a00eed341e0fc1ca8573e2f66744ea04055f259
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399200"
---
# <a name="rename"></a>přejmenování
**Co:** slouží k přejmenování identifikátory pro symboly kódu, jako je například pole lokálních proměnných, metod, obory názvů, vlastností a typy.

**Kdy:** chcete bezpečně něco přejmenovat bez nutnosti vyhledáte všechny instance a kopírovat/vložit nový název.

**Důvod, proč:** zkopírujete a vložíte nový název přes celý projekt by pravděpodobně vést k chybám.  Tento nástroj refaktoringu přesně provede akci přejmenování.

**Jak:**

1. Zvýrazněte nebo umístěte kurzor textu uvnitř položky, která má být přejmenována:

   ![Zvýrazněný kód](images/rename_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stisknutím klávesy **Ctrl + R**, pak **Ctrl + R**.  (Všimněte si, že klávesová zkratka může být jiný platformě, na který profil vyberete.)
   * **Myši**
     * Vyberte **Upravit > Refaktorovat > přejmenujte**.
     * Klikněte pravým tlačítkem na kód a vybrat **přejmenovat**.

1. V **přejmenovat** okna, která se otevře, zadejte nový název pro vybranou položku a klikněte **ve verzi Preview** tlačítko.  Změnit **obor vyhledávání** Pokud potřebujete rozšířit nebo zúžit rozsah přejmenování.

   ![Dialogové okno přejmenování](images/rename_dialog.png)

   > [!TIP]
   > Verzi preview, můžete přeskočit kontrolou **přeskočit náhled změní, pokud jsou všechny odkazy potvrzené** možnost.

1. Když **náhled změn – přejmenovat** zobrazí se okno, ujistěte se, že se změny se provádějí odpovídajícím způsobem.  K povolení nebo zakázání přejmenování libovolnou položku pomocí zaškrtávacích políček v horní části okna.

   ![Přejmenování ve verzi preview](images/rename_preview.png)

1. Pokud vše vypadá v pořádku, klikněte na tlačítko **použít** tlačítko a položce se přejmenuje ve zdrojovém kódu.
