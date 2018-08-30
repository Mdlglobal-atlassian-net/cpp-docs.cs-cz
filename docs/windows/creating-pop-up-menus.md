---
title: Vytváření místních nabídek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- context menus, Menu Editor
- pop-up menus, creating
- menus, pop-up
- menus, creating
- shortcut menus, creating
- pop-up menus, displaying
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b06fa02420b70538faa70b24137df634420dd8d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222641"
---
# <a name="creating-pop-up-menus"></a>Vytváření místních nabídek

[Místní nabídky](../mfc/menus-mfc.md) zobrazení často používané příkazy. Můžou být závislá na kontextu do umístění ukazatele. Pomocí místní nabídky v aplikaci vyžaduje vytváření samotné nabídky a následným připojením ke kódu aplikace.

Po vytvoření prostředku nabídky kódu aplikace potřebuje k načtení prostředku nabídky a použít [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) způsobit v nabídce Zobrazit. Jakmile uživatel má Zavře rozbalovací nabídky po kliknutí mimo něj nebo klikl na příkaz, že funkce vrátí. Pokud uživatel vybere příkaz, tento příkaz se pošle zpráva v okně, jehož popisovač byl předán.

### <a name="to-create-a-pop-up-menu"></a>Chcete-li vytvořit místní nabídky

1. [Vytvořit nabídku](../windows/creating-a-menu.md) s prázdný název (neposkytují **titulek**).

2. [Přidání příkazu nabídky do nové nabídky](../windows/adding-commands-to-a-menu.md). Přesunout na první příkaz nabídky pod názvem prázdné nabídky (říká dočasné titulek `Type Here`). Zadejte **titulek** a další informace.

   Tento postup opakujte pro další příkazy nabídky v místní nabídce.

3. Uložte prostředek nabídky.

   > [!TIP]
   > Další informace o zobrazení místní nabídky, naleznete v tématu [zobrazení nabídky jako místní nabídky](../windows/viewing-a-menu-as-a-pop-up-menu.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Připojení místní nabídky k aplikaci](../windows/connecting-a-pop-up-menu-to-your-application.md)  
[Editor nabídek](../windows/menu-editor.md)