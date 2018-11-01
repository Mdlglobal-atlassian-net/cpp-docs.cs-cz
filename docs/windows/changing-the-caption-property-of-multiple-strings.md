---
title: Změna vlastnosti titulku více řetězců prostředků (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
ms.assetid: 82ac4389-fd9c-4794-a18f-c6bf5b253bd7
ms.openlocfilehash: a0b658684a948bd006c392188ed650756bda297d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530829"
---
# <a name="changing-the-caption-property-of-multiple-string-resources-c"></a>Změna vlastnosti titulku více řetězců prostředků (C++)

Následující postup ukazuje, jak změnit vlastnosti titulku vícenásobných řetězců.

### <a name="to-change-the-caption-property-of-multiple-strings"></a>Změna vlastnosti titulku vícenásobných řetězců

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](../windows/resource-view-window.md).

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. Vyberte řetězců, které chcete změnit současným **Ctrl** klíče při klepnutí na každé z nich.

3. V [okno vlastností](/visualstudio/ide/reference/properties-window), zadejte novou hodnotu pro vlastnost, kterou chcete změnit.

4. Stisknutím klávesy **zadejte**.

Informace o přidávání prostředků do spravovaných projektů (těch, které se zaměřují na modul common language runtime), najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor řetězce](../windows/string-editor.md)