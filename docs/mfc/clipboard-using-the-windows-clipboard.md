---
title: 'Schránka: Použití schránky Windows | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Clipboard commands
- Cut/Copy and Paste command handler functions [MFC]
- handler functions, Cut/Copy and Paste commands
- Clipboard [MFC], commands
- commands [MFC], implementing Edit
- Clipboard commands [MFC], implementing
- Windows Clipboard [MFC]
- Clipboard [MFC], Windows Clipboard API
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e43b55382d5e6443119efb52bd1935d3150c1aac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409997"
---
# <a name="clipboard-using-the-windows-clipboard"></a>Schránka: Použití schránky systému Windows

Toto téma popisuje, jak používat standardní API Windows schránky v rámci aplikace knihovny MFC.

Většina aplikací pro Windows podporovat vyjmutí nebo zkopírování dat do schránky Windows a vložením dat ze schránky. Formáty dat schránky se liší mezi aplikacemi. Rozhraní framework podporuje jenom omezený počet formáty schránky pro omezený počet tříd. Obvykle provede příkazy související s schránky – vyjmutí, kopírování a vložení – v nabídce Upravit pro zobrazení. Knihovna tříd definuje ID příkazu pro tyto příkazy: **id_edit_cut –**, **id_edit_copy –**, a **id_edit_paste –**. Vyzve k jejich řádek zprávy jsou také definovány.

[Zprávy a příkazy v rámci](../mfc/messages-and-commands-in-the-framework.md) vysvětluje, jak zpracovat příkazy nabídky ve vaší aplikaci pomocí příkazu nabídky mapování na obslužnou rutinu. Tak dlouho, dokud vaše aplikace nedefinuje funkce obslužné rutiny pro příkazy schránky v nabídce Úpravy, zůstanou zakázané. Zápis funkce obslužné rutiny pro příkazy vyjmutí a kopírování, implementujte výběr v aplikaci. Chcete-li napsat obslužnou rutinu pro příkaz Paste, dotaz do schránky, zda obsahuje data ve formátu, který vaše aplikace může přijmout. Například pokud chcete povolit příkaz Kopírovat, můžete například napsat obslužnou rutinu přibližně takto:

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

Vyjmutí, kopírování a vložení příkazy jsou pouze v určitých kontextech smysluplné. Příkazy vyjmutí a kopírování musí být povolené pouze v případě, že něco je vybraná a příkaz Paste, jenom když se něco je do schránky. Toto chování můžete zadat tak, že definujete funkce obslužné rutiny aktualizace, které povolí nebo zakáže těchto příkazů v závislosti na kontextu. Další informace najdete v tématu [aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md).

Knihovny Microsoft Foundation Class poskytuje podporu schránky pro úpravy textu s `CEdit` a `CEditView` třídy. OLE – třídy také zjednodušit implementaci operace schránky, které se týkají položek OLE. Další informace o OLE – třídy naleznete v tématu [schránka: použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md).

Implementace dalších upravte příkazy nabídek, jako je vrácení zpět (**id_edit_undo –**) a znovu (**id_edit_redo –**), je také zbývá vám. Pokud aplikace nepodporuje tyto příkazy, můžete je snadno odstranit ze souboru prostředků pomocí editory prostředků Visual C++.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Kopírování a vkládání dat](../mfc/clipboard-copying-and-pasting-data.md)

- [Použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>Viz také

[Schránka](../mfc/clipboard.md)

