---
title: Zpracování zpráv s oznámením v ovládacích prvcích rozšířeného pole se seznamem
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 1890267f26ef43fd1dbf8fdea28f02e3d882d475
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378190"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Zpracování zpráv s oznámením v ovládacích prvcích rozšířeného pole se seznamem

Jak uživatelé komunikovat s poli rozšířené pole se seznamem, ovládací prvek (`CComboBoxEx`) odesílá zprávy s oznámením nezašle nadřazenému oknu, obvykle objekt zobrazení nebo dialogového okna. Tyto zprávy zpracovávají, pokud budete chtít udělat něco v odpovědi. Například když uživatel aktivuje rozevíracího seznamu nebo klikne do oblasti ovládacího prvku textového pole, CBEN_BEGINEDIT oznámení se posílá.

Použijte okno Vlastnosti pro přidání obslužné rutiny oznamovacích do nadřazené třídu pro ty zprávy, které chcete implementovat.

Následující seznam popisuje různé oznámení zaslaná z ovládacího prvku rozšířené pole se seznamem pole.

- CBEN_BEGINEDIT posílají, když uživatel aktivuje rozevíracího seznamu nebo klikne do oblasti ovládacího prvku textového pole.

- CBEN_DELETEITEM posílají, když se odstranil položku.

- CBEN_DRAGBEGIN posílají, když uživatel zahájí přetahování obrázek položky zobrazené v části ovládacího prvku pro úpravy.

- CBEN_ENDEDIT posílají, když uživatel uzavřel operace v rámci pole pro úpravy nebo má vybrat položku z ovládacího prvku rozevíracího seznamu.

- CBEN_GETDISPINFO odeslané k načtení zobrazení informací o položka zpětného volání.

- CBEN_INSERTITEM zasílat nová položka byla vložena do ovládacího prvku.

## <a name="see-also"></a>Viz také:

[Používání atributu CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
