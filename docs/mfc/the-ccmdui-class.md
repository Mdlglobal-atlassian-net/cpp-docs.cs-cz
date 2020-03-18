---
title: CCmdUI – třída
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 105aa7ad6c5cc6a5563dbde8145327a2b3d066a1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447138"
---
# <a name="the-ccmdui-class"></a>CCmdUI – třída

Při směrování příkazu Update na jeho obslužnou rutinu předává rozhraní obslužnou rutinu ukazatel na objekt `CCmdUI` (nebo na objekt třídy odvozené od `CCmdUI`). Tento objekt představuje položku nabídky nebo tlačítko panelu nástrojů nebo jiný objekt uživatelského rozhraní, který příkaz vygeneroval. Obslužná rutina aktualizace volá členské funkce `CCmdUI` struktury prostřednictvím ukazatele k aktualizaci objektu uživatelského rozhraní. Zde je například obslužná rutina aktualizace pro položku nabídky Vymazat vše:

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Tato obslužná rutina volá členskou funkci `Enable` objektu s přístupem k položce nabídky. `Enable` zpřístupňuje položku k použití.

## <a name="see-also"></a>Viz také

[Postupy: Aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)
