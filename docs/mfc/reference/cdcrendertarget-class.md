---
title: Třída CDCRenderTarget | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36f8a038cd282ddf233fe2cf15a134c52962ebff
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953698"
---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget – třída
Obálka pro ID2D1DCRenderTarget.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDCRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Vytvoří objekt CDCRenderTarget.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDCRenderTarget::Attach](#attach)|Připojí existující vykreslení cílové rozhraní k objektu|  
|[CDCRenderTarget::BindDC](#binddc)|Sváže cíl vykreslení kontextu zařízení, do které vydává příkazy pro kreslení|  
|[CDCRenderTarget::Create](#create)|Vytvoří CDCRenderTarget.|  
|[CDCRenderTarget::Detach](#detach)|Umožňuje odpojit vykreslení cílové rozhraní z objektu|  
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Vrátí ID2D1DCRenderTarget rozhraní|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDCRenderTarget::operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|Vrátí ID2D1DCRenderTarget rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Ukazatel na objekt ID2D1DCRenderTarget.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="attach"></a>  CDCRenderTarget::Attach  
 Připojí existující vykreslení cílové rozhraní k objektu  
  
```  
void Attach(ID2D1DCRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>Parametry  
 *pTarget*  
 Existující vykreslení cílové rozhraní. Nemůže mít hodnotu NULL  
  
##  <a name="binddc"></a>  CDCRenderTarget::BindDC  
 Sváže cíl vykreslení kontextu zařízení, do které vydává příkazy pro kreslení  
  
```  
BOOL BindDC(
    const CDC& dc,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 *řadič domény*  
 Kontext zařízení, do které cíl vykreslení vysílá příkazy kreslení  
  
 *Rect –*  
 Dimenze popisovač kontextu zařízení (HDC), ke kterému je vázán cíl vykreslení  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="cdcrendertarget"></a>  CDCRenderTarget::CDCRenderTarget  
 Vytvoří objekt CDCRenderTarget.  
  
```  
CDCRenderTarget();
```  
  
##  <a name="create"></a>  CDCRenderTarget::Create  
 Vytvoří CDCRenderTarget.  
  
```  
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```  
  
### <a name="parameters"></a>Parametry  
 *props*  
 Režim vykreslování, Pixelový formát, možnosti vzdálenou komunikaci, DPI informace a minimální podporu rozhraní DirectX požadované pro vykreslování hardwaru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="detach"></a>  CDCRenderTarget::Detach  
 Umožňuje odpojit vykreslení cílové rozhraní z objektu  
  
```  
ID2D1DCRenderTarget* Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na odpojit vykreslit cílové rozhraní.  
  
##  <a name="getdcrendertarget"></a>  CDCRenderTarget::GetDCRenderTarget  
 Vrátí ID2D1DCRenderTarget rozhraní  
  
```  
ID2D1DCRenderTarget* GetDCRenderTarget();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1DCRenderTarget nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="m_pdcrendertarget"></a>  CDCRenderTarget::m_pDCRenderTarget  
 Ukazatel na objekt ID2D1DCRenderTarget.  
  
```  
ID2D1DCRenderTarget* m_pDCRenderTarget;  
```  
  
##  <a name="operator_id2d1dcrendertarget_star"></a>  CDCRenderTarget::operator ID2D1DCRenderTarget *  
 Vrátí ID2D1DCRenderTarget rozhraní  
  
```  
operator ID2D1DCRenderTarget*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1DCRenderTarget nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
