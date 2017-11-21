---
title: "Přidat prostředek – dialogové okno | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.insertresource
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio], adding
- Add Resource dialog box
ms.assetid: e9fb6967-738f-47e8-ab58-728cf35b3af0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d210ea66faa89023dcdcfb914ca423086d6eddb1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="add-resource-dialog-box"></a>Dialogové okno Přidat prostředek
Pomocí tohoto dialogového okna Přidat prostředky do projektu aplikace pracovní plochy C++ Windows.  
  
> [!NOTE]
>  Tato informace se nevztahují k prostředkům v aplikacích pro Windows Store. Další informace o, najdete v tématu [definování prostředky aplikace](http://msdn.microsoft.com/en-us/476ea844-632c-4467-9ce3-966be1350dd4).  
  
 **Typ prostředku**  
 Určuje typ prostředku, který chcete vytvořit.  
  
 Lze rozbalit kategorie prostředků kurzoru a dialogového okna, čímž odhalíte další prostředky. Tyto prostředky jsou umístěny v sadě Visual Studio ...\Microsoft `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Pokud přidáte soubory .rct, je nutné umístit v tomto adresáři nebo je nutné zadat [obsahovat cestu](../windows/how-to-specify-include-directories-for-resources.md) pro ně. Prostředky v těchto souborech se potom objeví na druhé úrovni pod příslušnou kategorií. Počet souborů .rct, které lze přidat, není nijak omezen.  
  
 Prostředky zobrazené na nejvyšší úrovni stromové struktury jsou výchozí prostředky, které jsou k dispozici v systému Visual Studio.  
  
 **Nový**  
 Vytvoří prostředek na základě výběru v typu **typ prostředku** pole. Prostředek se otevře ve vhodném editoru. Například pokud vytvoříte zdroj dialogového okna, otevře se v [editoru dialogového okna](../windows/dialog-editor.md).  
  
 **Import**  
 Otevře se **importovat** dialogové, ve kterém můžete přejít na prostředek, můžete chtít importovat do aktuálního projektu. Lze importovat bitmapy, ikony, kurzory, soubory prostředků v jazyce HTML, soubory zvukových prostředků (.WAV) nebo soubory vlastních prostředků.  
  
 **Vlastní**  
 Otevře se [dialogové okno Nový vlastní prostředek](../windows/new-custom-resource-dialog-box.md) ve kterém můžete vytvořit vlastní prostředek. Vlastní prostředky lze upravovat pouze v binárním editoru.  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření prostředku](../windows/how-to-create-a-resource.md)