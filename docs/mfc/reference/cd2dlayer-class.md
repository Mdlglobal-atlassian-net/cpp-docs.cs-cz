---
title: "Třída CD2DLayer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
dev_langs: C++
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94345f4784254addce0deaf8bdb5061dbde6a8cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dlayer-class"></a>CD2DLayer – třída
Obálka pro ID2D1Layer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DLayer : public CD2DResource;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DLayer::CD2DLayer](#cd2dlayer)|Vytvoří objekt CD2DLayer.|  
|[CD2DLayer:: ~ CD2DLayer](#_dtorcd2dlayer)|Destruktor. Voláno, když je zničen objektu D2D vrstvy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DLayer::Attach](#attach)|Připojí existující prostředek rozhraní k objektu|  
|[CD2DLayer::Create](#create)|Vytvoří CD2DLayer. (Přepisuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DLayer::Destroy](#destroy)|Zničí CD2DLayer objektu. (Přepisuje [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DLayer::detach](#detach)|Umožňuje odpojit prostředek rozhraní z objektu|  
|[CD2DLayer::Get](#get)|Vrátí ID2D1Layer rozhraní|  
|[CD2DLayer::GetSize](#getsize)|Vrátí velikost cíle vykreslení v pixelech nezávislé na zařízení|  
|[CD2DLayer::IsValid](#isvalid)|Ověří platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DLayer::Operator ID2D1Layer *](#operator_id2d1layer_star)|Vrátí ID2D1Layer rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DLayer::m_pLayer](#m_player)|Ukládá ukazatel na objekt ID2D1Layer.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DLayer`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcd2dlayer"></a>CD2DLayer:: ~ CD2DLayer  
 Destruktor. Voláno, když je zničen objektu D2D vrstvy.  
  
```  
virtual ~CD2DLayer();
```  
  
##  <a name="attach"></a>CD2DLayer::Attach  
 Připojí existující prostředek rozhraní k objektu  
  
```  
void Attach(ID2D1Layer* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Existující rozhraní prostředků. Nemůže mít hodnotu NULL  
  
##  <a name="cd2dlayer"></a>CD2DLayer::CD2DLayer  
 Vytvoří objekt CD2DLayer.  
  
```  
CD2DLayer(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Ukazatel na cíl vykreslení.  
  
 `bAutoDestroy`  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
##  <a name="create"></a>CD2DLayer::Create  
 Vytvoří CD2DLayer.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Ukazatel na cíl vykreslení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="destroy"></a>CD2DLayer::Destroy  
 Zničí CD2DLayer objektu.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DLayer::detach  
 Umožňuje odpojit prostředek rozhraní z objektu  
  
```  
ID2D1Layer* Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní odpojit prostředků.  
  
##  <a name="get"></a>CD2DLayer::Get  
 Vrátí ID2D1Layer rozhraní  
  
```  
ID2D1Layer* Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1Layer nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="getsize"></a>CD2DLayer::GetSize  
 Vrátí velikost cíle vykreslení v pixelech nezávislé na zařízení  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální velikost cíle vykreslení v pixelech nezávislé na zařízení  
  
##  <a name="isvalid"></a>CD2DLayer::IsValid  
 Kontrola platnosti prostředků  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud prostředek je platná. jinak hodnota FALSE.  
  
##  <a name="m_player"></a>CD2DLayer::m_pLayer  
 Ukládá ukazatel na objekt ID2D1Layer.  
  
```  
ID2D1Layer* m_pLayer;  
```  
  
##  <a name="operator_id2d1layer_star"></a>CD2DLayer::Operator ID2D1Layer *  
 Vrátí ID2D1Layer rozhraní  
  
```  
operator ID2D1Layer* ();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1Layer nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
