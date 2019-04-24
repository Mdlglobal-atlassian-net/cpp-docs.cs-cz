---
title: Uživatelem definované obslužné rutiny
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.handlers
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
ms.openlocfilehash: d7c735531e4e2bd4da37ef7ba89cc9c4f9222b47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309587"
---
# <a name="user-defined-handlers"></a>Uživatelem definované obslužné rutiny

Následující položky mapování odpovídají prototypy funkcí.

|Položka mapování|Prototyp funkce|
|---------------|------------------------|
|ON_MESSAGE( \<message>, \<memberFxn> )|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_REGISTERED_MESSAGE( \<nMessageVariable>, \<memberFxn> )|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_THREAD_MESSAGE ( \<zpráva >, \<memberFxn >)|void memberFxn afx_msg (WPARAM, LPARAM);|
|ON_REGISTERED_THREAD_MESSAGE( \<nMessageVariable>, \<memberFxn> )|void memberFxn afx_msg (WPARAM, LPARAM);|

## <a name="see-also"></a>Viz také:

[Mapy zpráv](../../mfc/reference/message-maps-mfc.md)<br/>
[Obslužné rutiny pro zprávy WM_](../../mfc/reference/handlers-for-wm-messages.md)
