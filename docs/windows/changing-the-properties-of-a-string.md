---
title: Změna vlastností prostředku řetězce (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
ms.assetid: 0a220434-f444-4405-9a64-d28d6b965687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cfd55cbb67bc62760fba26f098a772d62042ea88
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081991"
---
# <a name="changing-the-properties-of-a-string-resource-c"></a>Změna vlastností prostředku řetězce (C++)

### <a name="to-change-a-string-or-its-identifier"></a>Chcete-li změnit její identifikátor nebo řetězec

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](../windows/resource-view-window.md).

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. Vyberte řetězec, který chcete upravit a dvakrát klikněte **ID**, **hodnotu**, nebo **titulek** sloupce. Nyní můžete:

   - Vyberte **ID** z **rozevírací seznam ID** seznamu nebo typu `ID` přímo na místě.

   - Zadejte jiné číslo v **hodnotu** sloupce.

   - Zadejte úpravy v operaci **titulek** sloupce.

        > [!NOTE]
        >  Můžete také upravit vlastnosti řetězce v [okno vlastností](/visualstudio/ide/reference/properties-window).

Informace o přidávání prostředků do spravovaných projektů (těch, které se zaměřují na modul common language runtime), najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor řetězce](../windows/string-editor.md)  