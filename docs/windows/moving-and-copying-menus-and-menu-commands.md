---
title: Přesouvání a kopírování nabídek a příkazů nabídky (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
ms.assetid: 1d8df535-9922-4579-a9c2-37aeac1856eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b12d9d09cd2e4b35c458c2acbefa48eee8c4b0a9
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44312754"
---
# <a name="moving-and-copying-menus-and-menu-commands"></a>Přesouvání a kopírování nabídek a příkazů nabídky

Mohou přesunout nebo kopírovat nabídek a příkazů nabídky pomocí přetahování myší metody nebo pomocí příkazů v místní nabídce (klikněte pravým tlačítkem na nabídky).

### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>Chcete přesunout nebo kopírovat nabídek nebo příkazů nabídky pomocí přetahování myší – metoda

1. Přetáhněte nebo zkopírujte položku, kterou chcete přejít na:

   - Nové umístění v nabídce aktuální.

   - Jiné nabídky. (Můžete přejít na jiné nabídky přetažením ukazatele myši nad nimi.)

2. Příkaz nabídky vyřaďte, když se vykreslilo vodítko ukazatele zobrazuje umístění, které chcete.

### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>Chcete přesunout nebo kopírovat nabídek nebo příkazů nabídky pomocí místní nabídky příkazů

1. Klikněte pravým tlačítkem na jeden nebo více nabídek nebo příkazů nabídky.

2. V místní nabídce zvolte **Vyjmout** (k přesunutí) nebo **kopírování**.

3. Pokud přecházíte na jiné nabídky položky prostředku nebo souboru skriptu prostředků [otevřete ho v jiném okně](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

4. Vyberte nabídky nebo příkaz nabídky, že kterou chcete přesunout nebo kopírovat do umístění.

5. V místní nabídce zvolte **vložit**. Položka přesunutý nebo zkopírovaný je umístěn před položku, kterou jste vybrali.

   > [!NOTE]
   > Můžete také přetáhnout, zkopírujte a vložte jiným nabídkám v jiných oknech nabídky.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům zobrazení statických prostředků a přiřazování prostředků řetězců pro vlastnosti.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor nabídek](../windows/menu-editor.md)