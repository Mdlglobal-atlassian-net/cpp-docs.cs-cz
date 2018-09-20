---
title: Přidání záznamu do tabulky akcelerátorů (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e0017e0c4d5462ef985b70b44120ff20066f626
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391797"
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