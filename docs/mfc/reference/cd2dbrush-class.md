---
title: Třída CD2DBrush | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DBrush
- AFXRENDERTARGET/CD2DBrush
- AFXRENDERTARGET/CD2DBrush::CD2DBrush
- AFXRENDERTARGET/CD2DBrush::Attach
- AFXRENDERTARGET/CD2DBrush::Destroy
- AFXRENDERTARGET/CD2DBrush::Detach
- AFXRENDERTARGET/CD2DBrush::Get
- AFXRENDERTARGET/CD2DBrush::GetOpacity
- AFXRENDERTARGET/CD2DBrush::GetTransform
- AFXRENDERTARGET/CD2DBrush::IsValid
- AFXRENDERTARGET/CD2DBrush::SetOpacity
- AFXRENDERTARGET/CD2DBrush::SetTransform
- AFXRENDERTARGET/CD2DBrush::m_pBrush
- AFXRENDERTARGET/CD2DBrush::m_pBrushProperties
dev_langs:
- C++
helpviewer_keywords:
- CD2DBrush [MFC], CD2DBrush
- CD2DBrush [MFC], Attach
- CD2DBrush [MFC], Destroy
- CD2DBrush [MFC], Detach
- CD2DBrush [MFC], Get
- CD2DBrush [MFC], GetOpacity
- CD2DBrush [MFC], GetTransform
- CD2DBrush [MFC], IsValid
- CD2DBrush [MFC], SetOpacity
- CD2DBrush [MFC], SetTransform
- CD2DBrush [MFC], m_pBrush
- CD2DBrush [MFC], m_pBrushProperties
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95fdd973d94c0d60e5e3177260740c5d62f1ea5b
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078553"
---
# <a name="cd2dbrush-class"></a>CD2DBrush – třída
Obálka pro ID2D1Brush.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DBrush : public CD2DResource;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBrush::CD2DBrush](#cd2dbrush)|Vytvoří objekt CD2DBrush.|  
|[CD2DBrush:: ~ CD2DBrush](#_dtorcd2dbrush)|Destruktor. Voláno, když je zničen objektu D2D štětce.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBrush::Attach](#attach)|Připojí existující prostředek rozhraní k objektu|  
|[CD2DBrush::Destroy](#destroy)|Zničí CD2DBrush objektu. (Přepisuje [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DBrush::detach](#detach)|Umožňuje odpojit prostředek rozhraní z objektu|  
|[CD2DBrush::Get](#get)|Vrátí ID2D1Brush rozhraní|  
|[CD2DBrush::GetOpacity](#getopacity)|Získá stupeň krytí tento stopy|  
|[CD2DBrush::GetTransform](#gettransform)|Získá aktuální transformace vykreslení cíle|  
|[CD2DBrush::IsValid](#isvalid)|Ověří platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DBrush::SetOpacity](#setopacity)|Nastaví úroveň krytí tento stopy|  
|[CD2DBrush::SetTransform](#settransform)|Zadaná transformace se vztahuje na cíl vykreslování, nahraďte existující transformace. Všechny následné kreslení operace dojít v transformovaných prostoru|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBrush::Operator ID2D1Brush *](#operator_id2d1brush_star)|Vrátí ID2D1Brush rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBrush::m_pBrush](#m_pbrush)|Ukládá ukazatel na objekt ID2D1Brush.|  
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|Štětce vlastnosti.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DBrush`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcd2dbrush"></a>  CD2DBrush:: ~ CD2DBrush  
 Destruktor. Voláno, když je zničen objektu D2D štětce.  
  
```  
virtual ~CD2DBrush();
```  
  
##  <a name="attach"></a>  CD2DBrush::Attach  
 Připojí existující prostředek rozhraní k objektu.  
  
```  
void Attach(ID2D1Brush* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 *pResource*  
 Existující rozhraní prostředků. Nemůže mít hodnotu NULL.  
  
##  <a name="cd2dbrush"></a>  CD2DBrush::CD2DBrush  
 Vytvoří objekt CD2DBrush.  
  
```  
CD2DBrush(
    CRenderTarget* pParentTarget,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentTarget*  
 Ukazatel na cíl vykreslení.  
  
 *pBrushProperties*  
 Ukazatel na krytí a transformace štětce.  
  
 *bAutoDestroy*  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
##  <a name="destroy"></a>  CD2DBrush::Destroy  
 Zničí CD2DBrush objektu.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DBrush::detach  
 Umožňuje odpojit prostředek rozhraní z objektu.  
  
```  
ID2D1Brush* Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní odpojit prostředků.  
  
##  <a name="get"></a>  CD2DBrush::Get  
 Vrátí ID2D1Brush rozhraní  
  
```  
ID2D1Brush* Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1Brush nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="getopacity"></a>  CD2DBrush::GetOpacity  
 Získá stupeň krytí tento stopy  
  
```  
FLOAT GetOpacity() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota mezi 0 a 1, která určuje krytí stopy. Tato hodnota je konstantní násobitel, který škáluje lineárně alfa sestavil stopy všechny pixelů. Krytí hodnoty jsou v rozsahu od 0 do 1 těsně před se násobí společně.  
  
##  <a name="gettransform"></a>  CD2DBrush::GetTransform  
 Získá aktuální transformace vykreslení cíle  
  
```  
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *transformace*  
 Pokud tento příkaz vrátí, obsahuje aktuální transformace vykreslení cíle. Tento parametr je předán bez inicializace.  
  
##  <a name="isvalid"></a>  CD2DBrush::IsValid  
 Kontrola platnosti prostředků  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud prostředek je platná. jinak hodnota FALSE.  
  
##  <a name="m_pbrush"></a>  CD2DBrush::m_pBrush  
 Ukládá ukazatel na objekt ID2D1Brush.  
  
```  
ID2D1Brush* m_pBrush;  
```  
  
##  <a name="m_pbrushproperties"></a>  CD2DBrush::m_pBrushProperties  
 Štětce vlastnosti.  
  
```  
CD2DBrushProperties* m_pBrushProperties;  
```  
  
##  <a name="operator_id2d1brush_star"></a>  CD2DBrush::Operator ID2D1Brush *  
 Vrátí ID2D1Brush rozhraní  
  
```  
operator ID2D1Brush*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1Brush nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="setopacity"></a>  CD2DBrush::SetOpacity  
 Nastaví úroveň krytí tento stopy  
  
```  
void SetOpacity(FLOAT opacity);
```  
  
### <a name="parameters"></a>Parametry  
 *Neprůhlednost.*  
 Hodnota mezi 0 a 1, která určuje krytí stopy. Tato hodnota je konstantní násobitel, který škáluje lineárně alfa sestavil stopy všechny pixelů. Krytí hodnoty jsou v rozsahu od 0 do 1 těsně před se násobí společně.  
  
##  <a name="settransform"></a>  CD2DBrush::SetTransform  
 Zadaná transformace se vztahuje na cíl vykreslování, nahraďte existující transformace. Všechny následné kreslení operace dojít v transformovaných prostoru.  
  
```  
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```  
  
### <a name="parameters"></a>Parametry  
 *transformace*  
 Transformace použít k vykreslení cíli  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
