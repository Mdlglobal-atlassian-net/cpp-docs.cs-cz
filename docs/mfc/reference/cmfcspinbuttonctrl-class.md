---
title: Třída CMFCSpinButtonCtrl | Microsoft Docs
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
ms.openlocfilehash: 1b8c602882036d77105bb619069a6e43d73ceeb6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366795"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl – třída
`CMFCSpinButtonCtrl` Třída podporuje visual správce, který se vykreslí ovládací prvek typu číselník tlačítko.  
  
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
 Pokud chcete použít k vykreslení ovládacího prvku typu číselník tlačítko v aplikaci visual manager, nahraďte všechny výskyty `CSpinButtonCtrl` třídy s `CMFCSpinButtonCtrl` třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCSpinButtonCtrl` třídy a použít jeho `Create` metoda.  
  
 [!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)  
  
 [CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxspinbuttonctrl.h  
  
##  <a name="ondraw"></a>  CMFCSpinButtonCtrl::OnDraw  
 Překreslí aktuální ovládací prvek typu číselník tlačítko.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontextu zařízení.  
  
### <a name="remarks"></a>Poznámky  
 Volání framework `CMFCSpinButtonCtrl::OnPaint` metodu ke zpracování [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) zprávu, a že metoda volá to `CMFCSpinButtonCtrl::OnDraw` metoda. Potlačí tuto metodu lze upravit způsob rozhraní nevykresluje ovládací prvek typu číselník tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager – třída](../../mfc/reference/cmfcvisualmanager-class.md)
