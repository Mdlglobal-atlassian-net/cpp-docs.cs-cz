---
title: Připojení místní nabídky do vaší aplikace C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- menus [C++], pop-up
- shortcut menus [C++], connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e9a5123481999328e8d3e010f752a27ecef27557
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313270"
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

[Vytváření místních nabídek](../windows/creating-pop-up-menus.md)  
[Editor nabídek](../windows/menu-editor.md)  