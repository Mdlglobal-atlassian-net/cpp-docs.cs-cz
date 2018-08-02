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
ms.openlocfilehash: 90a470aa5bb1b24ab2fe549f098a83c29e5d0828
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464146"
---
# <a name="adding-or-deleting-a-string"></a>Přidání nebo odstranění řetězce
Můžete rychle vložit nové položky do tabulky řetězců pomocí editoru řetězců. Nové řetězce jsou umístěny na konci v tabulce a jsou uvedeny další k dispozici identifikátor. Potom můžete upravit vlastnosti ID, hodnotu a popisek v [okno vlastností](/visualstudio/ide/reference/properties-window) podle potřeby.  
  
 Editor řetězců je zajištěno, že je velmi riskantní používat ID, které se už používá. Pokud vyberete ID už používá, editor řetězců oznámíme vám to a pak přiřaďte obecný jedinečné ID, například IDS_STRING58113.  
  
### <a name="to-add-a-string-table-entry"></a>Přidání položky tabulky řetězců  
  
1.  Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Klikněte pravým tlačítkem v rámci tabulky řetězců a zvolte **nový řetězec** z místní nabídky.  
  
3.  V **řetězec** editoru, vyberte možnost **ID** z rozevíracího seznamu ID nebo typ ID přímo v místě.  
  
4.  Upravit **hodnota**, v případě potřeby.  
  
5.  Zadejte položku pro **titulek**.  
  
    > [!NOTE]
    >  Řetězce s hodnotou Null nejsou povoleny v tabulkách řetězců Windows. Pokud vytvoříte položku v tabulce řetězec, který je prázdný řetězec, zobrazí se zpráva s výzvou k "Prosím zadejte řetězec pro tuto položku tabulky."  
  
### <a name="to-delete-a-string-table-entry"></a>Chcete-li odstranit položky tabulky řetězců  
  
1.  Vyberte položku, kterou chcete odstranit.  
  
2.  Na **upravit** nabídky, klikněte na tlačítko **odstranit**.  
  
 \- nebo –  
  
-   Klikněte pravým tlačítkem na řetězec, který chcete odstranit a zvolit **odstranit** z místní nabídky.  
  
 \- nebo –  
  
-   Stisknutím klávesy **odstranit** klíč.  
  
 Informace o přidávání prostředků do spravovaných projektů (těch, které se zaměřují na modul common language runtime), najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *příručce vývojáře v rozhraní .NET Framework.* Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) a [Návod: použití prostředků for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor řetězce](../windows/string-editor.md)   