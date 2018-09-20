---
title: Použití seznamů vlastností v aplikaci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog templates [MFC], property sheets
- dialog resources
- property pages [MFC], property sheets
- DoModal method property sheets
- AddPage method [MFC]
- property sheets, about property sheets
- Create method [MFC], property sheets
- CPropertyPage class [MFC], styles
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5b5bb50c99efc2a7b18fbbbabba394ec5330661
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378199"
---
# <a name="using-property-sheets-in-your-application"></a>Použití seznamů vlastností v aplikaci

Pokud chcete použít seznam vlastností ve vaší aplikaci, proveďte následující kroky:

1. Vytvoření prostředku šablony dialogového okna pro každou stránku vlastností. Mějte na paměti, která uživatel může být Měním z jedné stránky, takže rozložení na každé stránce jako konzistentně co nejlépe.

     Šablony dialogu pro všechny stránky není potřeba mít stejnou velikost. Rozhraní používá velikost největší stránky k určení, kolik místa k přidělení v seznamu vlastností pro stránky vlastností.

     Při vytváření prostředku šablony dialogového okna stránky vlastností, je nutné zadat následující styly v seznamu vlastností pro dialogové okno Vlastnosti:

   - Nastavte **titulek** textové pole na **Obecné** stránky na text, který chcete zobrazovat na kartě pro tuto stránku.

   - Nastavte **styl** pole se seznamem na **styly** stránce **podřízené**.

   - Nastavte **ohraničení** pole se seznamem na **styly** stránce **tenký**.

   - Ujistěte se, že **Titlebar** zaškrtávací políčko na **styly** je vybrána stránka.

   - Ujistěte se, že **zakázané** zaškrtávací políčko na **další styly** je vybrána stránka.

1. Vytvoření [CPropertyPage](../mfc/reference/cpropertypage-class.md)-odvozené třídy odpovídající každé šablony dialogového okna stránky vlastností. Zobrazit [přidání třídy](../ide/adding-a-class-visual-cpp.md). Zvolte `CPropertyPage` jako základní třídy.

1. Vytvořte členské proměnné pro uložení hodnoty pro tuto stránku vlastností. Proces pro přidání členské proměnné stránky vlastností je přesně stejné jako přidání členské proměnné do dialogového okna, protože je specializované dialogové okno stránky vlastností. Další informace najdete v tématu [definování členských proměnných pro ovládací prvky dialogového okna](../windows/defining-member-variables-for-dialog-controls.md).

1. Vytvoření [cpropertysheet –](../mfc/reference/cpropertysheet-class.md) objektu ve zdrojovém kódu. Obvykle vytvoříte `CPropertySheet` objektu v obslužnou rutinu pro příkaz, který zobrazí stránku vlastností. Tento objekt představuje celou vlastností. Pokud vytvoříte modální seznam vlastností s [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) – funkce rozhraní framework poskytuje tři příkazová tlačítka ve výchozím nastavení: OK, zrušit a použít. Rozhraní vytvoří žádné příkazová tlačítka pro vytvoření modeless – seznam vlastností s [vytvořit](../mfc/reference/cpropertysheet-class.md#create) funkce. Není nutné odvozovat třídu z `CPropertySheet` Pokud chcete přidat další ovládací prvky (například okno náhledu) nebo zobrazit nemodálního seznamu vlastností. Tento krok je nezbytný pro modeless – seznam vlastností, protože neobsahují žádné výchozí ovládací prvky, které lze použít k zavření seznamu vlastností.

1. Pro každou stránku přidat do seznamu vlastností postupujte takto:

   - Jeden objekt vytvořit pro každou `CPropertyPage`-odvozené třídy, kterou jste vytvořili dříve v tomto procesu.

   - Volání [CPropertySheet::AddPage](../mfc/reference/cpropertysheet-class.md#addpage) pro každou stránku.

     Obvykle, objekt, který vytvoří `CPropertySheet` také vytvoří `CPropertyPage` objekty v tomto kroku. Ale pokud se rozhodnete implementovat `CPropertySheet`– odvozené třídy, můžete vložit `CPropertyPage` objekty v `CPropertySheet` objektu a volání `AddPage` pro každou stránku z `CPropertySheet`-odvozený konstruktor třídy. `AddPage` Přidá `CPropertyPage` objektu do seznamu vlastností seznamu stránek, ale ve skutečnosti nevytváří v okně pro danou stránku. Proto není nutné čekat až do vytvoření okna listu vlastností pro volání `AddPage`; lze volat `AddPage` z konstruktoru seznamu vlastností.

     Ve výchozím nastavení Pokud seznam vlastností má více záložek, než se vejde v jediném řádku listu vlastností se karty zásobníku z více řádků. Chcete-li zakázat překrývání, zavolejte [CPropertySheet::EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) s parametrem nastaveným na **FALSE**. Je nutné volat `EnableStackedTabs` při vytváření seznamu vlastností.

1. Volání [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) nebo [vytvořit](../mfc/reference/cpropertysheet-class.md#create) zobrazíte seznam vlastností. Volání `DoModal` vytvořit seznam vlastností jako modální dialogové okno. Volání **vytvořit** k vytvoření seznamu vlastností, jako nemodálního dialogového okna.

1. Výměna dat mezi vlastníka seznam vlastností a stránek vlastností. To je vysvětleno v článku [výměna dat](../mfc/exchanging-data.md).

Příklad použití seznamů vlastností, najdete v ukázce MFC Obecné [PROPDLG](../visual-cpp-samples.md).

## <a name="see-also"></a>Viz také

[Seznamy vlastností](../mfc/property-sheets-mfc.md)

