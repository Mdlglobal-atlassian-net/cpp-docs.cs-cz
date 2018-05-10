---
title: Použití ovládacího prvku RichEdit 1.0 s MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls, RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d2d45de1c6bd986c2bf509ce601f80fcd3721599
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Použití ovládacího prvku RichEdit 1.0 s MFC
Použití ovládacího prvku RichEdit, nejprve je třeba volat [afxinitrichedit2 –](../mfc/reference/application-information-and-management.md#afxinitrichedit2) načíst ovládacího prvku RichEdit 2.0 (RICHED20. Knihovny DLL), nebo volejte [afxinitrichedit –](../mfc/reference/application-information-and-management.md#afxinitrichedit) načíst starší RichEdit 1.0 ovládacího prvku (RICHED32. KNIHOVNY DLL).  
  
 Můžete použít aktuální [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) třídy pomocí ovládacího prvku starší RichEdit 1.0, ale **CRichEditCtrl** je určen pouze pro podporu ovládacího prvku RichEdit 2.0. Protože jsou velmi podobné RichEdit 1.0 a RichEdit 2.0, budou fungovat většinu metod; Všimněte si však, že existují určité rozdíly mezi 1.0 a 2.0 ovládací prvky, takže některé metody může pracovat správně nebo vůbec.  
  
## <a name="requirements"></a>Požadavky  
 MFC  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží s editoru dialogových oken](../windows/troubleshooting-the-dialog-editor.md)   
 [Editor dialogových oken](../windows/dialog-editor.md)

