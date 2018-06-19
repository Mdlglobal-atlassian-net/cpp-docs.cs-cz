---
title: CPaintDC – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9f83c36a9c1a0d334e3b4a75724521d5711123e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376532"
---
# <a name="cpaintdc-class"></a>CPaintDC – třída
Odvozené třídy kontextu zařízení z [CDC](../../mfc/reference/cdc-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPaintDC : public CDC  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPaintDC::CPaintDC](#cpaintdc)|Vytvoří `CPaintDC` připojené k zadané [CWnd](../../mfc/reference/cwnd-class.md).|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPaintDC::m_ps](#m_ps)|Obsahuje [paintstruct –](../../mfc/reference/paintstruct-structure.md) použita k vyplnění klientské oblasti.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPaintDC::m_hWnd](#m_hwnd)|`HWND` Ke kterému tato `CPaintDC` objekt je připojený.|  
  
## <a name="remarks"></a>Poznámky  
 Provede [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) během vytváření a [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) během odstraňování.  
  
 A `CPaintDC` objekt lze použít pouze při odpovědi na [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) zprávy, obvykle v vaší `OnPaint` obslužné rutiny zpráv – členská funkce.  
  
 Další informace o používání `CPaintDC`, najdete v části [kontexty zařízení](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CPaintDC`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC  
 Vytvoří `CPaintDC` objekt, připraví okna aplikace pro malování a ukládá [paintstruct –](../../mfc/reference/paintstruct-structure.md) struktury v [m_ps](#m_ps) členské proměnné.  
  
```  
explicit CPaintDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Odkazuje na `CWnd` objekt, ke kterému `CPaintDC` objekt náleží.  
  
### <a name="remarks"></a>Poznámky  
 K výjimce (typu `CResourceException`) je vyvolána, pokud Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871) volání selže. Kontext zařízení nemusí být k dispozici, pokud systém Windows všechny jeho kontexty zařízení k dispozici již přiděleno. Vaše aplikace bojuje pro pět běžné zobrazení kontexty dostupné v každém okamžiku v systému Windows.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd  
 `HWND` Ke kterému tato `CPaintDC` objekt je připojený.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_hWnd` je chráněný proměnná typu `HWND`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]  
  
##  <a name="m_ps"></a>  CPaintDC::m_ps  
 `m_ps` je veřejný členské proměnné typu [paintstruct –](../../mfc/reference/paintstruct-structure.md).  
  
```  
PAINTSTRUCT m_ps;  
```  
  
### <a name="remarks"></a>Poznámky  
 Je `PAINTSTRUCT` , je předán a vyplňovat [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).  
  
 `PAINTSTRUCT` Obsahuje informace, které aplikace používá k vyplnění klientské oblasti okna přidružené `CPaintDC` objektu.  
  
 Všimněte si, že máte přístup prostřednictvím popisovač kontextu zařízení `PAINTSTRUCT`. Však může přistupovat k popisovač více přímo prostřednictvím `m_hDC` členské proměnné, `CPaintDC` dědí z `CDC`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPaintDC::m_hWnd](#m_hwnd).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MDI](../../visual-cpp-samples.md)   
 [Třída CDC](../../mfc/reference/cdc-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



