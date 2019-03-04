---
title: Oznámení z ovládacích prvků pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: fcb1dda1d915dc13e01effed9ba99070b825a15e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274528"
---
# <a name="notifications-from-a-rich-edit-control"></a>Oznámení z ovládacích prvků pro úpravy s formátováním

Oznamovací zprávy ovládacích prvků pro úpravy události ovlivňující bohaté sestavy ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Mohou být zpracovány nadřazené okno nebo pomocí reflexe zprávy podle získáte bohaté upravte samotný ovládací prvek. Bohaté ovládacích prvcích pro úpravy podporují všechny zprávy s oznámením použít s ovládacími prvky pro úpravy, jakož i několik další značky. Můžete určit, jaké zprávy s oznámením ovládacího prvku odešle nezašle nadřazenému oknu nastavením jeho "masky události."

Chcete-li nastavení masky události pro ovládací prvek pro úpravy s formátováním, použijte [seteventmask –](../mfc/reference/cricheditctrl-class.md#seteventmask) členskou funkci. Můžete načíst aktuální masky události pro úpravy s formátováním ovládacího prvku s použitím [geteventmask –](../mfc/reference/cricheditctrl-class.md#geteventmask) členskou funkci.

Následující odstavce seznamu několik upozornění a jejich použití:

- EN_MSGFILTER zpracování oznámení EN_MSGFILTER třídu, buď ovládací prvek RTF a umožňuje nezašle nadřazenému oknu, filtrovat všechny klávesnice a myši do ovládacího prvku. Obslužná rutina může zabránit zpracovává zprávy klávesnice nebo myši nebo zprávu můžete změnit úpravou zadaný [MSGFILTER](/windows/desktop/api/richedit/ns-richedit-_msgfilter) struktury.

- EN_PROTECTED zpracovávat zprávy oznámení EN_PROTECTED zjistit, kdy se uživatel pokusí o chráněný textový upravit. K označení rozsah textu jako chráněný, můžete nastavit efekt chráněné znak. Další informace najdete v tématu [formátování znaků v ovládacích prvcích upravit bohaté](../mfc/character-formatting-in-rich-edit-controls.md).

- EN_DROPFILES můžete povolit uživateli vkládají soubory do ovládacího prvku pomocí zpracování zprávy oznámení EN_DROPFILES. Zadaný [ENDROPFILES](/windows/desktop/api/richedit/ns-richedit-_endropfiles) struktura obsahuje informace o souborech probíhá vyřazování.

- EN_SELCHANGE aplikace může rozpoznat, kdy se zpracováním zprávy oznámení EN_SELCHANGE změní aktuální výběr. Oznámení určuje [selchange –](/windows/desktop/api/richedit/ns-richedit-_selchange) struktura obsahující informace o nový výběr.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
