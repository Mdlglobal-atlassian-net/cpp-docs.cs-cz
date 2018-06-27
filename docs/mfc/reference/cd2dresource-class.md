---
title: Třída CD2DResource | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
dev_langs:
- C++
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1848e0fe6d3e09ea4707279e83293ae2dc0feb64
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950674"
---
# <a name="cd2dresource-class"></a>CD2DResource – třída
Abstraktní třída, která poskytuje rozhraní pro vytváření a Správa prostředků D2D například štětce, vrstvy a texty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DResource : public CObject;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DResource::CD2DResource](#cd2dresource)|Vytvoří objekt CD2DResource.|  
|[CD2DResource:: ~ CD2DResource](#cd2dresource__~cd2dresource)|Destruktor. Voláno, když je zničen objektu D2D prostředků.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DResource::Create](#create)|Vytvoří CD2DResource.|  
|[CD2DResource::Destroy](#destroy)|Zničí CD2DResource objektu.|  
|[CD2DResource::IsValid](#isvalid)|Kontrola platnosti prostředků|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DResource::IsAutoDestroy](#isautodestroy)|Kontrola automaticky zrušte příznak.|  
|[CD2DResource::ReCreate](#recreate)|Znovu vytvoří CD2DResource.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|Prostředků bude destoyed vlastník (CRenderTarget)|  
|[CD2DResource::m_pParentTarget](#m_pparenttarget)|Ukazatel na hodnotu parent CRenderTarget)|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CD2DResource`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcd2dresource"></a>  CD2DResource:: ~ CD2DResource  
 Destruktor. Voláno, když je zničen objektu D2D prostředků.  
  
```  
virtual ~CD2DResource();
```  
  
##  <a name="cd2dresource"></a>  CD2DResource::CD2DResource  
 Vytvoří objekt CD2DResource.  
  
```  
CD2DResource(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentTarget*  
 Ukazatel na cíl vykreslení.  
  
 *bAutoDestroy*  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
##  <a name="create"></a>  CD2DResource::Create  
 Vytvoří CD2DResource.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *pRenderTarget*  
 Ukazatel na cíl vykreslení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="destroy"></a>  CD2DResource::Destroy  
 Zničí CD2DResource objektu.  
  
```  
virtual void Destroy() = 0;  
```  
  
##  <a name="isautodestroy"></a>  CD2DResource::IsAutoDestroy  
 Kontrola automaticky zrušte příznak.  
  
```  
BOOL IsAutoDestroy() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud objekt budou zničena jeho vlastníka; jinak hodnota FALSE.  
  
##  <a name="isvalid"></a>  CD2DResource::IsValid  
 Kontrola platnosti prostředků  
  
```  
virtual BOOL IsValid() const = 0;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud prostředek je platná. jinak hodnota FALSE.  
  
##  <a name="m_bisautodestroy"></a>  CD2DResource::m_bIsAutoDestroy  
 Prostředků bude destoyed vlastník (CRenderTarget)  
  
```  
BOOL m_bIsAutoDestroy;  
```  
  
##  <a name="m_pparenttarget"></a>  CD2DResource::m_pParentTarget  
 Ukazatel na hodnotu parent CRenderTarget)  
  
```  
CRenderTarget* m_pParentTarget;  
```  
  
##  <a name="recreate"></a>  CD2DResource::ReCreate  
 Znovu vytvoří CD2DResource.  
  
```  
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 *pRenderTarget*  
 Ukazatel na cíl vykreslení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
