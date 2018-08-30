---
title: Cwindowdc – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 40566ab94c9708d7b31f88de0f96b4fc33675534
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212518"
---
# <a name="cwindowdc-class"></a>Cwindowdc – třída
Odvozené od `CDC`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CWindowDC : public CDC  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CWindowDC::CWindowDC](#cwindowdc)|Vytvoří `CWindowDC` objektu.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[CWindowDC::m_hWnd](#m_hwnd)|HWND, ke kterému je tento `CWindowDC` je připojen.|  
  
## <a name="remarks"></a>Poznámky  
 Volá funkci Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)v době konstrukce a [ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc) v době zničení. To znamená, že `CWindowDC` objektů přistupuje k oblasti celé obrazovky [CWnd](../../mfc/reference/cwnd-class.md) (klientská a neklientská oblast).  
  
 Další informace o používání `CWindowDC`, naleznete v tématu [kontexty zařízení](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## <a name="requirements"></a>Požadavky  
 Hlavička: afxwin.h  
  
##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC  
 Vytvoří `CWindowDC` objekt, který přistupuje k oblasti celé obrazovky (klientská a neklientská) z `CWnd` objekt, který odkazuje *pWnd*.  
  
```  
explicit CWindowDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Okno, jehož klientské oblasti bude mít přístup k objektu kontextu zařízení.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor zavolá funkci Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc).  
  
 Výjimky (typu `CResourceException`) je vyvolána, pokud Windows `GetWindowDC` volání selže. Kontext zařízení nemusí být k dispozici, pokud Windows má již přiděleno všechny jeho kontexty zařízení k dispozici. Vaše aplikace bojuje pěti běžných zobrazení kontextů k dispozici v daném okamžiku v části Windows.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd  
 HWND o HODNOTĚ `CWnd` ukazatele je použit pro vytvoření `CWindowDC` objektu.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_hWnd` je chráněný proměnné typu HWND.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWindowDC::CWindowDC](#cwindowdc).  
  
## <a name="see-also"></a>Viz také  
 [CDC – třída](../../mfc/reference/cdc-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDC – třída](../../mfc/reference/cdc-class.md)
