---
title: "Třída CHwndRenderTarget | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
dev_langs: C++
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7576d1a5635cf30084c1f36b4ec14ad2a9f9b74d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget – třída
Obálka pro ID2D1HwndRenderTarget.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CHwndRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Vytvoří objekt CHwndRenderTarget od HWND.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CHwndRenderTarget::Attach](#attach)|Připojí existující vykreslení cílové rozhraní k objektu|  
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Určuje, zda je occluded HWND přidružený tento cíl vykreslení.|  
|[CHwndRenderTarget::Create](#create)|Vytvoří cíl vykreslení přidružené okna|  
|[CHwndRenderTarget::Detach](#detach)|Umožňuje odpojit vykreslení cílové rozhraní z objektu|  
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Vrátí HWND přidružený k tomuto vykreslit cíl.|  
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Vrátí ID2D1HwndRenderTarget rozhraní.|  
|[CHwndRenderTarget::ReCreate](#recreate)|Znovu vytvoří cíl vykreslení přidružené okna|  
|[CHwndRenderTarget::Resize](#resize)|Změní velikost cíle vykreslení na velikost zadaná pixelů|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget *](#operator_id2d1hwndrendertarget_star)|Vrátí ID2D1HwndRenderTarget rozhraní.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Ukazatel na objekt ID2D1HwndRenderTarget.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="attach"></a>CHwndRenderTarget::Attach  
 Připojí existující vykreslení cílové rozhraní k objektu  
  
```  
void Attach(ID2D1HwndRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pTarget`  
 Existující vykreslení cílové rozhraní. Nemůže mít hodnotu NULL  
  
##  <a name="checkwindowstate"></a>CHwndRenderTarget::CheckWindowState  
 Určuje, zda je occluded HWND přidružený tento cíl vykreslení.  
  
```  
D2D1_WINDOW_STATE CheckWindowState() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Je occluded hodnotu, která určuje, zda HWND přidružený k tomuto vykreslení cíl.  
  
##  <a name="chwndrendertarget"></a>CHwndRenderTarget::CHwndRenderTarget  
 Vytvoří objekt CHwndRenderTarget od HWND.  
  
```  
CHwndRenderTarget(HWND hwnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hwnd`  
 HWND přidružený k tomuto vykreslení cíl  
  
##  <a name="create"></a>CHwndRenderTarget::Create  
 Vytvoří cíl vykreslení přidružené okna  
  
```  
BOOL Create(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 HWND přidružený k tomuto vykreslení cíl  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. Jinak vrátí hodnotu FALSE  
  
##  <a name="detach"></a>CHwndRenderTarget::Detach  
 Umožňuje odpojit vykreslení cílové rozhraní z objektu  
  
```  
ID2D1HwndRenderTarget* Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na odpojit vykreslit cílové rozhraní.  
  
##  <a name="gethwnd"></a>CHwndRenderTarget::GetHwnd  
 Vrátí HWND přidružený k tomuto vykreslit cíl.  
  
```  
HWND GetHwnd() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 HWND přidružený k tomuto vykreslit cíl.  
  
##  <a name="gethwndrendertarget"></a>CHwndRenderTarget::GetHwndRenderTarget  
 Vrátí ID2D1HwndRenderTarget rozhraní.  
  
```  
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1HwndRenderTarget nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="m_phwndrendertarget"></a>CHwndRenderTarget::m_pHwndRenderTarget  
 Ukazatel na objekt ID2D1HwndRenderTarget.  
  
```  
ID2D1HwndRenderTarget* m_pHwndRenderTarget;  
```  
  
##  <a name="operator_id2d1hwndrendertarget_star"></a>CHwndRenderTarget::operator ID2D1HwndRenderTarget *  
 Vrátí ID2D1HwndRenderTarget rozhraní.  
  
```  
operator ID2D1HwndRenderTarget*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1HwndRenderTarget nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="recreate"></a>CHwndRenderTarget::ReCreate  
 Znovu vytvoří cíl vykreslení přidružené okna  
  
```  
BOOL ReCreate(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 HWND přidružený k tomuto vykreslení cíl  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="resize"></a>CHwndRenderTarget::Resize  
 Změní velikost cíle vykreslení na velikost zadaná pixelů  
  
```  
BOOL Resize(const CD2DSizeU& size);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Velikost nového cíle vykreslení v pixelech zařízení  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
