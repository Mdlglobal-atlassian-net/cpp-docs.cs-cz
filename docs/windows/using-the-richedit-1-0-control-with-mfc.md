---
title: "Použití ovládacího prvku RichEdit 1.0 s MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls, RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8085eb8b28ece4f0ca24d00c33b8809aa412da5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Použití ovládacího prvku RichEdit 1.0 s MFC
Použití ovládacího prvku RichEdit, nejprve je třeba volat [afxinitrichedit2 –](../mfc/reference/application-information-and-management.md#afxinitrichedit2) načíst ovládacího prvku RichEdit 2.0 (RICHED20. Knihovny DLL), nebo volejte [afxinitrichedit –](../mfc/reference/application-information-and-management.md#afxinitrichedit) načíst starší RichEdit 1.0 ovládacího prvku (RICHED32. KNIHOVNY DLL).  
  
 Můžete použít aktuální [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) třídy pomocí ovládacího prvku starší RichEdit 1.0, ale **CRichEditCtrl** je určen pouze pro podporu ovládacího prvku RichEdit 2.0. Protože jsou velmi podobné RichEdit 1.0 a RichEdit 2.0, budou fungovat většinu metod; Všimněte si však, že existují určité rozdíly mezi 1.0 a 2.0 ovládací prvky, takže některé metody může pracovat správně nebo vůbec.  
  
## <a name="requirements"></a>Požadavky  
 MFC  
  
## <a name="see-also"></a>Viz také  
 [Řešení potíží s editoru dialogových oken](../windows/troubleshooting-the-dialog-editor.md)   
 [Editor dialogových oken](../windows/dialog-editor.md)

