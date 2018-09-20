---
title: Ccmdui – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CCmdUI
dev_langs:
- C++
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18b5675aff2d10f224238a1ba6d3b919e1b285a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374579"
---
# <a name="the-ccmdui-class"></a>CCmdUI – třída

Když se směruje na její obslužná rutina příkazu k aktualizaci, rozhraní předá obslužnou rutinu ukazatele na `CCmdUI` objektu (nebo na objekt `CCmdUI`– odvozené třídy). Tento objekt představuje položka nabídky nebo panelu nástrojů tlačítko nebo jiného uživatelského rozhraní objektu, který vygeneroval tento příkaz. Obslužná rutina aktualizace volání členských funkcí `CCmdUI` struktury prostřednictvím ukazatele aktualizace objektů uživatelského rozhraní. Tady je příklad, obslužnou rutinu aktualizace pro vymazat všechny položky nabídky:

[!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]

Tato obslužná rutina zavolá `Enable` členské funkce objektu s přístupem k položce nabídky. `Enable` Díky položky k dispozici pro použití.

## <a name="see-also"></a>Viz také

[Postupy: Aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)

