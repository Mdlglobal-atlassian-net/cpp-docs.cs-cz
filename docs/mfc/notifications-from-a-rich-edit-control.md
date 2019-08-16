---
title: Oznámení z ovládacích prvků pro úpravy s formátováním
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], notification [MFC]
- CRichEditCtrl class [MFC], notifications
- rich edit controls [MFC], notifications
- notifications [MFC], from CRichEditCtrl
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
ms.openlocfilehash: d097996e61a3d461dacd3d30e13b9262c7d32434
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508054"
---
# <a name="notifications-from-a-rich-edit-control"></a>Oznámení z ovládacích prvků pro úpravy s formátováním

Zprávy s oznámením oznamují události, které ovlivňují ovládací prvek RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Mohou být zpracovány nadřazeným oknem nebo pomocí reflexe zprávy samotným ovládacím prvkem pro úpravy RTF. Ovládací prvky s bohatou úpravou podporují všechny oznamovací zprávy používané s ovládacími prvky pro úpravy a také několik dalších. Můžete určit, které oznamovací zprávy ovládací prvek s bohatým ovládáním pošle své nadřazené okno pomocí nastavení "maska události".

Pro nastavení masky události pro ovládací prvek s formátováním RTF použijte členskou funkci [SetEventMask](../mfc/reference/cricheditctrl-class.md#seteventmask) . Aktuální masku události pro ovládací prvek s bohatým úpravou můžete načíst pomocí členské funkce [GetEventMask –](../mfc/reference/cricheditctrl-class.md#geteventmask) .

Následující odstavce uvádějí několik konkrétních oznámení a jejich použití:

- EN_MSGFILTER, který zpracovává oznámení EN_MSGFILTER, umožňuje třídu, buď ovládací prvek s bohatým úpravou nebo jeho nadřazené okno, filtrovat všechny vstupy klávesnice a myši na ovládací prvek. Obslužná rutina může zabránit zpracování zprávy klávesnice nebo myši nebo může změnit zprávu změnou zadané struktury [MSGFILTER](/windows/win32/api/richedit/ns-richedit-msgfilter) .

- EN_PROTECTED pořídí zprávu oznámení EN_PROTECTED, která zjistí, kdy se uživatel pokusí upravit chráněný text. Chcete-li označit rozsah textu jako chráněný, můžete nastavit efekt chráněný znak. Další informace naleznete v tématu [formátování znaků v ovládacích prvcích pro úpravy s formátováním](../mfc/character-formatting-in-rich-edit-controls.md).

- EN_DROPFILES můžete uživateli povolit vyřazení souborů v ovládacím prvku Rich Edit zpracováním zprávy s oznámením EN_DROPFILES. Zadaná struktura [ENDROPFILES](/windows/win32/api/richedit/ns-richedit-endropfiles) obsahuje informace o vynechávání souborů.

- EN_SELCHANGE aplikace může zjistit, kdy se aktuální výběr změní zpracováním zprávy oznámení EN_SELCHANGE. Zpráva oznámení určuje strukturu [SelChange](/windows/win32/api/richedit/ns-richedit-selchange) , která obsahuje informace o novém výběru.

## <a name="see-also"></a>Viz také:

[Používání atributu CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
