---
title: "CClientDC – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
dev_langs: C++
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e88f9b789a87eac5af56c27d156cf2e00929d5fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cclientdc-class"></a>CClientDC – třída
Má na starosti volání funkcí Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871) během vytváření a [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920) během odstraňování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CClientDC : public CDC  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CClientDC::CClientDC](#cclientdc)|Vytvoří `CClientDC` připojený k objektu `CWnd`.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CClientDC::m_hWnd](#m_hwnd)|`HWND` Období, pro které bude tato `CClientDC` je platný.|  
  
## <a name="remarks"></a>Poznámky  
 To znamená, že zařízení kontext přidružený `CClientDC` objekt je klientské oblasti časového období.  
  
 Další informace o `CClientDC`, najdete v části [kontexty zařízení](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CClientDC`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cclientdc"></a>CClientDC::CClientDC  
 Vytvoří `CClientDC` objekt, který přistupuje k klientské oblasti [CWnd](../../mfc/reference/cwnd-class.md) na kterou odkazuje `pWnd`.  
  
```  
explicit CClientDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Okno jejichž klientské oblasti objektu kontextu zařízení bude mít přístup.  
  
### <a name="remarks"></a>Poznámky  
 V konstruktoru volání funkce systému Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871).  
  
 K výjimce (typu `CResourceException`) je vyvolána, pokud Windows `GetDC` volání selže. Kontext zařízení nemusí být k dispozici, pokud systém Windows všechny jeho kontexty zařízení k dispozici již přiděleno. Vaše aplikace bojuje pro pět běžné zobrazení kontexty dostupné v každém okamžiku v systému Windows.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>CClientDC::m_hWnd  
 `HWND` z `CWnd` použitý k vytvoření ukazatele `CClientDC` objektu.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_hWnd`je chráněný proměnné.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CClientDC::CClientDC](#cclientdc).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MDI](../../visual-cpp-samples.md)   
 [Třída CDC](../../mfc/reference/cdc-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CDC](../../mfc/reference/cdc-class.md)
