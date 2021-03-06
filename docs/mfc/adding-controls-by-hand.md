---
title: Ruční přidání ovládacích prvků
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
ms.openlocfilehash: c70539b49fcf2aa87f0bee375a87b38277b6ed42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394803"
---
# <a name="adding-controls-by-hand"></a>Ruční přidání ovládacích prvků

Můžete buď [přidání ovládacích prvků do dialogového okna s editorem dialogového okna](../mfc/using-the-dialog-editor-to-add-controls.md) nebo přidávat sami, s kódem.

Chcete-li vytvořit objekt ovládacího prvku, bude obvykle vložit objekt ovládacího prvku jazyka C++ v dialogovém okně C++ nebo objekt okna rámce. Stejně jako mnoho dalších objektů v rámci ovládací prvky vyžadují dvoufázová konstrukce. Měli byste zavolat ovládacího prvku **vytvořit** členské funkce jako součást vytváření dialogového okna nadřazené okno rámce nebo pole. Pro dialogová okna, to se obvykle provádí v [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)a oken s rámečkem v [OnCreate](../mfc/reference/cwnd-class.md#oncreate).

Následující příklad ukazuje, jak může prohlásit `CEdit` objektu v deklaraci třídy z třídy odvozené dialogového okna a následně zavolat `Create` členskou funkci `OnInitDialog`. Protože `CEdit` objekt je deklarován jako vložený objekt, je vytvořen automaticky při vytvoření objektu dialogového okna, ale je stále je nutné inicializovat s vlastním `Create` členskou funkci.

[!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]

Následující `OnInitDialog` funkce nastaví obdélníku, pak zavolá `Create` vytvořit ovládací prvek pro úpravy Windows a připojit ho k neinicializovaného `CEdit` objektu.

[!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]

Po vytvoření upravit objekt, můžete také nastavit zaměření pro vstup na ovládací prvek voláním `SetFocus` členskou funkci. Nakonec se vrátí 0 z `OnInitDialog` zobrazíte nastavit fokus. Pokud jste vrátí nenulovou hodnotu, dialogové okno správce nastaví fokus na první položku v seznamu položek dialogového okna ovládacího prvku. Ve většině případů budete chtít přidat ovládací prvky dialogových oknech s editorem dialogového okna.

## <a name="see-also"></a>Viz také:

[Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)<br/>
[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)
