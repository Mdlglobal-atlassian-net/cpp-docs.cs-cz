---
title: přejmenování
ms.date: 11/16/2016
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
ms.openlocfilehash: a747784f46341f130d1271fd0f15475b63d7b6d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265001"
---
# <a name="rename"></a>přejmenování

**Co:** Slouží k přejmenování identifikátory pro symboly kódu, jako je například pole lokálních proměnných, metod, obory názvů, vlastností a typy.

**Kdy:** Chcete něco bezpečně přejmenovat bez nutnosti vyhledáte všechny instance a kopírovat/vložit nový název.

**Proč:** Zkopírujete a vložíte nový název přes celý projekt by pravděpodobně vést k chybám.  Tento nástroj refaktoringu přesně provede akci přejmenování.

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
