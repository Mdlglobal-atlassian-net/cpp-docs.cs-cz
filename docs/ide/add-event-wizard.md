---
title: Průvodce přidáním události
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.event.overview
helpviewer_keywords:
- Add Event Wizard [C++]
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
ms.openlocfilehash: e8e78dce3f3f4ec9412be910cde5e0468ce533bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510770"
---
# <a name="add-event-wizard"></a>Průvodce přidáním události

Tento průvodce přidá událost do projektu ovládacího prvku ActiveX knihovny MFC. Můžete zadat vlastní události, obvykle základní událost si můžete přizpůsobit nebo můžete vybrat ze seznamu uložených událostí.

- **Název události**

   Nastaví název používají klienti automatizace k vyžádání události z třídy. Zadejte název a vyberte ho ze seznamu.

- **Typ události**

   Určuje typ události pro přidání. K dispozici pouze v případě, že vyberete **název události** seznamu.

   |Možnost|Popis|
   |------------|-----------------|
   |**Stock**|Určuje, že uložených událostí, jako je kliknutí na tlačítko, budou implementovány pro tuto třídu. Uložených událostí jsou definovány v knihovny Microsoft Foundation Class (MFC).|
   |**Vlastní**|Určuje, že poskytnete vlastní implementaci události.|

- **Interní název**

   Nastaví název členské funkce, která odesílá událost. K dispozici pouze pro vlastní události. Název je založen na **název události**. Interní název můžete změnit, pokud chcete zadat jiný než název **název události**.

- **Typ parametru**

   Nastaví typ **název parametru**. Vyberte typ ze seznamu.

- **Název parametru**

   Nastaví název parametru předávání události. Po zadání názvu, musíte kliknout na **přidat** ho přidat do seznamu parametrů.

   Po kliknutí na **přidat**, zobrazí se název parametru v **seznam parametrů**.

   > [!NOTE]
   > Pokud zadáte název parametru a potom klikněte na tlačítko **Dokončit** před kliknutím na **přidat**, pak parametr není přidán k této události. Musíte najít metodu a ručně vložit parametr. **Seznam parametrů**

- **Add**

   Přidá parametr, který jste zadali v **název parametru**a její typ na **seznam parametrů**. Musíte kliknout na **přidat** přidání parametru do seznamu.

- **odebrat**

   Odstraní parametr vyberete v **seznam parametrů** ze seznamu.

- **Seznam parametrů**

   Zobrazí všechny parametry a jejich typy, které aktuálně přidané k metodě. Jak budete přidávat parametry, průvodce aktualizuje **seznam parametrů** zobrazíte každý parametr pomocí jeho typu.

## <a name="see-also"></a>Viz také

[Přidání události](../ide/adding-an-event-visual-cpp.md)