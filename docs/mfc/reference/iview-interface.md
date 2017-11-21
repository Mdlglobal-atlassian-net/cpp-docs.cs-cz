---
title: "Rozhraní IView | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IView
- No header/IView
- No header/IView::OnActivateView
- No header/IView::OnInitialUpdate
- No header/IView::OnUpdate
dev_langs: C++
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 144cea65ddfa5153fb117c9570b101a1ce99eb32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iview-interface"></a>IView rozhraní
Implementuje několik metod, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) používá k odesílání oznámení zobrazení do ovládacího prvku spravované.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
interface class IView  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IView::OnActivateView](#onactivateview)|Voláno rozhraním MFC, pokud je aktivace nebo deaktivace zobrazení.|  
|[IView::OnInitialUpdate](#oninitialupdate)|Voláno rámcem po zobrazení je nejprve připojen k dokumentu, ale před zpočátku je zobrazeno zobrazení.|  
|[IView::OnUpdate](#onupdate)|Voláno rozhraním MFC po zobrazení byly změny; Tato funkce umožňuje zobrazit aktualizace jeho zobrazení, aby se projevily změny.|  
  
## <a name="remarks"></a>Poznámky  
 `IView`implementuje několik metod, `CWinFormsView` používá k předávání běžné zobrazení oznámení na hostované spravované ovládací prvek. Jedná se o [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) a [OnActivateView](#onactivateview).  
  
 `IView`je podobná [CView](../../mfc/reference/cview-class.md), ale se používá jenom s spravované zobrazení a ovládací prvky.  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  

## <a name="requirements"></a>Požadavky  
 Záhlaví: afxwinforms.h (definovanou v atlmfc\lib\mfcmifc80.dll sestavení)  

## <a name="onactivateview"></a>IView::OnActivateView  
Voláno rozhraním MFC, pokud je aktivace nebo deaktivace zobrazení.
```
void OnActivateView(bool activate);
```
## <a name="parameters"></a>Parametry
`activate`  
Určuje, zda zobrazení se aktivace nebo deaktivace.  

## <a name="oninitialupdate"></a>IView::OnInitialUpdate
Voláno rámcem po zobrazení je nejprve připojen k dokumentu, ale před zpočátku je zobrazeno zobrazení.
```
void OnInitialUpdate();
```

## <a name="onupdate"></a>IView::OnUpdate 
Voláno rozhraním MFC po zobrazení byly změny.  
```
void OnUpdate();
```
## <a name="remarks"></a>Poznámky  
Tato funkce umožňuje zobrazit aktualizace jeho zobrazení, aby se projevily změny.

## <a name="see-also"></a>Viz také  
 [CWinFormsView – třída](../../mfc/reference/cwinformsview-class.md)   
 [CView – třída](../../mfc/reference/cview-class.md)
