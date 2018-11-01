---
title: Připojení místní nabídky do vaší aplikace C++
ms.date: 11/04/2016
helpviewer_keywords:
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- menus [C++], pop-up
- shortcut menus [C++], connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
ms.openlocfilehash: 8a0cb64caaa58b464b0d5abb52093350c5e3cfeb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556491"
---
# <a name="connecting-a-pop-up-menu-to-your-c-application"></a>Připojení místní nabídky do vaší aplikace C++

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>Pro připojení místní nabídky k aplikaci

1. Přidání obslužné rutiny zpráv pro WM_CONTEXTMENU (například). Další informace najdete v tématu [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

2. Přidejte následující kód do obslužné rutiny zpráv:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md) předané ve zprávě je obslužná rutina v souřadnicovém systému obrazovky.

## <a name="requirements"></a>Požadavky

MFC

## <a name="see-also"></a>Viz také

[Vytváření místních nabídek](../windows/creating-pop-up-menus.md)<br/>
[Editor nabídek](../windows/menu-editor.md)