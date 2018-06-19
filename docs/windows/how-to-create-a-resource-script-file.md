---
title: 'Postupy: vytvoření souboru skriptu prostředků | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rc files, creating
- .rc files, creating
- resource script files, creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a15352640a39ff6adc3b5a956a1f32c9fd414272
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875520"
---
# <a name="how-to-create-a-resource-script-file"></a>Postupy: Vytvoření souboru skriptu prostředků
> [!NOTE]
>  Editor prostředků není ve verzích Express k dispozici.  
>   
>  Tomto materiálu se vztahuje na aplikací klasické pracovní plochy Windows. Projekty v jazycích technologie .NET nepoužívají soubory skriptu prostředků. V tématu [soubory prostředků](../windows/resource-files-visual-studio.md), další informace.  
  
### <a name="to-create-a-new-resource-script-rc-file"></a>Vytvoření nového souboru skriptu prostředků (.rc)  
  
1.  Přesuňte fokus na složku existujícího projektu v `Solution Explorer`, například na „MyProject“.  
  
    > [!NOTE]
    >  Nepleťte si složku projektu se složkou Řešení v Průzkumníku řešení. Pokud přesunout zaměření na složku řešení, vaše volby v **přidat novou položku** dialogové okno (v kroku 3) se budou lišit.  
  
2.  Na **projektu** nabídce klikněte na tlačítko **přidat novou položku**.  
  
3.  V **přidat novou položku** dialogové okno, klikněte **Visual C++** zvolte složku **soubor zdrojů (.)** v pravém podokně.  
  
4.  Zadejte název souboru skriptu prostředků v **název** textové pole a pak klikněte na **otevřete**.  
  
 Teď můžete [vytvořit](../windows/how-to-create-a-resource.md) a přidejte nové prostředky do souboru .rc.  
  
> [!NOTE]
>  Skript prostředků (soubor .rc) lze přidat pouze do existujícího projektu, který je načten do vývojového prostředí (IDE) pro Visual Studio. Nelze vytvořit samostatný soubor .rc (mimo projekt). [Šablony prostředků](../windows/how-to-use-resource-templates.md) (soubory .rct) lze kdykoli vytvořit.  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)