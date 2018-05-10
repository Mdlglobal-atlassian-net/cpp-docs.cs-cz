---
title: Hledání řetězce | Microsoft Docs
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
- strings [C++], searching
- strings [C++]
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3763baf0f085dc72040ab22c9efd38e8aa8068f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="finding-a-string"></a>Hledání řetězce
Můžete vyhledat jednoho nebo více řetězců v tabulce řetězců a použít [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) s **hledání v souborech** příkazu (**upravit** nabídky) najít všechny instance řetězce odpovídající vzor.  
  
### <a name="to-find-a-string-in-the-string-table"></a>Najít řetězec do tabulky řetězců  
  
1.  Otevřít tabulku řetězec poklepáním na ikonu v [zobrazení prostředků](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Na **upravit** nabídky, klikněte na **najít a nahradit**, zvolte **najít**.  
  
3.  V **najít** pole, v rozevíracím seznamu vyberte předchozí hledaný řetězec nebo zadejte titulek textu nebo prostředku identifikátor řetězce, který chcete najít.  
  
4.  Vyberte některé z **najít** možnosti.  
  
5.  Klikněte na tlačítko **najít další**.  
  
    > [!TIP]
    >  Chcete-li používat regulární výrazy při vyhledávání souborů, použijte **hledání v souborech** příkaz. Zadejte regulární výraz k odpovídá vzorku nebo klikněte na tlačítko napravo **najít** pole zobrazíte seznam vyhledávání regulárních výrazů. Když vyberete výrazu z tohoto seznamu, je nahrazena jako hledaný text v **najít** pole. Pokud používáte regulární výrazy, nezapomeňte **použít: regulární výrazy** je zaškrtnuté políčko.  
  
 Informace o přidávání zdrojů do spravovaných projekty (ty, které cílí modul common language runtime), najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace o ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a prostředky řetězce přiřazení k vlastnosti, najdete v části [návod: lokalizace Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) a [Návod: použití zdrojů pro lokalizaci s technologií ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor řetězce](../windows/string-editor.md)   

