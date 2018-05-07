---
title: Třída CWindowDC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7867f35a66abf0f5a33ecd411b81111e84e3800f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cwindowdc-class"></a>CWindowDC – třída
Odvozené z `CDC`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CWindowDC : public CDC  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CWindowDC::CWindowDC](#cwindowdc)|Vytvoří `CWindowDC` objektu.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CWindowDC::m_hWnd](#m_hwnd)|`HWND` Ke kterému tato `CWindowDC` je připojen.|  
  
## <a name="remarks"></a>Poznámky  
 Volání funkce systému Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947\(v=vs.85\).aspx)během vytváření a [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920\(v=vs.85\).aspx) během odstraňování. To znamená, že `CWindowDC` objekt přistupuje k oblasti celou obrazovku [CWnd](../../mfc/reference/cwnd-class.md) (klient a nonclient oblasti).  
  
 Další informace o používání `CWindowDC`, najdete v části [kontexty zařízení](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: afxwin.h  
  
##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC  
 Vytvoří `CWindowDC` objekt, který má přístup k celé oblasti obrazovky (klient a nonclient) `CWnd` objektu na kterou odkazuje `pWnd`.  
  
```  
explicit CWindowDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Okno jejichž klientské oblasti objekt kontextu zařízení bude mít přístup.  
  
### <a name="remarks"></a>Poznámky  
 V konstruktoru volání funkce systému Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947).  
  
 K výjimce (typu `CResourceException`) je vyvolána, pokud Windows `GetWindowDC` volání selže. Kontext zařízení nemusí být k dispozici, pokud systém Windows všechny jeho kontexty zařízení k dispozici již přiděleno. Vaše aplikace bojuje pro pět běžné zobrazení kontexty dostupné v každém okamžiku v systému Windows.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd  
 `HWND` z `CWnd` ukazatele se používá pro konstrukci `CWindowDC` objektu.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_hWnd` je chráněný proměnná typu `HWND`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWindowDC::CWindowDC](#cwindowdc).  
  
## <a name="see-also"></a>Viz také  
 [Třída CDC](../../mfc/reference/cdc-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDC – třída](../../mfc/reference/cdc-class.md)
