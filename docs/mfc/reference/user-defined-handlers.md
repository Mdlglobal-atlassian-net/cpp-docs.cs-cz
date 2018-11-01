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
ms.openlocfilehash: 4d2102668b7cc964e6fe3bffdcc6931a2961a737
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562250"
---
# <a name="user-defined-handlers"></a>Uživatelem definované obslužné rutiny

Následující položky mapování odpovídají prototypy funkcí.

|Položka mapování|Prototyp funkce|
|---------------|------------------------|
|ON_MESSAGE ( \<zpráva >, \<memberFxn >)|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_REGISTERED_MESSAGE ( \<nMessageVariable >, \<memberFxn >)|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_THREAD_MESSAGE ( \<zpráva >, \<memberFxn >)|void memberFxn afx_msg (WPARAM, LPARAM);|
|ON_REGISTERED_THREAD_MESSAGE ( \<nMessageVariable >, \<memberFxn >)|void memberFxn afx_msg (WPARAM, LPARAM);|

## <a name="see-also"></a>Viz také

[Mapy zpráv](../../mfc/reference/message-maps-mfc.md)<br/>
[Obslužné rutiny pro zprávy WM_](../../mfc/reference/handlers-for-wm-messages.md)

