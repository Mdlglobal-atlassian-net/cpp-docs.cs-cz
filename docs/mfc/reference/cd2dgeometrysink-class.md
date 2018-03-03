---
title: "Třída CD2DGeometrySink | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89286aaccd2c59efb2bac14978a2d8838af7a4e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink – třída
Obálka pro ID2D1GeometrySink.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DGeometrySink;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Vytvoří objekt CD2DGeometrySink z CD2DPathGeometry objektu.|  
|[CD2DGeometrySink:: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|Destruktor. Voláno, když je zničen objektu D2D geometrie podřízený.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DGeometrySink::AddArc](#addarc)|Přidá jeden oblouk geometrie cesta|  
|[CD2DGeometrySink::AddBezier](#addbezier)|Vytvoří krychlový Bézierovu křivku mezi bodem aktuální a zadaný koncový bod.|  
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Vytvoří posloupnost krychlový Bézierových křivek a přidá je do geometrie jímky.|  
|[CD2DGeometrySink::AddLine](#addline)|Vytvoří segment řádek mezi bodem aktuální a zadaný koncový bod a přidává ji k geometrie jímky.|  
|[CD2DGeometrySink::AddLines](#addlines)|Vytvoří pořadí čar pomocí uvedených bodů a přidá je do geometrie jímky.|  
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Vytvoří kvadratické Bézierovy křivky mezi bodem aktuální a zadaný koncový bod.|  
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Přidá posloupnost kvadratické Bézierovy segmentů jako pole v jediném volání.|  
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Spustí novou obrázek na zadaný bod.|  
|[CD2DGeometrySink::Close](#close)|Zavře jímky geometrie|  
|[CD2DGeometrySink::EndFigure](#endfigure)|Končí na aktuální obrázku; Volitelně zavře.|  
|[CD2DGeometrySink::Get](#get)|Vrátí ID2D1GeometrySink rozhraní|  
|[CD2DGeometrySink::IsValid](#isvalid)|Kontroluje, geometry podřízený platnosti|  
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Určuje metodu sloužící k určení, které jsou bodů v geometrické popsaného tento podřízený geometrie a které body jsou mimo.|  
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Určuje tahu a připojení k možnosti, které má být použita pro nové segmenty, které jsou přidány do geometrie jímky.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DGeometrySink::Operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|Vrátí ID2D1GeometrySink rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DGeometrySink::m_pSink](#m_psink)|Ukazatel ID2D1GeometrySink.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CD2DGeometrySink`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink:: ~ CD2DGeometrySink  
 Destruktor. Voláno, když je zničen objektu D2D geometrie podřízený.  
  
```  
virtual ~CD2DGeometrySink();
```  
  
##  <a name="addarc"></a>CD2DGeometrySink::AddArc  
 Přidá jeden oblouk geometrie cesta  
  
```  
void AddArc(const D2D1_ARC_SEGMENT& arc);
```  
  
### <a name="parameters"></a>Parametry  
 `arc`  
 Segment oblouk pro přidání do obrázku  
  
##  <a name="addbezier"></a>CD2DGeometrySink::AddBezier  
 Vytvoří krychlový Bézierovu křivku mezi bodem aktuální a zadaný koncový bod.  
  
```  
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>Parametry  
 `bezier`  
 Struktura, která popisuje kontrolních bodů a koncového bodu Bézierovy křivky přidat.  
  
##  <a name="addbeziers"></a>CD2DGeometrySink::AddBeziers  
 Vytvoří posloupnost krychlový Bézierových křivek a přidá je do geometrie jímky.  
  
```  
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,  
    D2D1_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>Parametry  
 `beziers`  
 Pole Bézierovy segmentů, které popisuje Bézierových křivek vytvořit. Křivka vykreslením z aktuální bodu podřízený Geometrie (koncový bod poslední segment vykreslovat nebo umístění, které BeginFigure) pro koncový bod první segment Bézierovy křivky v poli. Pokud pole obsahuje další Bézierovy segmenty, každý další segment Bézierovy používá koncový bod předchozího segmentu Bézierovy jako počáteční bod.  
  
##  <a name="addline"></a>CD2DGeometrySink::AddLine  
 Vytvoří segment řádek mezi bodem aktuální a zadaný koncový bod a přidává ji k geometrie jímky.  
  
```  
void AddLine(CD2DPointF point);
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Koncový bod řádku k vykreslení.  
  
##  <a name="addlines"></a>CD2DGeometrySink::AddLines  
 Vytvoří pořadí čar pomocí uvedených bodů a přidá je do geometrie jímky.  
  
```  
void AddLines(
    const CArray<CD2DPointF,  
    CD2DPointF>& points);
```  
  
### <a name="parameters"></a>Parametry  
 `points`  
 Pole jeden nebo více bodů, které popisují, řádky určené k vykreslení. Řádek je znázorněna od geometrie podřízený aktuálnímu bodu (koncový bod poslední segment vykreslovat nebo umístění, které BeginFigure) do prvního bodu v poli. Pokud pole obsahuje další body, řádek vykreslením z prvního bodu na druhý bod v poli, z druhý bod do třetí bodu a tak dále. Pole pořadí koncových bodů čar k vykreslení.  
  
##  <a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier  
 Vytvoří kvadratické Bézierovy křivky mezi bodem aktuální a zadaný koncový bod.  
  
```  
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>Parametry  
 `bezier`  
 Struktura, která popisuje řídicí bod a koncovým bodem kvadratické Bézierovy křivky přidat.  
  
##  <a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers  
 Přidá posloupnost kvadratické Bézierovy segmentů jako pole v jediném volání.  
  
```  
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,  
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>Parametry  
 `beziers`  
 Pole pořadí kvadratické Bézierovy segmentů.  
  
##  <a name="beginfigure"></a>CD2DGeometrySink::BeginFigure  
 Spustí novou obrázek na zadaný bod.  
  
```  
void BeginFigure(
    CD2DPointF startPoint,  
    D2D1_FIGURE_BEGIN figureBegin);
```  
  
### <a name="parameters"></a>Parametry  
 `startPoint`  
 Bod, od kterého má začít nový obrázek.  
  
 `figureBegin`  
 Jestli nový obrázek by měl být prázdné nebo vyplněné.  
  
##  <a name="cd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink  
 Vytvoří objekt CD2DGeometrySink z CD2DPathGeometry objektu.  
  
```  
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```  
  
### <a name="parameters"></a>Parametry  
 `pathGeometry`  
 Existující objekt CD2DPathGeometry.  
  
##  <a name="close"></a>CD2DGeometrySink::Close  
 Zavře jímky geometrie  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota FALSE.  
  
##  <a name="endfigure"></a>CD2DGeometrySink::EndFigure  
 Končí na aktuální obrázku; Volitelně zavře.  
  
```  
void EndFigure(D2D1_FIGURE_END figureEnd);
```  
  
### <a name="parameters"></a>Parametry  
 `figureEnd`  
 Hodnota, která označuje, zda aktuální obrázek je uzavřený. Pokud na obrázku je zavřená, je mezi bodem aktuální a počáteční bod určeného BeginFigure vykresluje řádku.  
  
##  <a name="get"></a>CD2DGeometrySink::Get  
 Vrátí ID2D1GeometrySink rozhraní  
  
```  
ID2D1GeometrySink* Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1GeometrySink nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="isvalid"></a>CD2DGeometrySink::IsValid  
 Kontroluje, geometry podřízený platnosti  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud podřízený geometry je platný; jinak hodnota FALSE.  
  
##  <a name="m_psink"></a>CD2DGeometrySink::m_pSink  
 Ukazatel ID2D1GeometrySink.  
  
```  
ID2D1GeometrySink* m_pSink;  
```  
  
##  <a name="operator_id2d1geometrysink_star"></a>CD2DGeometrySink::Operator ID2D1GeometrySink *  
 Vrátí ID2D1GeometrySink rozhraní  
  
```  
operator ID2D1GeometrySink*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1GeometrySink nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="setfillmode"></a>CD2DGeometrySink::SetFillMode  
 Určuje metodu sloužící k určení, které jsou bodů v geometrické popsaného tento podřízený geometrie a které body jsou mimo.  
  
```  
void SetFillMode(D2D1_FILL_MODE fillMode);
```  
  
### <a name="parameters"></a>Parametry  
 `fillMode`  
 Metoda použitá k určení, zda je k danému bodu součástí geometrie.  
  
##  <a name="setsegmentflags"></a>CD2DGeometrySink::SetSegmentFlags  
 Určuje tahu a připojení k možnosti, které má být použita pro nové segmenty, které jsou přidány do geometrie jímky.  
  
```  
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `vertexFlags`  
 Možnosti tahu a spojení má být použita pro nové segmenty, které jsou přidány do geometrie jímky.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
