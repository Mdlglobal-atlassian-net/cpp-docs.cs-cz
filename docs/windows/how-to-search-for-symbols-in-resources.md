---
title: "Postupy: vyhledávání symbolů v prostředcích | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- symbols, finding
- resources [Visual Studio], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 04b2bb47977a349bfd06dc6770aab80626395714
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-search-for-symbols-in-resources"></a>Postupy: Vyhledávání symbolů v prostředcích
### <a name="to-find-symbols-in-resources"></a>Najít symboly v prostředky  
  
1.  Z **upravit** nabídce zvolte **najít Symbol**.  
  
2.  V [najít Symbol – dialogové](http://msdn.microsoft.com/en-us/63e93d9c-784f-418d-a76a-723da5ff5d96)v **najít** pole, v rozevíracím seznamu vyberte předchozí hledaný řetězec nebo zadejte klávesa akcelerátoru, kterou chcete najít (například ID_ACCEL1).  
  
    > [!TIP]
    >  Použít [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) pro hledání, je nutné použít [najít v souborech – příkaz](/visualstudio/ide/reference/find-command) z **upravit** nabídky místo **najít Symbol**příkaz. Chcete-li regulární výrazy, musíte mít **použití: regulární výrazy** v zaškrtnuto políčko [dialogové okno Hledat](http://msdn.microsoft.com/en-us/dad03582-4931-4893-83ba-84b37f5b1600). Pak kliknete tlačítko se šipkou vpravo napravo **najít** pole zobrazíte seznam vyhledávání regulárních výrazů. Když vyberete výrazu z tohoto seznamu, je nahrazena jako hledaný text v **najít** pole.  
  
3.  Vyberte některé z **najít** možnosti.  
  
4.  Klikněte na tlačítko **najít další**.  
  
    > [!NOTE]
    >  Nelze vyhledat symboly v řetězci, akcelerátoru nebo binární prostředky.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace o ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a prostředky řetězce přiřazení k vlastnosti a [návod: použití prostředků pro lokalizaci pomocí technologie ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)   
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)