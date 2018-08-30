---
title: Přidání nebo odstranění řetězce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], adding to string tables
- string tables, deleting strings
- strings [C++], deleting in string tables
- string tables, adding strings
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 952531a846fe48e9f093f016efd67d73c386d82c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204484"
---
# <a name="adding-or-deleting-a-string"></a>Přidání nebo odstranění řetězce

Můžete rychle vkládat nové položky do řetězce pomocí tabulky **řetězec** editoru. Nové řetězce jsou umístěny na konci v tabulce a jsou uvedeny další k dispozici identifikátor. Potom můžete upravit **ID**, **hodnotu**, nebo **titulek** vlastnosti v [okno vlastností](/visualstudio/ide/reference/properties-window) podle potřeby.

**Řetězec** editor zajišťuje, je velmi riskantní používat ID, které se už používá. Pokud vyberete ID už používá, **řetězec** oznámíme vám to a zařaďte obecné jedinečné ID, například editor `IDS_STRING58113`.

### <a name="to-add-a-string-table-entry"></a>Přidání položky tabulky řetězců

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](../windows/resource-view-window.md).

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. Klikněte pravým tlačítkem v rámci tabulky řetězců a zvolte **nový řetězec** z místní nabídky.

3. V **řetězec** editoru, vyberte možnost **ID** z rozevíracího seznamu ID nebo typ ID přímo v místě.

4. Upravit **hodnota**, v případě potřeby.

5. Zadejte položku pro **titulek**.

   > [!NOTE]
   > Řetězce s hodnotou Null nejsou povoleny v tabulkách řetězců Windows. Pokud vytvoříte položku v tabulce řetězec, který je prázdný řetězec, zobrazí se zpráva s výzvou k "Prosím zadejte řetězec pro tuto položku tabulky."

### <a name="to-delete-a-string-table-entry"></a>Chcete-li odstranit položky tabulky řetězců

1. Vyberte položku, kterou chcete odstranit.

2. Na **upravit** nabídky, klikněte na tlačítko **odstranit**.

\- nebo –

- Klikněte pravým tlačítkem na řetězec, který chcete odstranit a zvolit **odstranit** z místní nabídky.

\- nebo –

- Stisknutím klávesy **odstranit** klíč.

Informace o přidávání prostředků do spravovaných projektů (těch, které se zaměřují na modul common language runtime), najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor řetězce](../windows/string-editor.md)  