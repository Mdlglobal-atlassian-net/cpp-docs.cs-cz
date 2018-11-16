---
title: Přidat událost
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.event.overview
helpviewer_keywords:
- ActiveX controls [C++], adding events to
- MFC ActiveX controls [C++], adding events
- events [C++], ActiveX controls
- add event wizard [C++]
ms.assetid: fe34832a-edfc-4f86-aacb-8df77001873d
ms.openlocfilehash: 1d5a8f5666dd04e00f8a438fdbf00320c37e14f4
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693422"
---
# <a name="add-an-event"></a>Přidat událost

Ze zobrazení tříd, můžete ji přidat události [Průvodce přidáním události](#add-event-wizard) pouze pro třídy ovládacího prvku v vaše [ovládací prvek ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control.md) projektu. Pokud chcete přidat událost na jiný typ projektu, použijte **události** tlačítko [okno vlastností](/visualstudio/ide/reference/properties-window).

**Postup přidání události do vašeho projektu ovládací prvek ActiveX knihovny MFC:**

1. V zobrazení tříd rozbalte uzel projektu pro zobrazení tříd v projektu.

1. Klikněte pravým tlačítkem na třídě ovládacího prvku v projektu.

1. V místní nabídce zvolte **přidat**a klikněte na tlačítko **přidat událost** zobrazíte Průvodce přidáním události.

1. Zadejte informace o událostech do polí příslušné průvodce.

1. Vyberte **Dokončit** k přidání události do projektu.

## <a name="in-this-section"></a>V tomto oddílu

- [Průvodce přidáním události](#add-event-wizard)

## <a name="add-event-wizard"></a>Průvodce přidáním události

Tento průvodce přidá událost do projektu ovládacího prvku ActiveX knihovny MFC. Můžete zadat vlastní událost, přizpůsobení typické základní událost nebo vyberte ze seznamu uložených událostí.

- **Název události**

   Nastaví název používají klienti automatizace k vyžádání události z třídy. Zadejte název a vyberte ho ze seznamu.

- **Typ události**

   Určuje typ události pro přidání. K dispozici pouze v případě, že vyberete **název události** seznamu.

   |Možnost|Popis|
   |------------|-----------------|
   |**Stock**|Určuje, že uložených událostí, jako je kliknutí na tlačítko, budou implementovány pro tuto třídu. Uložených událostí jsou definovány v knihovny Microsoft Foundation Class (MFC).|
   |**Vlastní**|Určuje, že používáte vlastní implementaci události.|

- **Interní název**

   Nastaví název členské funkce, která odesílá událost. K dispozici pouze pro vlastní události. Název je založen na **název události**. Interní název můžete změnit, pokud chcete zadat jiný než název **název události**.

- **Typ parametru**

   Nastaví typ **název parametru**. Vyberte typ ze seznamu.

- **Název parametru**

   Nastaví název parametru předávání události. Po zadání názvu, je nutné vybrat **přidat** ho přidat do seznamu parametrů.

   Jakmile vyberete **přidat**, zobrazí se název parametru v **seznam parametrů**.

   > [!NOTE]
   > Pokud zadáte název parametru a pak vyberete **Dokončit** dřív, než vyberete **přidat**, pak parametr není přidán k této události. Musíte najít metodu a ručně vložit parametr.

- **Add**

   Přidá parametr, který jste zadali v **název parametru**a její typ na **seznam parametrů**. Vyberte **přidat** přidání parametru do seznamu.

- **odebrat**

   Odstraní parametr vyberete v **seznam parametrů** ze seznamu.

- **Seznam parametrů**

   Zobrazí všechny parametry a jejich typy, které aktuálně přidané k metodě. Jak budete přidávat parametry, průvodce aktualizuje **seznam parametrů** zobrazíte každý parametr pomocí jeho typu.
