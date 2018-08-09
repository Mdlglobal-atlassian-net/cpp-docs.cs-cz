---
title: Úprava částí obrázku (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1880853c63a236e824f9b59156181dccb2bba819
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647443"
---
# <a name="editing-parts-of-an-image-image-editor-for-icons"></a>Úprava částí obrázku (editor obrázků pro ikony)
Můžete provádět standardní operace úprav – vyjmutí, kopírování, vymazání a přesouvání – na [výběr](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), zda je výběr celého obrázku nebo jen jeho části. Protože **Image** editor používá **schránky Windows**, můžou přenášet imagí mezi **Image** editoru a dalšími aplikacemi pro Windows.  
  
 Kromě toho můžete změnit velikost výběru, zda obsahuje celého obrázku nebo jen část.  
  
### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Vyjmout aktuálního výběru a přesunout ho do schránky.  
  
1.  Klikněte na tlačítko **Vyjmout** na **upravit** nabídky.  
  
### <a name="to-copy-the-selection"></a>Kopírovat výběr  
  
1.  Umístěte ukazatel uvnitř ohraničení výběru nebo kdekoli na něm s výjimkou úchyty pro změnu velikosti.  
  
2.  Podržte stisknutou klávesu **Ctrl** klíče při přetahování výběr do nového umístění. Obsah původního výběru je beze změny.  
  
3.  Zkopíruje výběr do bitové kopie v daném umístění, klikněte na tlačítko vně výběr kurzoru.  
  
### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Chcete-li vložit obsah schránky do bitové kopie  
  
1.  Z **upravit** nabídce zvolte **vložit**.  
  
     Obsah schránky obklopený ohraničení výběru se zobrazí v levém horním rohu podokna.  
  
2.  Umístěte ukazatel myši v rámci ohraničení výběru a přetáhněte ji na obrázku do požadovaného umístění na obrázku.  
  
3.  Pokud chcete ukotvit bitové kopie v jeho novém umístění, klikněte na tlačítko mimo hranice výběru.  
  
### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Chcete-li odstranit aktuální výběr bez přesouvání do schránky.  
  
1.  Z **upravit** nabídce zvolte **odstranit**.  
  
     Původní oblast výběru se vyplní aktuální barvou pozadí.  
  
    > [!NOTE]
    >  Můžete přistupovat **Vyjmout**, **kopírování**, **vložit**, a **odstranit** příkazy kliknutím pravým tlačítkem v **zobrazení prostředků** okna.  
  
### <a name="to-move-the-selection"></a>Chcete-li přesunout výběr  
  
1.  Umístěte ukazatel uvnitř ohraničení výběru nebo kdekoli na něm s výjimkou úchyty pro změnu velikosti.  
  
2.  Přetáhněte do nového umístění.  
  
3.  Chcete-li ukotvit výběr obrázku v jeho novém umístění, klikněte na tlačítko mimo hranice výběru.  
  
 Další informace o vykreslování s výběrem, naleznete v tématu [vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)