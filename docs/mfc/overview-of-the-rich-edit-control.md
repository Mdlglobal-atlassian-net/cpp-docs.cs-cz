---
title: Přehled ovládacích prvků pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: 9ef696bc348dfb18b797b487224b97261020e11c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366876"
---
# <a name="overview-of-the-rich-edit-control"></a>Přehled ovládacích prvků pro úpravy s formátováním

> [!IMPORTANT]
> Pokud používáte rozšířený ovládací prvek pro úpravy v dialogovém okně (bez ohledu na to, zda je vaše aplikace SDI, MDI nebo dialogová okna), musíte před zobrazením dialogového okna zavolat [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) jednou. Typické místo pro volání této funkce je `InitInstance` v členské funkci programu. Není nutné volat pro pokaždé, když zobrazíte dialogové okno, pouze při prvním zobrazení. `AfxInitRichEdit` Pokud pracujete se společností . `CRichEditView`

Bohaté ovládací prvky pro úpravy ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) poskytují programovací rozhraní pro formátování textu. Aplikace však musí implementovat všechny součásti uživatelského rozhraní nezbytné k tomu, aby byly operace formátování dostupné uživateli. To znamená, že ovládací prvek rich edit podporuje změnu atributů znaků nebo odstavců vybraného textu. Některé příklady atributů znaků jsou tučné písmo, kurzíva, rodina písem a velikost bodu. Příklady atributů odstavce zahrnují zarovnání, okraje a zarážky tabulátoru. Je však na vás, abyste poskytli uživatelské rozhraní, ať už se jedná o tlačítka panelu nástrojů, položky nabídky nebo dialogové okno znaků formátu. K dispozici jsou také funkce pro dotaz na ovládací prvek rich edit pro atributy aktuálního výběru. Tyto funkce slouží k zobrazení aktuálního nastavení atributů, například nastavením zaškrtnutí v příkazu UI, pokud má výběr atribut tučného formátování znaků.

Další informace o formátování znaků a odstavců naleznete v [tématu Formátování znaků](../mfc/character-formatting-in-rich-edit-controls.md) a [Formátování odstavců](../mfc/paragraph-formatting-in-rich-edit-controls.md) dále v tomto tématu.

Ovládací prvky pro bohaté úpravy podporují téměř všechny operace a oznamovací zprávy používané s víceřádkovými ovládacími prvky pro úpravy. Proto aplikace, které již používají ovládací prvky pro úpravy lze snadno změnit použít bohaté editovat ovládací prvky. Další zprávy a oznámení umožňují aplikacím přístup k funkcím jedinečným pro bohaté ovládací prvky úprav. Informace o ovládacích prvcích úprav naleznete v [tématu CEdit](../mfc/reference/cedit-class.md).

Další informace o oznámeních najdete v [tématu Oznámení z ovládacího prvku rich edit](../mfc/notifications-from-a-rich-edit-control.md) dále v tomto tématu.

## <a name="see-also"></a>Viz také

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
