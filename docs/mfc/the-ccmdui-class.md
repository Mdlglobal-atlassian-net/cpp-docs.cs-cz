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
ms.openlocfilehash: 47ef359f71d9dd30f2ba1ff1c4cf504bccd33ffd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667945"
---
# <a name="the-ccmdui-class"></a>CCmdUI – třída

Když se směruje na její obslužná rutina příkazu k aktualizaci, rozhraní předá obslužnou rutinu ukazatele na `CCmdUI` objektu (nebo na objekt `CCmdUI`– odvozené třídy). Tento objekt představuje položka nabídky nebo panelu nástrojů tlačítko nebo jiného uživatelského rozhraní objektu, který vygeneroval tento příkaz. Obslužná rutina aktualizace volání členských funkcí `CCmdUI` struktury prostřednictvím ukazatele aktualizace objektů uživatelského rozhraní. Tady je příklad, obslužnou rutinu aktualizace pro vymazat všechny položky nabídky:

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Tato obslužná rutina zavolá `Enable` členské funkce objektu s přístupem k položce nabídky. `Enable` Díky položky k dispozici pro použití.

## <a name="see-also"></a>Viz také

[Postupy: Aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)

