---
title: Přidání záznamu do tabulky akcelerátorů (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
ms.openlocfilehash: 63ae7296d7571bb70f4ca7abe05f39591cc40ced
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626847"
---
# <a name="adding-an-entry-to-an-accelerator-table-c"></a>Přidání záznamu do tabulky akcelerátorů (C++)

### <a name="to-add-an-entry-to-an-accelerator-table"></a>Přidání záznamu do tabulky akcelerátorů

1. V projektu jazyka C++, otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. Klikněte pravým tlačítkem v tabulce akcelerátorů a zvolte **nový akcelerátor** z místní nabídky nebo klikněte na položku prázdný řádek v tabulce dole.

3. Vyberte [ID](id-property.md) z rozevíracího seznamu v ID pole nebo zadejte nové ID v **ID** pole.

4. Typ [klíč](../windows/accelerator-key-property.md) chcete použít jako akcelerátor nebo klikněte pravým tlačítkem a zvolte **další stisknutá klávesa** z místní nabídky k nastavení kombinace kláves ( **další stisknutá klávesa** je příkaz k dispozici prostřednictvím **upravit** nabídky).

5. Změnit [modifikátor](../windows/accelerator-modifier-property.md) a [typ](../windows/accelerator-type-property.md), v případě potřeby.

6. Stisknutím klávesy **ENTER**.

   > [!NOTE]
   > Ujistěte se, že se všechny akcelerátory, které definujete. Může mít několik kombinace kláves, které jsou přiřazeny stejnému identifikátoru s neplatí výplně, například **Ctrl** + **P** a **F8** lze obě přiřadit ID_PRINT. Však mít přiřazeno více než jeden ID nebude fungovat dobře, například kombinaci kláves **Ctrl** + **Z** přiřazená ID_SPELL_CHECK a ID_THESAURUS.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Úprava tabulek akcelerátorů](../windows/editing-accelerator-tables.md)<br/>
[Editor akcelerátorů](../windows/accelerator-editor.md)