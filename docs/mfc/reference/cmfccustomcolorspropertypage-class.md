---
title: "Třída CMFCCustomColorsPropertyPage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
dev_langs:
- C++
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7dac4260c69e4d2bbf9c74965e73f6961dd6ad6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage – třída
Představuje stránku vlastností, která můžete vybrat vlastní barvy v dialogovém okně barvy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCCustomColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Výchozí konstruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|`CMFCCustomColorsPropertyPage::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|`CMFCCustomColorsPropertyPage::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Nastaví barvu součástí stránku vlastností.|  
  
### <a name="remarks"></a>Poznámky  
 `CMFCColorDialog` Třída používá tato třída zobrazíte její stránku vlastností vlastních barev. Další informace o `CMFCColorDialog`, najdete v části [CMFCColorDialog třída](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCCustomColorsPropertyPage` objektu a nastavte barvu součástí stránku vlastností.  
  
 [!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcustomcolorspropertypage.h  
  
##  <a name="setup"></a>CMFCCustomColorsPropertyPage::Setup  
 Nastaví barvu součástí stránku vlastností.  
  
```  
void Setup(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v]`R`|Komponentu red hodnoty RGB.|  
|[v]`G`|Zelená součást hodnotou.|  
|[v]`B`|Modré součást hodnotou.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda aktualizace aktuální RGB a přidružené HLS (hue, světlost a sytost) Barva hodnoty na stránce vlastností. [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) metoda volá tuto metodu, pokud rozhraní inicializuje dialogové okno barev nebo stisknutí levé tlačítko. Další informace o `CMFCColorDialog`, najdete v části [CMFCColorDialog třída](../../mfc/reference/cmfccolordialog-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog – třída](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCStandardColorsPropertyPage – třída](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
