---
title: Cmfcspinbuttonctrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
dev_langs:
- C++
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 960a1a0338a3390fdc10cf03ddc235bcf4ecbae9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712748"
---
# <a name="cmfcspinbuttonctrl-class"></a>Cmfcspinbuttonctrl – třída
`CMFCSpinButtonCtrl` Třída podporuje vizuálního správce, který vykreslí ovládací prvek číselníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCSpinButtonCtrl : public CSpinButtonCtrl  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Výchozí konstruktor.|  
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Překreslí aktuální ovládací prvek typu číselník tlačítko.|  
  
## <a name="remarks"></a>Poznámky  
 Nakreslete ovládací prvek číselníku ve vaší aplikaci pomocí Správce vzhledu, nahraďte všechny výskyty `CSpinButtonCtrl` třídy s `CMFCSpinButtonCtrl` třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCSpinButtonCtrl` třídy a použít jeho `Create` metoda.  
  
 [!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cspinbuttonctrl –](../../mfc/reference/cspinbuttonctrl-class.md)  
  
 [Cmfcspinbuttonctrl –](../../mfc/reference/cmfcspinbuttonctrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxspinbuttonctrl.h  
  
##  <a name="ondraw"></a>  CMFCSpinButtonCtrl::OnDraw  
 Překreslí aktuální ovládací prvek typu číselník tlačítko.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
*primární řadič domény*<br/>
[in] Ukazatel na kontext zařízení.  
  
### <a name="remarks"></a>Poznámky  
 Rámec volá `CMFCSpinButtonCtrl::OnPaint` metodu ke zpracování [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) zprávu, a že metoda volá to `CMFCSpinButtonCtrl::OnDraw` metody. Přepsáním této metody můžete přizpůsobit tak, jak rozhraní nakreslí otočný ovládací prvek tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager – třída](../../mfc/reference/cmfcvisualmanager-class.md)
