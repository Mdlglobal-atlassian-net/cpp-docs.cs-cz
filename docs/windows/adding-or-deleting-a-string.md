---
title: "Přidání nebo odstranění řetězce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.string
dev_langs: C++
helpviewer_keywords:
- strings [C++], adding to string tables
- string tables, deleting strings
- strings [C++], deleting in string tables
- string tables, adding strings
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e485e1c689814e63c5a43edba2ded80967d576a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-or-deleting-a-string"></a>Přidání nebo odstranění řetězce
Můžete rychle vložit nové položky do tabulce řetězců pomocí editoru řetězec. Nové řetězce jsou umístěny na konec tabulky a mají k dispozici další identifikátor. Potom můžete upravit vlastnosti ID, hodnota nebo popisek v [vlastnosti – okno](/visualstudio/ide/reference/properties-window) podle potřeby.  
  
 Editor řetězce zajistí, že nepoužíváte ID, které je již používán. Pokud vyberete ID již používán, bude editor řetězce s upozorněním a potom přiřadit obecné jedinečné ID, například IDS_STRING58113.  
  
### <a name="to-add-a-string-table-entry"></a>Chcete-li přidat položku tabulky řetězec  
  
1.  Otevřít tabulku řetězec poklepáním na ikonu v [zobrazení prostředků](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Klikněte pravým tlačítkem do tabulky řetězců a zvolte **nový řetězec** z místní nabídky.  
  
3.  V **řetězec** editor, vyberte možnost **ID** z rozevíracího seznamu ID, nebo zadat na ID přímo v místě.  
  
4.  Upravit **hodnotu**, v případě potřeby.  
  
5.  Zadejte položku pro **popisek**.  
  
    > [!NOTE]
    >  Řetězce Null nejsou povoleny v tabulkách řetězec Windows. Pokud vytvoříte položku v tabulce řetězec, který je řetězec null, obdržíte zprávu s dotazem na "Prosím zadejte řetězec pro tuto položku tabulky."  
  
### <a name="to-delete-a-string-table-entry"></a>Chcete-li odstranit položku tabulky řetězec  
  
1.  Vyberte položku, kterou chcete odstranit.  
  
2.  Na **upravit** nabídky, klikněte na tlačítko **odstranit**.  
  
 \-nebo –  
  
-   Klikněte pravým tlačítkem na řetězec, který chcete odstranit a zvolit **odstranit** z místní nabídky.  
  
 \-nebo –  
  
-   Stiskněte **odstranit** klíč.  
  
 Informace o přidávání zdrojů do spravovaných projekty (ty, které cílí modul common language runtime), najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace o ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a prostředky řetězce přiřazení k vlastnosti, najdete v části [návod: lokalizace Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) a [Návod: použití zdrojů pro lokalizaci s technologií ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor řetězce](../windows/string-editor.md)   

