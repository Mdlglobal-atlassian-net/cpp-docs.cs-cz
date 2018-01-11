---
title: "Třída CD2DPathGeometry | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
dev_langs: C++
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9142b268c5f09a88883d048c35287966d9ef8aab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry – třída
Obálka pro ID2D1PathGeometry.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DPathGeometry : public CD2DGeometry;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|Vytvoří objekt CD2DPathGeometry.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DPathGeometry::Attach](#attach)|Připojí existující prostředek rozhraní k objektu|  
|[CD2DPathGeometry::Create](#create)|Vytvoří CD2DPathGeometry. (Přepisuje [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DPathGeometry::Destroy](#destroy)|Zničí CD2DPathGeometry objektu. (Přepisuje [CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|  
|[CD2DPathGeometry::detach](#detach)|Umožňuje odpojit prostředek rozhraní z objektu|  
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|Načte počet číslic v geometrické cestu.|  
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|Načte počet segmentů v geometrické cestu.|  
|[CD2DPathGeometry::Open](#open)|Načte podřízený geometry, který se používá k naplnění geometrie cestu s obrázky a segmentů.|  
|[CD2DPathGeometry::Stream](#stream)|Zkopíruje obsah geometrického cestu do zadané ID2D1GeometrySink.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|Ukazatel ID2D1PathGeometry.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
 `CD2DPathGeometry`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="attach"></a>CD2DPathGeometry::Attach  
 Připojí existující prostředek rozhraní k objektu  
  
```  
void Attach(ID2D1PathGeometry* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Existující rozhraní prostředků. Nemůže mít hodnotu NULL  
  
##  <a name="cd2dpathgeometry"></a>CD2DPathGeometry::CD2DPathGeometry  
 Vytvoří objekt CD2DPathGeometry.  
  
```  
CD2DPathGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Ukazatel na cíl vykreslení.  
  
 `bAutoDestroy`  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
##  <a name="create"></a>CD2DPathGeometry::Create  
 Vytvoří CD2DPathGeometry.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `pRenderTarget`  
 Ukazatel na cíl vykreslení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="destroy"></a>CD2DPathGeometry::Destroy  
 Zničí CD2DPathGeometry objektu.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DPathGeometry::detach  
 Umožňuje odpojit prostředek rozhraní z objektu  
  
```  
ID2D1PathGeometry* Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní odpojit prostředků.  
  
##  <a name="getfigurecount"></a>CD2DPathGeometry::GetFigureCount  
 Načte počet číslic v geometrické cestu.  
  
```  
int GetFigureCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet číslic v geometrické cestu.  
  
##  <a name="getsegmentcount"></a>CD2DPathGeometry::GetSegmentCount  
 Načte počet segmentů v geometrické cestu.  
  
```  
int GetSegmentCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet segmentů v geometrické cestu.  
  
##  <a name="m_ppathgeometry"></a>CD2DPathGeometry::m_pPathGeometry  
 Ukazatel ID2D1PathGeometry.  
  
```  
ID2D1PathGeometry* m_pPathGeometry;  
```  
  
##  <a name="open"></a>CD2DPathGeometry::Open  
 Načte podřízený geometry, který se používá k naplnění geometrie cestu s obrázky a segmentů.  
  
```  
ID2D1GeometrySink* Open();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na ID2D1GeometrySink, který se používá k naplnění geometrie cestu s obrázky a segmentů.  
  
##  <a name="stream"></a>CD2DPathGeometry::Stream  
 Zkopíruje obsah geometrického cestu do zadané ID2D1GeometrySink.  
  
```  
BOOL Stream(ID2D1GeometrySink* geometrySink);
```  
  
### <a name="parameters"></a>Parametry  
 `geometrySink`  
 Podřízený, ke kterému se zkopírují geometrie Cesta obsahu. Úprava tento podřízený nezmění obsah geometrického této cesty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
