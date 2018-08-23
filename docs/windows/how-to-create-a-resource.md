---
title: 'Postupy: vytvoření prostředku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [Visual Studio], creating
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d269dbc83c11fa4ece55d8df8f6629d1afd52c03
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594510"
---
# <a name="how-to-create-a-resource"></a>Postupy: Vytvoření prostředku

> [!NOTE]
> **Zobrazení prostředků** není podporováno ve verzích Express.

### <a name="to-create-a-new-resource-in-resource-view"></a>Chcete-li vytvořit nový prostředek v okně zobrazení prostředků

1. Se zaměřením na souboru .rc v [zobrazení prostředků](../windows/resource-view-window.md), klikněte na tlačítko **upravit** nabídku a zvolte **přidat prostředek** (nebo klikněte pravým tlačítkem na soubor .rc v **zobrazení prostředků** a zvolte **přidat prostředek** z místní nabídky).

   > [!NOTE] 
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. V [přidat prostředek – dialogové okno](../windows/add-resource-dialog-box.md), vyberte typ prostředku, které chcete přidat do projektu.

### <a name="to-create-a-new-resource-in-solution-explorer"></a>Chcete-li vytvořit nový prostředek v Průzkumníku řešení

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na složku projektu a zvolte **přidat**, pak klikněte na tlačítko **přidat prostředek** v místní nabídce.

   Pokud jste ještě není soubor .rc v projektu, tento krok ho vytvoří. Opakujte tento krok a přidejte konkrétní typy prostředků do nového souboru .rc.

2. V [přidat prostředek – dialogové okno](../windows/add-resource-dialog-box.md), vyberte typ prostředku, které chcete přidat do projektu.

### <a name="to-create-a-new-resource-in-class-view"></a>Chcete-li vytvořit nový prostředek v zobrazení tříd

1. V [zobrazení tříd](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925), klikněte pravým tlačítkem na vaší třídy a zvolte **přidat**, pak klikněte na tlačítko **přidat prostředek** z místní nabídky.

2. V [přidat prostředek – dialogové okno](../windows/add-resource-dialog-box.md), vyberte typ prostředku, které chcete přidat do projektu.

### <a name="to-create-a-new-resource-from-the-project-menu"></a>Chcete-li vytvořit nový prostředek z nabídky Projekt

1. Z **projektu** nabídce zvolte **přidat prostředek**.

Při vytváření nového prostředku jazyka Visual C++ přiřadí jedinečný název, například `IDD_Dialog1`. Toto ID prostředku lze přizpůsobit úpravou vlastností pro prostředek v editoru přidružený prostředek nebo v [okno vlastností](/visualstudio/ide/reference/properties-window).

Prostředek můžete vytvořit jako nové výchozí prostředek (prostředek, který není založen na šabloně) nebo jako prostředek vzorované po [šablony](../windows/how-to-use-resource-templates.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Editory prostředků](../windows/resource-editors.md)  
[Přidat prostředek – dialogové okno](../windows/add-resource-dialog-box.md)