---
title: "Třída CD2DGeometry | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::Attach
- AFXRENDERTARGET/CD2DGeometry::CombineWithGeometry
- AFXRENDERTARGET/CD2DGeometry::CompareWithGeometry
- AFXRENDERTARGET/CD2DGeometry::ComputeArea
- AFXRENDERTARGET/CD2DGeometry::ComputeLength
- AFXRENDERTARGET/CD2DGeometry::ComputePointAtLength
- AFXRENDERTARGET/CD2DGeometry::Destroy
- AFXRENDERTARGET/CD2DGeometry::Detach
- AFXRENDERTARGET/CD2DGeometry::FillContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Get
- AFXRENDERTARGET/CD2DGeometry::GetBounds
- AFXRENDERTARGET/CD2DGeometry::GetWidenedBounds
- AFXRENDERTARGET/CD2DGeometry::IsValid
- AFXRENDERTARGET/CD2DGeometry::Outline
- AFXRENDERTARGET/CD2DGeometry::Simplify
- AFXRENDERTARGET/CD2DGeometry::StrokeContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Tessellate
- AFXRENDERTARGET/CD2DGeometry::Widen
- AFXRENDERTARGET/CD2DGeometry::m_pGeometry
dev_langs: C++
helpviewer_keywords:
- CD2DGeometry [MFC], CD2DGeometry
- CD2DGeometry [MFC], Attach
- CD2DGeometry [MFC], CombineWithGeometry
- CD2DGeometry [MFC], CompareWithGeometry
- CD2DGeometry [MFC], ComputeArea
- CD2DGeometry [MFC], ComputeLength
- CD2DGeometry [MFC], ComputePointAtLength
- CD2DGeometry [MFC], Destroy
- CD2DGeometry [MFC], Detach
- CD2DGeometry [MFC], FillContainsPoint
- CD2DGeometry [MFC], Get
- CD2DGeometry [MFC], GetBounds
- CD2DGeometry [MFC], GetWidenedBounds
- CD2DGeometry [MFC], IsValid
- CD2DGeometry [MFC], Outline
- CD2DGeometry [MFC], Simplify
- CD2DGeometry [MFC], StrokeContainsPoint
- CD2DGeometry [MFC], Tessellate
- CD2DGeometry [MFC], Widen
- CD2DGeometry [MFC], m_pGeometry
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 02a0b36d01a14b6765d8169caa1966297b759658
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cd2dgeometry-class"></a>CD2DGeometry – třída
Obálka pro ID2D1Geometry.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DGeometry : public CD2DResource;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Vytvoří objekt CD2DGeometry.|  
|[CD2DGeometry:: ~ CD2DGeometry](#_dtorcd2dgeometry)|Destruktor. Voláno, když je zničen geometrický objekt D2D.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DGeometry::Attach](#attach)|Připojí existující prostředek rozhraní k objektu|  
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Kombinuje tento geometrie pomocí zadaná geometrie a výsledek je uložen ve ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|Popisuje průnik mezi tato geometrie a zadaná geometrie. Porovnání se provádí pomocí zadané sloučení tolerance.|  
|[CD2DGeometry::ComputeArea](#computearea)|Vypočítá oblasti geometrického útvaru. po jejím transformovat zadaný matice a průmětu pomocí zadané tolerance.|  
|[CD2DGeometry::ComputeLength](#computelength)|Vypočítá délku geometrie, jako by byl každý segment unrolled na čáru.|  
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Vypočítá bod a tangens vektoru v zadané vzdálenosti podél geometrie po jejím transformovat zadaný matice a průmětu pomocí zadané tolerance.|  
|[CD2DGeometry::Destroy](#destroy)|Zničí CD2DGeometry objektu. (Přepisuje [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DGeometry::detach](#detach)|Umožňuje odpojit prostředek rozhraní z objektu|  
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Určuje, zda oblasti sestavil geometrie by obsahovat zadaný bod zadané zadanou toleranci sloučení.|  
|[CD2DGeometry::Get](#get)|Vrátí ID2D1Geometry rozhraní|  
|[CD2DGeometry::GetBounds](#getbounds)||  
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Získá hranice geometrického útvaru. poté, co byla rozšířit zadaný tahu šířkou a stylu a transformovat zadaný matice.|  
|[CD2DGeometry::IsValid](#isvalid)|Ověří platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DGeometry::Outline](#outline)|Vypočítá obrys geometrie a zapíše výsledek ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::Simplify](#simplify)|Vytvoří zjednodušenou verzi geometry, který obsahuje pouze řádky a (volitelně) krychlový Bézierových křivek a zapíše výsledek ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Určuje, zda geometrie tahu obsahuje zadaný bod daného sílu tahu zadaný, styl a transformace.|  
|[CD2DGeometry::Tessellate](#tessellate)|Vytvoří sadu trojúhelníčky po směru hodinových ručiček vinutým, které zahrnují geometrie po byla transformována, pomocí zadané matice a průmětu pomocí zadané tolerance.|  
|[CD2DGeometry::widen](#widen)|Rozšiřuje geometrie podle zadaného tahu a zapíše výsledek ID2D1SimplifiedGeometrySink po jejím transformovat zadaný matice a průmětu pomocí zadané tolerance.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DGeometry::Operator ID2D1Geometry *](#operator_id2d1geometry_star)|Vrátí ID2D1Geometry rozhraní|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|Ukazatel ID2D1Geometry.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DGeometry`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometry"></a>CD2DGeometry:: ~ CD2DGeometry  
 Destruktor. Voláno, když je zničen geometrický objekt D2D.  
  
```  
virtual ~CD2DGeometry();
```  
  
##  <a name="attach"></a>CD2DGeometry::Attach  
 Připojí existující prostředek rozhraní k objektu  
  
```  
void Attach(ID2D1Geometry* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 `pResource`  
 Existující rozhraní prostředků. Nemůže mít hodnotu NULL  
  
##  <a name="cd2dgeometry"></a>CD2DGeometry::CD2DGeometry  
 Vytvoří objekt CD2DGeometry.  
  
```  
CD2DGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Ukazatel na cíl vykreslení.  
  
 `bAutoDestroy`  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
##  <a name="combinewithgeometry"></a>CD2DGeometry::CombineWithGeometry  
 Kombinuje tento geometrie pomocí zadaná geometrie a výsledek je uložen ve ID2D1SimplifiedGeometrySink.  
  
```  
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,  
    D2D1_COMBINE_MODE combineMode,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `inputGeometry`  
 Geometrie kombinovat s touto instancí.  
  
 `combineMode`  
 Typ operaci combine k provedení.  
  
 `inputGeometryTransform`  
 Transformace, které chcete použít pro inputGeometry před kombinování.  
  
 `geometrySink`  
 Výsledek operaci combine.  
  
 `flatteningTolerance`  
 Maximální rozsah na vzdálenost mezi body v polygonálních sblížení geometrie. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="comparewithgeometry"></a>CD2DGeometry::CompareWithGeometry  
 Popisuje průnik mezi tato geometrie a zadaná geometrie. Porovnání se provádí pomocí zadané sloučení tolerance.  
  
```  
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `inputGeometry`  
 Geometrie k testování.  
  
 `inputGeometryTransform`  
 Transformace, které chcete použít pro inputGeometry.  
  
 `flatteningTolerance`  
 Maximální rozsah na vzdálenost mezi body v polygonálních sblížení geometrie. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="computearea"></a>CD2DGeometry::ComputeArea  
 Vypočítá oblasti geometrického útvaru. po jejím transformovat zadaný matice a průmětu pomocí zadané tolerance.  
  
```  
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& area,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `worldTransform`  
 Transformace, které chcete použít pro tento geometrické obrazce před computing jeho oblasti.  
  
 `area`  
 Po návratu tato metoda obsahuje ukazatel na oblasti transformovaných, plochou verzi této geometrie. Musíte přidělit úložiště pro tento parametr.  
  
 `flatteningTolerance`  
 Maximální rozsah na vzdálenost mezi body v polygonálních aproximace geometrického útvaru. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="computelength"></a>CD2DGeometry::ComputeLength  
 Vypočítá délku geometrie, jako by byl každý segment unrolled na čáru.  
  
```  
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& length,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `worldTransform`  
 Transformace, které chcete použít pro geometrie před výpočet jeho délka.  
  
 `length`  
 Po návratu tato metoda obsahuje ukazatel na délku geometrického útvaru. Pro uzavřené geometrie délka obsahuje segment implicitní ukončovací. Musíte přidělit úložiště pro tento parametr.  
  
 `flatteningTolerance`  
 Maximální rozsah na vzdálenost mezi body v polygonálních aproximace geometrického útvaru. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="computepointatlength"></a>CD2DGeometry::ComputePointAtLength  
 Vypočítá bod a tangens vektoru v zadané vzdálenosti podél geometrie po jejím transformovat zadaný matice a průmětu pomocí zadané tolerance.  
  
```  
BOOL ComputePointAtLength(
    FLOAT length,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DPointF& point,  
    CD2DPointF& unitTangentVector,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `length`  
 Vzdálenost podél geometrie bodu a tangens najít. Pokud tato vzdálenost menší pak 0, tato metoda vypočítá prvního bodu v geometrie. Pokud tato vzdálenost je větší než délka geometrie, tato metoda vypočítá posledního bodu v geometrie.  
  
 `worldTransform`  
 Transformace, které chcete použít pro geometrie před výpočtem Zadaný bod a tangens.  
  
 `point`  
 Umístění v zadané vzdálenosti podél geometrie. Pokud geometrie je prázdný, obsahuje tento bod NaN jako jeho x a y hodnoty.  
  
 `unitTangentVector`  
 Po návratu tato metoda obsahuje ukazatel na tečný vektoru v zadané vzdálenosti podél geometrie. Pokud geometrie je prázdný, obsahuje tento vektoru NaN jako jeho x a y hodnoty. Musíte přidělit úložiště pro tento parametr.  
  
 `flatteningTolerance`  
 Maximální rozsah na vzdálenost mezi body v polygonálních aproximace geometrického útvaru. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="destroy"></a>CD2DGeometry::Destroy  
 Zničí CD2DGeometry objektu.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DGeometry::detach  
 Umožňuje odpojit prostředek rozhraní z objektu  
  
```  
ID2D1Geometry* Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní odpojit prostředků.  
  
##  <a name="fillcontainspoint"></a>CD2DGeometry::FillContainsPoint  
 Určuje, zda oblasti sestavil geometrie by obsahovat zadaný bod zadané zadanou toleranci sloučení.  
  
```  
BOOL FillContainsPoint(
    CD2DPointF point,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    BOOL* contains,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Bod, který chcete otestovat.  
  
 `worldTransform`  
 Transformace, které chcete použít pro geometrie před testování pro členství ve skupině.  
  
 `contains`  
 Po návratu tato metoda obsahuje hodnotu bool, který má hodnotu TRUE, pokud oblasti sestavil geometrie obsahuje čárky. jinak hodnota FALSE. Musíte přidělit úložiště pro tento parametr.  
  
 `flatteningTolerance`  
 Číselná přesnost, pomocí kterého přesné geometrickou cesty a cesty průnik se počítá. Chybějící výplně menší než tolerance body jsou považovány za stále uvnitř. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="get"></a>CD2DGeometry::Get  
 Vrátí ID2D1Geometry rozhraní  
  
```  
ID2D1Geometry* Get();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1Geometry nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="getbounds"></a>CD2DGeometry::GetBounds  
  
```   
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,  
CD2DRectF& bounds) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `worldTransform`  
 `bounds`  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="getwidenedbounds"></a>CD2DGeometry::GetWidenedBounds  
 Získá hranice geometrického útvaru. poté, co byla rozšířit zadaný tahu šířkou a stylu a transformovat zadaný matice.  
  
```  
BOOL GetWidenedBounds(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DRectF& bounds,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strokeWidth`  
 Hodnota, o který rozšíří geometrie podle vytažení jeho outline.  
  
 `strokeStyle`  
 Styl tahu, která rozšiřuje geometrie.  
  
 `worldTransform`  
 Transformace použít geometrie po transformaci geometrie a po geometrie byla vytažený..  
  
 `bounds`  
 Po návratu tato metoda obsahuje rozsah rozšířené geometrického útvaru. Musíte přidělit úložiště pro tento parametr.  
  
 `flatteningTolerance`  
 Maximální rozsah na vzdálenost mezi body v polygonálních sblížení geometrie. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="isvalid"></a>CD2DGeometry::IsValid  
 Kontrola platnosti prostředků  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud prostředek je platná. jinak hodnota FALSE.  
  
##  <a name="m_pgeometry"></a>CD2DGeometry::m_pGeometry  
 Ukazatel ID2D1Geometry.  
  
```  
ID2D1Geometry* m_pGeometry;  
```  
  
##  <a name="operator_id2d1geometry_star"></a>CD2DGeometry::Operator ID2D1Geometry *  
 Vrátí ID2D1Geometry rozhraní  
  
```  
operator ID2D1Geometry*();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1Geometry nebo hodnota NULL, pokud objekt dosud není inicializován.  
  
##  <a name="outline"></a>CD2DGeometry::Outline  
 Vypočítá obrys geometrie a zapíše výsledek ID2D1SimplifiedGeometrySink.  
  
```  
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `worldTransform`  
 Transformace, které chcete použít pro obrys geometrie.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink, ke kterému se připojí transformovaných obrys geometrie.  
  
 `flatteningTolerance`  
 Maximální rozsah na vzdálenost mezi body v polygonálních aproximace geometrického útvaru. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="simplify"></a>CD2DGeometry::Simplify  
 Vytvoří zjednodušenou verzi geometry, který obsahuje pouze řádky a (volitelně) krychlový Bézierových křivek a zapíše výsledek ID2D1SimplifiedGeometrySink.  
  
```  
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `simplificationOption`  
 Hodnota, která určuje, zda zjednodušené geometrie by měl obsahovat křivek.  
  
 `worldTransform`  
 Transformace, které chcete použít pro zjednodušené geometrie.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink, ke kterému se připojí zjednodušené geometrie.  
  
 `flatteningTolerance`  
 Maximální rozsah na vzdálenost mezi body v polygonálních aproximace geometrického útvaru. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="strokecontainspoint"></a>CD2DGeometry::StrokeContainsPoint  
 Určuje, zda geometrie tahu obsahuje zadaný bod daného sílu tahu zadaný, styl a transformace.  
  
```  
BOOL StrokeContainsPoint(
    CD2DPointF point,  
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    BOOL* contains,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Bod, který chcete otestovat členství ve skupině.  
  
 `strokeWidth`  
 Tloušťka tahu použít.  
  
 `strokeStyle`  
 Styl tahu použít.  
  
 `worldTransform`  
 Transformace, které chcete použít pro vytažené geometrie.  
  
 `contains`  
 Po návratu tato metoda obsahuje logickou hodnotu nastavit na hodnotu TRUE, pokud geometrie tahu obsahuje zadaný bod; jinak hodnota FALSE. Musíte přidělit úložiště pro tento parametr.  
  
 `flatteningTolerance`  
 Číselná přesnost, pomocí kterého přesné geometrickou cesty a cesty průnik se počítá. Chybějící tahu menší než tolerance body jsou považovány za stále uvnitř. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="tessellate"></a>CD2DGeometry::Tessellate  
 Vytvoří sadu trojúhelníčky po směru hodinových ručiček vinutým, které zahrnují geometrie po byla transformována, pomocí zadané matice a průmětu pomocí zadané tolerance.  
  
```  
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1TessellationSink* tessellationSink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `worldTransform`  
 Transformace, které chcete použít pro tento geometry, nebo hodnota NULL.  
  
 `tessellationSink`  
 ID2D1TessellationSink, ke kterému teselace sestavy se připojí.  
  
 `flatteningTolerance`  
 Maximální rozsah na vzdálenost mezi body v polygonálních aproximace geometrického útvaru. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
##  <a name="widen"></a>CD2DGeometry::widen  
 Rozšiřuje geometrie podle zadaného tahu a zapíše výsledek ID2D1SimplifiedGeometrySink po jejím transformovat zadaný matice a průmětu pomocí zadané tolerance.  
  
```  
BOOL Widen(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strokeWidth`  
 Hodnota, o který rozšíří geometrie.  
  
 `strokeStyle`  
 Styl tahu aplikovat na geometry, nebo hodnotu NULL.  
  
 `worldTransform`  
 Transformace se použije k geometrie po rozšíření ho.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink, ke kterému se připojí rozšířené geometrie.  
  
 `flatteningTolerance`  
 Maximální rozsah na vzdálenost mezi body v polygonálních aproximace geometrického útvaru. Menší hodnoty poskytuje přesnější výsledky ale způsobit pomalejší provádění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí hodnotu TRUE. V opačném případě vrátí hodnotu FALSE.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
