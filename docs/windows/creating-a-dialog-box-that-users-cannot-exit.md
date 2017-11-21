---
title: "Vytváření dialogu, který uživatelé nemohou zavřít. | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes, creating
- modal dialog boxes, logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1992f896baac2748246e8c74ba3abbc2997a95af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-dialog-box-that-users-cannot-exit"></a>Vytvoření dialogového okna, které uživatelé nemohou zavřít.
Můžete vytvořit runtime dialogové okno s uživatele nelze ukončit. Tento druh dialogové okno je užitečný pro přihlášení a pro aplikace nebo dokumentu zámky.  
  
### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>Chcete-li vytvořit dialogové okno, které uživatel nemůže ukončit.  
  
1.  V **vlastnosti** nastavte dialogové okno, v podokně **nabídky systému** vlastnost **false**.  
  
     To zakáže nabídky systému dialogového a **Zavřít** tlačítko.  
  
2.  V dialogovém okně pole formuláře, odstraňte **zrušit** a **OK** tlačítka.  
  
     Za běhu uživatel nemůže ukončit modální dialogové okno, které má tyto vlastnosti.  
  
 Pro umožnění testování druhu dialogového okna, při stisknutí klávesy ESC vyhledá funkci test dialogové okno pole. (ESC se také označuje jako vk_escape – klíč virtuální.) Bez ohledu na to, jak je navržený dialogové okno se bude chovat v době běhu můžete ukončit jej v testovacím režimu stisknutím klávesy ESC.  
  
> [!NOTE]
>  Pro aplikace MFC, chcete-li vytvořit dialogové okno, které uživatelé nemohou zavřít, je nutné přepsat výchozí chování `OnOK` a `OnCancel` vzhledem k tomu, že i v případě, že odstraníte přidružené tlačítek, dialogové okno můžete stále zrušit stisknutím klávesy ENTER nebo ESC.  
  
 Informace o tom, jak přidat prostředky do spravovaných projekty najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření prostředku](../windows/how-to-create-a-resource.md)   
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editor dialogových oken](../windows/dialog-editor.md)

