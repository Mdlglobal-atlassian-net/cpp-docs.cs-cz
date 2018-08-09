---
title: Přidat prostředek – dialogové okno | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.insertresource
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], adding
- Add Resource dialog box
ms.assetid: e9fb6967-738f-47e8-ab58-728cf35b3af0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc7826b10e822b833b7a0a9361d55f74da46342a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651688"
---
# <a name="add-resource-dialog-box"></a>Dialogové okno Přidat prostředek
Použijte toto dialogové okno Přidat prostředky do projektu aplikace klasické pracovní plochy Windows C++.  
  
> [!NOTE]
>  Tyto informace se nevztahují na prostředky v aplikacích pro univerzální platformu Windows. Další informace o tom najdete v tématu [prostředků aplikace a systém správy zdrojů](/windows/uwp/app-resources/).  
  
### <a name="resource-type"></a>Typ prostředku 
 Určuje typ prostředku, který chcete vytvořit.  
  
 Lze rozbalit kategorie prostředků kurzoru a dialogového okna, čímž odhalíte další prostředky. Tyto prostředky jsou umístěny v ...\Microsoft Visual Studio `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Pokud přidáte soubory .rct, je nutné umístit do tohoto adresáře nebo je nutné zadat [zahrnout cestu](../windows/how-to-specify-include-directories-for-resources.md) pro ně. Prostředky v těchto souborech se potom objeví na druhé úrovni pod příslušnou kategorií. Počet souborů .rct, které lze přidat, není nijak omezen.  
  
 Prostředky zobrazené na nejvyšší úrovni stromové struktury jsou výchozí prostředky, které jsou k dispozici v systému Visual Studio.  
  
### <a name="new"></a>Nový
 Vytvoří prostředek v závislosti na typu, který jste vybrali v **typ prostředku** pole. Prostředek se otevře ve vhodném editoru. Například pokud vytvoříte prostředek dialogového okna, otevře se v [editoru dialogového okna](../windows/dialog-editor.md).  
  
### <a name="import"></a>Importovat
 Otevře **importovat** dialogovému oknu, ve kterém můžete přejít k prostředku můžete chtít importovat do aktuálního projektu. Lze importovat bitmapy, ikony, kurzory, soubory prostředků v jazyce HTML, soubory zvukových prostředků (.WAV) nebo soubory vlastních prostředků.  
  
### <a name="custom"></a>Vlastní
 Otevře [nový vlastní prostředek – dialogové okno](../windows/new-custom-resource-dialog-box.md) ve kterém můžete vytvářet vlastní prostředek. Vlastní prostředky lze upravovat pouze v binárním editoru.  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření prostředku](../windows/how-to-create-a-resource.md)