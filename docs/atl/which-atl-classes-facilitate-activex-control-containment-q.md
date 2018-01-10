---
title: "Které třídy ATL usnadnění uzavření ovládacího prvku ActiveX? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
ms.assetid: 803a4605-7f4c-4139-8638-49d8783d31b0
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 880c7bd52476614a4356690aff2fda286e9f3aef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="which-atl-classes-facilitate-activex-control-containment"></a>Které třídy ATL usnadnění uzavření ovládacího prvku ActiveX?
Hostování ovládacího prvku kódu ATL na nevyžaduje, můžete použít všechny třídy ATL; můžete jednoduše vytvořit **"AtlAxWin80"** okno a použití rozhraní API hostování ovládacího prvku v případě potřeby (Další informace najdete v tématu **co je rozhraní API ovládacího prvku ATL – hostování**. Ale následující třídy usnadňují funkce omezení použití.  
  
|Třída|Popis|  
|-----------|-----------------|  
|[CAxWindow](../atl/reference/caxwindow-class.md)|Zabalí **"AtlAxWin80"** okno, poskytuje metody pro vytvoření okna, vytvoření ovládacího prvku nebo připojení ovládacího prvku do okna a načítání ukazatele rozhraní na objekt hostitele.|  
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Zabalí **"AtlAxWinLic80"** okně poskytnete metody vytvoření okna, vytvoření ovládacího prvku nebo připojení licencovanou ovládacího prvku do okna a načítání ukazatele rozhraní na objekt hostitele.|  
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Funguje jako základní třída pro třídy ovládacích prvků ActiveX podle prostředku dialogového okna. Tyto ovládací prvky může obsahovat další ovládací prvky ActiveX.|  
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Funguje jako základní třída pro třídy dialogových oken podle prostředku dialogového okna. Ovládací prvky ActiveX může obsahovat tyto dialogy.|  
|[CWindow](../atl/reference/cwindow-class.md)|Poskytuje metodu, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), který vrátí ukazatele rozhraní v ovládacím prvku zadané ID jeho hostitelské okno. Kromě toho rozhraní API systému Windows obálky vystavené `CWindow` obecně snazší správa oken.|  
  
## <a name="see-also"></a>Viz také  
 [Uzavření ovládacího prvku – nejčastější dotazy](../atl/atl-control-containment-faq.md)

