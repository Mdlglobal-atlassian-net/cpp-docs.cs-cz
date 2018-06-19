---
title: Třída CMFCImageEditorPaletteBar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
dev_langs:
- C++
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e377a465dd55d8940e74617130216220d03f1218
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370039"
---
# <a name="cmfcimageeditorpalettebar-class"></a>CMFCImageEditorPaletteBar – třída
Poskytuje funkce panelu palety dialogovém okně editor bitové kopie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCImageEditorPaletteBar : public CMFCToolBar  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCImageEditorPaletteBar::GetRowHeight](#getrowheight)|Vrátí výšku tlačítka panelu nástrojů. (Přepisuje [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|  
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Určuje, zda lze panelu nástrojů zobrazovat tlačítka, která rozšířili ohraničení. (Přepisuje [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|  
  
### <a name="remarks"></a>Poznámky  
 Tato třída není určena pro použití přímo z vašeho kódu.  
  
 Rozhraní používá tuto třídu pro zobrazení palety panelu v dialogovém okně editor bitové kopie. Další informace o dialogovém okně editor bitové kopie najdete v tématu [CMFCImageEditorDialog třída](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afximageeditordialog.h  
  
##  <a name="getrowheight"></a>  CMFCImageEditorPaletteBar::GetRowHeight  
 Vrátí výšku tlačítka panelu nástrojů.  
  
```  
virtual int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška jednotlivých tlačítek na panelu nástrojů.  
  
##  <a name="isbuttonextrasizeavailable"></a>  CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable  
 Určuje, zda lze panelu nástrojů zobrazovat tlačítka, která rozšířili ohraničení.  
  
```  
virtual BOOL IsButtonExtraSizeAvailable() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí hodnotu `FALSE`.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md)
