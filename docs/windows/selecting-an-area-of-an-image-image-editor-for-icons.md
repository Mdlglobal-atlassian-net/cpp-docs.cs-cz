---
title: Výběr oblasti obrázku (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.editing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ed8669a22be7e1a2b696ca9373c30e71f17c191
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012680"
---
# <a name="selecting-an-area-of-an-image-image-editor-for-icons"></a>Výběr oblasti obrázku (editor obrázků pro ikony)
Nástroje pro výběr můžete použít k definování oblast bitovou kopii, kterou chcete vyjmout, kopírovat, zrušte, změna velikosti, Invertovat nebo přesunout. S **obdélníku výběru** nástroje můžete definovat a vyberte obdélníkovou oblast obrázku. S **Volný výběr** nástroj od ruky obrys oblasti, kterou chcete vybrat pro vyjmutí, kopírování nebo jiné operace můžete nakreslit.  
  
> [!NOTE]
>  Najdete v článku **obdélníku výběru** a **Volný výběr** nástroje na obrázku [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) nebo zobrazení popisů tlačítek spojených s každé tlačítko na **Editor obrázků** nástrojů.  
  
 Můžete také vytvořit vlastní štětec z výběru. Další informace najdete v tématu [vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
### <a name="to-select-an-area-of-an-image"></a>Vyberte oblast obrázku  
  
1.  Na **Editor obrázků** nástrojů (nebo z **Image** nabídce **nástroje** příkaz), klikněte na nástroj pro výběr chcete.  
  
2.  Přesuňte bod vložen do jednoho rohu oblast obrázku, který chcete vybrat. Mezi vlasy se zobrazí po kurzoru nad bitovou kopii.  
  
3.  Přetáhněte kurzor protilehlého rohu oblasti, kterou chcete vybrat. Obdélník ukazuje, jaké pixelů bude vybrána. Všechny obrazové body v obdélníku, včetně těch v obdélníku, jsou zahrnuté ve výběru.  
  
4.  Uvolněte tlačítko myši. Ohraničení výběru obklopuje vybrané oblasti.  
  
### <a name="to-select-an-entire-image"></a>K výběru celého obrázku  
  
1.  Kliknutím na obrázek mimo aktuální výběr. Ohraničení výběru změní fokus a zahrnuje celou image ještě jednou.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)