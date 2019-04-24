---
title: CCmdUI – třída
ms.date: 11/04/2016
f1_keywords:
- CCmdUI
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
ms.openlocfilehash: 8e0af0703924d6fae626d3753b8523efe0c56652
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306298"
---
# <a name="the-ccmdui-class"></a>CCmdUI – třída

Když se směruje na její obslužná rutina příkazu k aktualizaci, rozhraní předá obslužnou rutinu ukazatele na `CCmdUI` objektu (nebo na objekt `CCmdUI`– odvozené třídy). Tento objekt představuje položka nabídky nebo panelu nástrojů tlačítko nebo jiného uživatelského rozhraní objektu, který vygeneroval tento příkaz. Obslužná rutina aktualizace volání členských funkcí `CCmdUI` struktury prostřednictvím ukazatele aktualizace objektů uživatelského rozhraní. Tady je příklad, obslužnou rutinu aktualizace pro vymazat všechny položky nabídky:

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Tato obslužná rutina zavolá `Enable` členské funkce objektu s přístupem k položce nabídky. `Enable` Díky položky k dispozici pro použití.

## <a name="see-also"></a>Viz také:

[Postupy: Aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)
