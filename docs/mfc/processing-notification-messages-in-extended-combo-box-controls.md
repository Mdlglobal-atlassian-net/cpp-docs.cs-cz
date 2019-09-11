---
title: Zpracování zpráv s oznámením v ovládacích prvcích rozšířeného pole se seznamem
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 044cef644f746f7cb70944805882bd8e2f2806b4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908100"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>Zpracování zpráv s oznámením v ovládacích prvcích rozšířeného pole se seznamem

Když uživatelé komunikují s rozšířeným polem se seznamem, ovládací`CComboBoxEx`prvek () odesílá zprávy s oznámením do svého nadřazeného okna, obvykle do zobrazení nebo z objektu dialogového okna. Pokud chcete něco udělat v reakci, Zpracujte tyto zprávy. Například když uživatel aktivuje rozevírací seznam nebo klikne v poli pro úpravy ovládacího prvku, pošle se oznámení CBEN_BEGINEDIT.

Pomocí [Průvodce třídou](reference/mfc-class-wizard.md) přidejte do nadřazené třídy obslužné rutiny oznámení pro ty zprávy, které chcete implementovat.

Následující seznam popisuje různá oznámení odesílaná ovládacím prvkem rozšířené pole se seznamem.

- CBEN_BEGINEDIT se odešle, když uživatel aktivuje rozevírací seznam nebo klikne v poli pro úpravy ovládacího prvku.

- CBEN_DELETEITEM se posílá, když se položka odstranila.

- CBEN_DRAGBEGIN se pošle, když uživatel začne přetahovat obrázek položky zobrazené v části pro úpravy ovládacího prvku.

- CBEN_ENDEDIT se odesílá, když uživatel uzavře operaci v poli pro úpravy nebo vybral položku v rozevíracím seznamu ovládacího prvku.

- CBEN_GETDISPINFO odeslána pro načtení informací o zobrazení položky zpětného volání.

- CBEN_INSERTITEM odeslána, když byla do ovládacího prvku vložena nová položka.

## <a name="see-also"></a>Viz také:

[Používání atributu CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
