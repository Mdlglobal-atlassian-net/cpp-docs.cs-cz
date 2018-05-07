---
title: Třída CMFCDesktopAlertWndButton | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: efabaabdcc3f08a58cb7dc0a7845a56e5238548d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton – třída
Umožňuje tlačítka, který se má přidat do plochy dialogového okna výstrah.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDesktopAlertWndButton : public CMFCButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Výchozí konstruktor.|  
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Určuje, jestli se v oblasti Titulek dialogového okna výstrah zobrazí tlačítko.|  
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Určuje, zda tlačítko zavře dialogové okno upozornění.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|Název|Popis|  
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Logická hodnota, která určuje, jestli se v oblasti Titulek dialogového okna výstrah zobrazí tlačítko.|  
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Logická hodnota, která určuje, zda tlačítko zavře dialogové okno upozornění.|  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, konstruktor nastaví `m_bIsCaptionButton` a `m_bIsCloseButton` datových členů ke `FALSE`. Nadřazený `CMFCDesktopAlertDialog` objektu sady `m_bIsCaptionButton` k `TRUE` Pokud tlačítko je umístěný v oblasti Titulek dialogového okna výstrah. `CMFCDesktopAlertDialog` Třída vytvoří `CMFCDesktopAlertWndButton` objekt, který slouží jako tlačítko zavření dialogového okna výstrah pole a nastaví `m_bIsCloseButton` k `TRUE`.  
  
 Přidat `CMFCDesktopAlertWndButton` objekty do `CMFCDesktopAlertDialog` objektů, jako by všechny tlačítko Přidat. Další informace o `CMFCDesktopAlertDialog`, najdete v části [CMFCDesktopAlertDialog třída](../../mfc/reference/cmfcdesktopalertdialog-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `SetImage` metoda v `CMFCDesktopAlertWndButton` třídy. Tento fragment kódu je součástí [plochy výstrahy Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdesktopalertwnd.h  
  
##  <a name="iscaptionbutton"></a>  CMFCDesktopAlertWndButton::IsCaptionButton  
 Určuje, jestli se v oblasti Titulek dialogového okna výstrah zobrazí tlačítko.  
  
```  
BOOL IsCaptionButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li na tlačítko se zobrazí v oblasti titulek pole dialogového okna výstrah; jinak hodnota 0.  
  
##  <a name="isclosebutton"></a>  CMFCDesktopAlertWndButton::IsCloseButton  
 Určuje, zda tlačítko zavře dialogové okno upozornění.  
  
```  
BOOL IsCloseButton() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li na tlačítko zavření dialogového okna Výstraha; jinak hodnota 0.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertDialog – třída](../../mfc/reference/cmfcdesktopalertdialog-class.md)
