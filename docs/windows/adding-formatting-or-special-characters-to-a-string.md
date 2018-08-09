---
title: Přidání formátovacích nebo speciálních znaků do řetězce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8ccfe36f4bbd14856b25d18bc83339ece2e98801
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644778"
---
# <a name="adding-formatting-or-special-characters-to-a-string"></a>Přidání formátovacích nebo speciálních znaků do řetězce
### <a name="to-add-formatting-or-special-characters-to-a-string"></a>Přidání formátovacích nebo speciálních znaků do řetězce  
  
1.  Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Vyberte řetězec, který chcete upravit.  
  
3.  V [okno vlastností](/visualstudio/ide/reference/properties-window), přidejte všechny standardní řídicí sekvence, které tady textu **titulek** pole a stiskněte klávesu **Enter**.  
  
    |Chcete-li získat tento|Zadejte toto|  
    |-----------------|---------------|  
    |Nový řádek|\n|  
    |Návrat na začátek řádku|\r|  
    |Tabulátor|\t|  
    |Zpětné lomítko (\\)|\\\|  
    |Znak ASCII|\ddd (osmičkové soustavě)|  
    |upozornění (zvonek)|\a|  
  
> [!NOTE]
>  **Řetězec** editor nepodporuje kompletní řídicí znaky ASCII. Můžete použít pouze ty uvedené výše.  
  
 Informace o přidávání prostředků do spravovaných projektů (těch, které se zaměřují na modul common language runtime), najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) a [Návod: použití prostředků for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="requirements"></a>Požadavky 
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor řetězce](../windows/string-editor.md)   