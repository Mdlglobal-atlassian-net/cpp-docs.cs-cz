---
title: "Přidání formátovacích nebo speciálních znaků do řetězce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ca91ef9742f2dfb10a0af12c74ca58f80035d131
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-formatting-or-special-characters-to-a-string"></a>Přidání formátovacích nebo speciálních znaků do řetězce
### <a name="to-add-formatting-or-special-characters-to-a-string"></a>Přidání formátovacích nebo speciálních znaků do řetězce  
  
1.  Otevřít tabulku řetězec poklepáním na ikonu v [zobrazení prostředků](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Vyberte řetězec, který chcete upravit.  
  
3.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window), přidejte všechny standardní řídicí sekvence níže uvedené na text v **popisek** pole a stiskněte klávesu **ENTER**.  
  
    |Chcete-li získat to|Tento typ|  
    |-----------------|---------------|  
    |Nový řádek|\n|  
    |Návrat na začátek řádku|\r|  
    |Tabulátor|\t|  
    |Zpětné lomítko (\\)|\\\|  
    |Znaků ASCII|\ddd (osmičková zápis)|  
    |Výstraha (zvonku)|\a|  
  
> [!NOTE]
>  Editor řetězce nepodporuje kompletní uvozovacími znaky ASCII, znak. Můžete použít pouze ty uvedené výše.  
  
 Informace o přidávání zdrojů do spravovaných projekty (ty, které cílí modul common language runtime), najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace o ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a prostředky řetězce přiřazení k vlastnosti, najdete v části [návod: lokalizace Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) a [Návod: použití zdrojů pro lokalizaci s technologií ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor řetězce](../windows/string-editor.md)   

