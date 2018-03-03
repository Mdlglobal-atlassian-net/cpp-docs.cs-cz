---
title: "Schránka: Použití schránky systému Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6063a27495d46e4b54f3133b92689e4b0faaa631
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard-using-the-windows-clipboard"></a>Schránka: Použití schránky systému Windows
Toto téma popisuje, jak používat standardní API schránky systému Windows v rámci aplikace knihovny MFC.  
  
 Většina aplikací pro Windows podporuje vyjímání nebo kopírování dat do schránky systému Windows a vkládání dat ze schránky. Formáty dat schránky liší mezi aplikacemi. Rozhraní framework podporuje pouze omezený počet formáty schránky pro omezený počet tříd. Za normálních okolností implementujete příkazů týkajících se schránky – vyjmutí, kopírování a vložení – v nabídce Upravit pro zobrazení. Knihovny tříd definuje ID příkazu pro tyto příkazy: **id_edit_cut –**, **id_edit_copy –**, a **id_edit_paste –**. Jejich výzvy řádek zprávy je definována.  
  
 [Zprávy a příkazy v rámci](../mfc/messages-and-commands-in-the-framework.md) vysvětluje, jak pro zpracování příkazy nabídky v aplikaci mapování na obslužnou rutinu příkaz nabídky. Tak dlouho, dokud vaše aplikace nedefinuje funkce obslužné rutiny pro příkazy schránky v nabídce Upravit, zůstanou zakázané. Zápis funkce obslužné rutiny pro příkazy vyjmutí a kopírování, implementujte výběr ve vaší aplikaci. Zápis obslužné rutiny funkce pro příkaz vložení, dotaz schránky pro zjistil, zda obsahuje data ve formátu, který může přijmout vaší aplikace. Například pokud chcete povolit příkaz Kopírovat, můžete napsat obslužnou rutinu přibližně takto:  
  
 [!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]  
  
 Vyjmutí, kopírování a vložení příkazy jsou pouze smysluplný v některých kontextech. Vyjmutí a kopírování příkazů by měl povolit pouze v případě, že je něco je vybrán, a příkaz Vložit pouze v případě něco do schránky. Toto chování můžete zadat tak, že definujete funkce obslužné rutiny aktualizace, které povolení nebo zakázání tyto příkazy v závislosti na kontextu. Další informace najdete v tématu [postup aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md).  
  
 Knihovny Microsoft Foundation Class poskytuje podporu schránky pro úpravy textu s `CEdit` a `CEditView` třídy. Třídy OLE také zjednodušit implementující operace schránky, které zahrnují OLE – položky. Další informace o třídy OLE najdete v tématu [schránka: použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md).  
  
 Implementace dalších upravit příkazy nabídky, jako je vrácení zpět (**id_edit_undo –**) a znovu proveďte (**id_edit_redo –**), zůstane na vás. Pokud vaše aplikace nepodporuje tyto příkazy, můžete je snadno odstranit ze souboru prostředků pomocí editory prostředků Visual C++.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Kopírování a vkládání dat](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
## <a name="see-also"></a>Viz také  
 [Schránka](../mfc/clipboard.md)

