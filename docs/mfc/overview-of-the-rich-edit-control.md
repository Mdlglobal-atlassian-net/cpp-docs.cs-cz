---
title: Přehled ovládacích prvků pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: 7f307674645ad68455123b801fef8e4ae24b5b41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548275"
---
# <a name="overview-of-the-rich-edit-control"></a>Přehled ovládacích prvků pro úpravy s formátováním

> [!IMPORTANT]
>  Pokud používáte ovládacího prvku v dialogovém okně (bez ohledu na to, zda je vaše aplikace SDI MDI, nebo na základě dialogového okna), je nutné volat [afxinitrichedit –](../mfc/reference/application-information-and-management.md#afxinitrichedit) po před dialogového okna se zobrazí pole. Typické místo pro volání této funkce je ve svém programu `InitInstance` členskou funkci. Není nutné volat pokaždé, když dialogovém okně zobrazí jenom při prvním spuštění. Není nutné volat `AfxInitRichEdit` při práci s `CRichEditView`.

Ovládací prvky pro úpravy s formátováním ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) poskytují programovací rozhraní pro formátování textu. Však musí aplikace implementovat součásti potřebné k zajištění operací formátování pro uživatele k dispozici žádné uživatelského rozhraní. To znamená získáte bohaté upravit ovládací prvek podporuje změna atributů znak nebo odstavce vybraného textu. Příklady znaků, které atributy jsou tučné, kurzíva, rodina písem a velikost v bodech. Příklady atributy odstavce: zarovnání, okrajů a tabulátoru. Je ale jenom na vás k poskytování uživatelského rozhraní, zda tlačítka na panelu nástrojů, položky nabídky nebo dialogové okno znak formátu. Existují také funkce k dotazování ovládací prvek RTF pro atributy aktuálního výběru. Pomocí těchto funkcí zobrazte aktuální nastavení pro atributy, například nastavení zaškrtávací políčko u příkazu uživatelského rozhraní, pokud výběr obsahuje atribut tučného písma formátování.

Další informace o formátování znaků a odstavců najdete v tématu [formátování](../mfc/character-formatting-in-rich-edit-controls.md) a [formátování odstavce](../mfc/paragraph-formatting-in-rich-edit-controls.md) dále v tomto tématu.

Pro úpravy s formátováním podpora ovládacích prvků téměř všechny operace a zprávy s oznámením použít s víceřádková textová pole. Ovládacích prvcích pro úpravy proto, že již ovládacích prvcích pro úpravy k použití můžete snadno změnit používat bohaté aplikace. Další zprávy a oznámení umožňují aplikacím přístup k funkci jedinečné pro bohaté ovládací prvky. Informace o ovládacích prvcích pro úpravy, naleznete v tématu [CEdit](../mfc/reference/cedit-class.md).

Další informace o oznámeních najdete v tématu [oznámení z ovládacího prvku Rich upravit](../mfc/notifications-from-a-rich-edit-control.md) dále v tomto tématu.

## <a name="see-also"></a>Viz také

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

