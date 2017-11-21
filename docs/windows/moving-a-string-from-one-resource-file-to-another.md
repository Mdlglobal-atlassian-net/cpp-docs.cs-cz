---
title: "Přesunutí řetězce z jednoho zdrojového souboru do jiného | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- strings [C++], moving between files
- resource script files, moving strings
- string editing, moving strings between resources
- String editor, moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5bac062d954d8cec4c53b7b81af684c9cb16f4f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="moving-a-string-from-one-resource-file-to-another"></a>Přesunutí řetězce z jednoho zdrojového souboru do druhého
### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Přesunutí řetězce ze souboru skriptu jeden prostředek  
  
1.  Tabulky řetězců otevřete v oba soubory .rc. (Další informace najdete v tématu [zobrazení prostředků v prostředků skriptu souboru mimo of projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Klikněte pravým tlačítkem na řetězec, který chcete přesunout a zvolte **Vyjmout** z místní nabídky.  
  
3.  Umístěte kurzor na cíli **Editor řetězce** okno.  
  
4.  V souboru .rc, do které chcete přesunout řetězec, klikněte pravým tlačítkem a zvolte **vložení** z místní nabídky.  
  
    > [!NOTE]
    >  Pokud **ID** nebo **hodnotu** přesunutý řetězec je v konfliktu s existujícím **ID** nebo **hodnotu** v cílovém souboru, buď **ID** nebo **hodnotu** změn přesunutý řetězec. Pokud řetězec existuje se stejným **ID**, **ID** změn přesunutý řetězec. Pokud řetězec existuje se stejným **hodnotu**, **hodnotu** změn přesunutý řetězec.  
  
 Informace o přidávání zdrojů do spravovaných projekty (ty, které cílí modul common language runtime), najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace o ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a prostředky řetězce přiřazení k vlastnosti, najdete v části [návod: lokalizace Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) a [Návod: použití zdrojů pro lokalizaci s technologií ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor řetězce](../windows/string-editor.md)   
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Přizpůsobení rozložení oken](/visualstudio/ide/customizing-window-layouts-in-visual-studio)   

