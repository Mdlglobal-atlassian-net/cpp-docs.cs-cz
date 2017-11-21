---
title: "Třída COleControlModule | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: OleControlModule
dev_langs: C++
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0153adbae458d0f4ab432c2c7cb8c71621d76418
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="colecontrolmodule-class"></a>COleControlModule – třída
Základní třída, ze kterého odvodíte objekt OLE řízení modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleControlModule : public CWinApp  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje členské funkce pro inicializaci modulu ovládacího prvku. Každý modul OLE ovládací prvek, který používá třídy Microsoft Foundation může obsahovat pouze jeden objekt odvozený od `COleControlModule`. Tento objekt je vytvořený, když se vytvářejí další globální objekty C++. Deklarovat vaší odvozené `COleControlModule` objektu na globální úrovni.  
  
 Další informace o používání `COleControlModule` třídy najdete v tématu [CWinApp](../../mfc/reference/cwinapp-class.md) třídy a v článku [– ovládací prvky ActiveX](../../mfc/mfc-activex-controls.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 `COleControlModule`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC TESTHELP](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



