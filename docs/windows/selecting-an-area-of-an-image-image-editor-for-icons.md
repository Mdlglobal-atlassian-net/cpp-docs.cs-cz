---
title: "Výběr oblasti obrázku (Editor obrázků pro ikony) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.image.editing
dev_langs: C++
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 02caf907ae59251a3a8988eeb5bd8e3269cd855b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="selecting-an-area-of-an-image-image-editor-for-icons"></a>Výběr oblasti obrázku (editor obrázků pro ikony)
Nástroje pro výběr můžete definovat oblast bitovou kopii, kterou chcete vyjmout, kopírovat, vymazat, změnit velikost, Invertovat nebo přesunout. Pomocí **obdélníku výběru** nástroj můžete definovat a vyberte obdélníkovou oblast bitové kopie. S **nestandardní výběr** nástroj může kreslení od ruky outline oblasti, kterou chcete vybrat pro vyjmutí, kopírování, nebo jiné operace.  
  
> [!NOTE]
>  Najdete v článku **obdélníku výběru** a **nestandardní výběr** nástroje na obrázku [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) nebo zobrazit popisy přidružené každé tlačítko na **Editor obrázků** panelu nástrojů.  
  
 Můžete také vytvořit vlastního štětce z výběru. Další informace najdete v tématu [vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
### <a name="to-select-an-area-of-an-image"></a>Vyberte oblast obrázku  
  
1.  Na **Editor obrázků** panelu nástrojů (nebo z **bitové kopie** nabídce **nástroje** příkaz), klikněte na tlačítko chcete nástroj pro výběr.  
  
2.  Přesuňte kurzor na roh oblast, která chcete vybrat. Když je kurzor přes bitovou kopii, zobrazí se zaměřovacím.  
  
3.  Přetáhněte kurzor na opačné rohu oblasti, kterou chcete vybrat. Obdélníku ukazuje, jaké pixelů bude vybrána. Všechny pixelů v obdélníku, včetně těch, které v obdélníku, jsou zahrnuty ve výběru.  
  
4.  Uvolnění tlačítka myši. Hranice výběru uzavře vybrané oblasti.  
  
### <a name="to-select-an-entire-image"></a>Chcete-li vybrat celého obrázku  
  
1.  Kliknutím na obrázek mimo aktuální výběr. Hranice výběru změní fokus a zahrnuje celou bitovou kopii znovu.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Požadavky  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)

