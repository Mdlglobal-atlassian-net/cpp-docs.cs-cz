---
title: Přiřazení příkazu nabídky ke klávese akcelerátoru (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
ms.openlocfilehash: c68d391d1046ab1d1af2fcf54b43b25a7aa9a237
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478322"
---
# <a name="associating-a-menu-command-with-an-accelerator-key-c"></a>Přiřazení příkazu nabídky ke klávese akcelerátoru (C++)

Jsou často časy, kdy má příkaz nabídky a kombinace kláves stejný příkaz programu. Můžete to provést pomocí **nabídky** editor přiřadit stejný identifikátor prostředku pro příkaz nabídky a záznam v tabulce akcelerátorů vaší aplikace. Pak upravíte [titulek](../windows/menu-command-properties.md) příkazu nabídky, aby se zobrazil název klíče akcelerátoru.

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Pro přiřazení příkazu nabídky klávese akcelerátoru

1. V **nabídky** editoru vyberte požadovaný příkaz nabídky.

2. V [okno vlastností](/visualstudio/ide/reference/properties-window), přidejte název klíče akcelerátoru k **titulek** vlastnost:

   - Po popisek nabídky zadejte řídicí sekvence pro kartu (\t), takže všechno, co jsou klávesové zkratky v nabídce vlevo.

   - Zadejte název modifikační klávesa (**Ctrl**, **Alt**, nebo **Shift**) následované znakem plus (**+**) a název, písmeno, nebo symbol Další klíč.

       Například chcete přiřadit **Ctrl**+**O** k **otevřít** příkaz **souboru** nabídky, změnit příkazu nabídky  **Titulek** tak, aby vypadal takto:

        ```
        &Open...\tCtrl+O
        ```

       Příkaz nabídky v **nabídky** editoru se aktualizuje tak, aby odrážely nový popisek během psaní.

3. [Vytvoření položky tabulky akcelerátorů](../windows/adding-an-entry-to-an-accelerator-table.md) v **akcelerátoru** editoru a přiřaďte ho stejný identifikátor jako příkaz nabídky. Pomocí kombinace kláves, která si myslíte, že bude snadno pamatovat.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Přidání komentářů k nabídce](../windows/adding-commands-to-a-menu.md)<br/>
[Editor nabídek](../windows/menu-editor.md)