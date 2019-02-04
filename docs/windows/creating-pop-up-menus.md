---
title: Vytváření místních nabídek (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
ms.openlocfilehash: cf2e3578f49cb6b4af8797052273211f699a6b4f
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702827"
---
# <a name="creating-pop-up-menus-c"></a>Vytváření místních nabídek (C++)

[Místní nabídky](../mfc/menus-mfc.md) zobrazení často používané příkazy. Můžou být závislá na kontextu do umístění ukazatele. Pomocí místní nabídky v aplikaci vyžaduje vytváření samotné nabídky a následným připojením ke kódu aplikace.

Po vytvoření prostředku nabídky, kód vaší aplikace potřebuje k načtení prostředku nabídky a použít [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) způsobit v nabídce Zobrazit. Jakmile uživatel má vynechat v rozbalovací nabídce vyberete mimo něj, nebo má vybraný příkaz, který funkce vrátí. Pokud uživatel vybere příkaz, tento příkaz se pošle zpráva v okně, jehož popisovač byl předán.

## <a name="to-create-a-pop-up-menu"></a>Chcete-li vytvořit místní nabídky

1. [Vytvořit nabídku](../windows/creating-a-menu.md) s prázdný název (neposkytují **titulek**).

1. [Přidání příkazu nabídky do nové nabídky](../windows/adding-commands-to-a-menu.md). Přesunout na první příkaz nabídky pod názvem prázdné nabídky (říká dočasné titulek `Type Here`). Zadejte **titulek** a další informace.

   Tento postup opakujte pro další příkazy nabídky v místní nabídce.

1. Uložte prostředek nabídky.

## <a name="to-connect-a-pop-up-menu-to-your-application"></a>Pro připojení místní nabídky k aplikaci

1. Přidání obslužné rutiny zpráv pro WM_CONTEXTMENU (například). Další informace najdete v tématu [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

1. Přidejte následující kód do obslužné rutiny zpráv:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md) předané ve zprávě je obslužná rutina v souřadnicovém systému obrazovky.

   > [!NOTE]
   > Připojení místní nabídky k aplikaci vyžaduje knihovny MFC.

## <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>Chcete-li zobrazit prostředku nabídky jako místní nabídky

Obvykle, když pracujete v **nabídky** editoru, prostředku nabídky se zobrazí jako panel nabídek. Může však mít prostředky nabídky, které jsou přidány do řádku nabídek aplikace, zatímco program běží.

Klikněte pravým tlačítkem na nabídku a zvolte **zobrazit jako místní nabídku** z místní nabídky.

   Tato možnost je pouze zobrazení prioritní a nezmění vaši nabídku.

   > [!NOTE]
   > Chcete-li změnit zpět na zobrazení řádku nabídek klikněte na tlačítko **zobrazit jako místní nabídku** znovu (který odstraněn znak zaškrtnutí barvy a vrátí zobrazení řádku nabídek).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor nabídek](../windows/menu-editor.md)
