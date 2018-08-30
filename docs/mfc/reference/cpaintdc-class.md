---
title: Cpaintdc – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 49681f240d6cee257e48c2cf1c5d2479b3678135
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208367"
---
# <a name="cpaintdc-class"></a>Cpaintdc – třída
Kontext zařízení třída odvozená z [CDC](../../mfc/reference/cdc-class.md).  
  
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
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[CPaintDC::m_hWnd](#m_hwnd)|HWND, ke kterému je tento `CPaintDC` objekt připojen.|  
  
## <a name="remarks"></a>Poznámky  
 Funguje [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) v době konstrukce a [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) v době zničení.  
  
 A `CPaintDC` objektu jde použít jenom při odpovídání na [WM_PAINT](/windows/desktop/gdi/wm-paint) zpráv, obvykle v vaše `OnPaint` obslužná rutina zprávy členskou funkci.  
  
 Další informace o používání `CPaintDC`, naleznete v tématu [kontexty zařízení](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CPaintDC`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC  
 Vytvoří `CPaintDC` připraví okna aplikace pro kreslení objektu a ukládá [paintstruct –](../../mfc/reference/paintstruct-structure.md) struktury v [m_ps](#m_ps) členské proměnné.  
  
```  
explicit CPaintDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Odkazuje na `CWnd` objekt, na který `CPaintDC` objekt patří.  
  
### <a name="remarks"></a>Poznámky  
 Výjimky (typu `CResourceException`) je vyvolána, pokud Windows [GetDC](/windows/desktop/api/winuser/nf-winuser-getdc) volání selže. Kontext zařízení nemusí být k dispozici, pokud Windows má již přiděleno všechny jeho kontexty zařízení k dispozici. Vaše aplikace bojuje pěti běžných zobrazení kontextů k dispozici v daném okamžiku v části Windows.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd  
 `HWND` Ke kterému je tento `CPaintDC` objekt připojen.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Poznámky  
 *m_hWnd* je chráněná proměnná typu HWND.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]  
  
##  <a name="m_ps"></a>  CPaintDC::m_ps  
 `m_ps` je veřejné členské proměnné typu [paintstruct –](../../mfc/reference/paintstruct-structure.md).  
  
```  
PAINTSTRUCT m_ps;  
```  
  
### <a name="remarks"></a>Poznámky  
 Je `PAINTSTRUCT` , který je předán a vyplňuje [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).  
  
 `PAINTSTRUCT` Obsahuje informace, které aplikace používá k vyplnění klientské oblasti okna přidružené `CPaintDC` objektu.  
  
 Všimněte si, že dostanete popisovač kontextu zařízení prostřednictvím `PAINTSTRUCT`. Však můžete přistupovat k popisovač více přímo prostřednictvím `m_hDC` členské proměnné, která `CPaintDC` dědí z CSP.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPaintDC::m_hWnd](#m_hwnd).  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC MDI](../../visual-cpp-samples.md)   
 [CDC – třída](../../mfc/reference/cdc-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



