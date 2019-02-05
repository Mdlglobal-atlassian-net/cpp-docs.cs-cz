---
title: Vytvoření dialogového okna (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: 928432000fb9a6347433b78b224e15f07ce810d2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742645"
---
# <a name="creating-a-dialog-box-c"></a>Vytvoření dialogového okna (C++)

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-new-dialog-box"></a>K vytvoření nového dialogového okna

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a pak zvolte **přidat prostředek** z místní nabídky.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. V **přidat prostředek** dialogu **dialogové okno** v **typ prostředku** seznamu a pak zvolte **nový**.

   Pokud symbol plus (**+**) se zobrazí vedle **dialogové okno** typ prostředku, znamená to, že pole šablon dialogového okna jsou k dispozici. Vyberte znaménko plus rozbalit seznam šablon, vyberte šablonu a zvolte **nový**.

   Otevře se dialogové okno Nový v **dialogové okno** editoru.

   Můžete také [otevřete existující dialogových oknech v editoru dialogové okno pro úpravy](../windows/viewing-and-editing-resources-in-a-resource-editor.md).

## <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Chcete-li vytvořit dialogové okno, které uživatel nemohou zavřít.

Můžete vytvořit modul runtime dialogové okno, které uživatel nemůže ukončeno. Tento druh dialogové okno je užitečný pro přihlášení a pro aplikace nebo dokumentu zámky.

1. V **vlastnosti** podokno pro dialogové okno, nastavte **systémové nabídky** vlastnost **false**.

   Toto nastavení zakáže nabídky systému dialogového a **Zavřít** tlačítko.

1. V dialogovém okně pole formuláře, odstraňte **zrušit** a **OK** tlačítka.

   V době běhu nemůže uživatel ukončit modální dialogové okno, které má tyto vlastnosti.

Pokud chcete povolit testování tohoto druhu dialogového okna, test dialog box – funkce zjistí při **Esc** stisknutí. (**Esc** se také označuje jako virtuální vk_escape – klíč.) Bez ohledu na to, jak je určen dialogovém okně chování za běhu, můžete testovací režim ukončit stisknutím kombinace kláves **Esc**.

> [!NOTE]
> Pro aplikace knihovny MFC, chcete-li vytvořit dialogové okno, které uživatelé nebudou moct zavřít, je nutné přepsat výchozí chování `OnOK` a `OnCancel` vzhledem k tomu, že i v případě, že odstraníte přidružené tlačítka, dialogové okno může stále vynechat stisknutím klávesy  **Zadejte** nebo **Esc**.

Informace o tom, jak přidat prostředky do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Postupy: Vytvoření prostředku](../windows/how-to-create-a-resource.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editor dialogových oken](../windows/dialog-editor.md)