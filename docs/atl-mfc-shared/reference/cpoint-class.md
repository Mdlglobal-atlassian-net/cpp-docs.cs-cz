---
title: "Třída CPoint | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
dev_langs: C++
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eb04a51ef9127daa32cb428b058eb6ac7007ba9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cpoint-class"></a>CPoint – třída
Podobně jako Windows `POINT` struktura.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPoint : public tagPOINT 
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPoint::CPoint](#cpoint)|Vytvoří `CPoint`.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPoint::Offset](#offset)|Přidá hodnoty **x** a **y** členy `CPoint`.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPoint::operator-](#operator_-)|Vrátí rozdíl `CPoint` a velikost nebo negace bod nebo velikost rozdíl mezi dvěma body nebo posun podle záporná velikost.|  
|[CPoint::operator! =](#operator_neq)|Kontroluje nerovnost mezi dva body.|  
|[CPoint::operator +](#operator_add)|Vrátí součet `CPoint` a na velikosti nebo bod, nebo `CRect` posunut o velikosti.|  
|[CPoint::operator +=](#operator_add_eq)|Posun `CPoint` přidáním velikost nebo bodu.|  
|[CPoint::operator-=](#operator_-_eq)|Posun `CPoint` odečtením velikost nebo bodu.|  
|[CPoint::operator ==](#operator_eq_eq)|Kontroly rovnosti mezi dva body.|  
  
## <a name="remarks"></a>Poznámky  
 Zahrnuje také členské funkce k manipulaci s `CPoint` a [bodu](../../mfc/reference/point-structure1.md) struktury.  
  
 A `CPoint` objekt lze použít kdekoli `POINT` struktura se používá. Operátory této třídy, které pracují se "velikost" přijmout, buď [CSize](../../atl-mfc-shared/reference/csize-class.md) objekty nebo [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktur, protože zaměnitelné.  
  
> [!NOTE]
>  Tato třída je odvozený od `tagPOINT` struktura. (Název `tagPOINT` je méně často používaná název `POINT` struktura.) To znamená, že data členů `POINT` struktury `x` a `y`, jsou členy dat dostupný `CPoint`.  
  
> [!NOTE]
>  Další informace o sdílených nástroj třídy (jako je `CPoint`), najdete v části [sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `tagPOINT`  
  
 `CPoint`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atltypes.h  
  
##  <a name="cpoint"></a>CPoint::CPoint
 Vytvoří `CPoint` objektu.  
  
```  
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `initX`  
 Určuje hodnotu `x` členem `CPoint`.  
  
 `initY`  
 Určuje hodnotu `y` členem `CPoint`.  
  
 `initPt`  
 [BOD](../../mfc/reference/point-structure1.md) struktura nebo `CPoint` určující hodnoty používané k chybě při inicializaci `CPoint`.  
  
 `initSize`  
 [VELIKOST](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) určující hodnoty používané k chybě při inicializaci `CPoint`.  
  
 `dwPoint`  
 Nastaví `x` člena do aplikace word nejnižší z `dwPoint` a `y` člena do aplikace word horní z `dwPoint`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou zadány žádné argumenty, `x` a `y` členů je nastaven na hodnotu 0.  
  
### <a name="example"></a>Příklad  
  
```cpp   
CPoint   ptTopLeft(0, 0); 
// works from a POINT, too  
 
POINT   ptHere;  
ptHere.x = 35;  
ptHere.y = 95;  
 
CPoint   ptMFCHere(ptHere);
 
// works from a SIZE 
SIZE   sHowBig;  
sHowBig.cx = 300;  
sHowBig.cy = 10;  
 
CPoint ptMFCBig(sHowBig); 
// or from a DWORD  
 
DWORD   dwSize;  
dwSize = MAKELONG(35, 95);
 
CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```  
  
##  <a name="offset"></a>CPoint::Offset  
 Přidá hodnoty **x** a **y** členy `CPoint`.  
  
```  
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *xOffset*  
 Určuje dobu, k posunutí **x** členem `CPoint`.  
  
 *yOffset*  
 Určuje dobu, k posunutí **y** členem `CPoint`.  
  
 `point`  
 Určuje dobu ( [bodu](../../mfc/reference/point-structure1.md) nebo `CPoint`) k posunutí `CPoint`.  
  
 `size`  
 Určuje dobu ( [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) nebo [CSize](../../atl-mfc-shared/reference/csize-class.md)) k posunutí `CPoint`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]  
  
##  <a name="operator_eq_eq"></a>CPoint::operator ==  
 Kontroly rovnosti mezi dva body.  
  
```  
BOOL operator==(POINT point) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Obsahuje [bodu](../../mfc/reference/point-structure1.md) struktura nebo `CPoint` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud body jsou si rovny; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]  
  
##  <a name="operator_neq"></a>CPoint::operator! =  
 Kontroluje nerovnost mezi dva body.  
  
```  
BOOL operator!=(POINT point) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Obsahuje [bodu](../../mfc/reference/point-structure1.md) struktura nebo `CPoint` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud body nejsou stejné; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]  
  
##  <a name="operator_add_eq"></a>CPoint::operator +=  
 První přetížení přidá velikost tak, aby `CPoint`.  
  
```  
void operator+=(SIZE size) throw(); 
void operator+=(POINT point) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Obsahuje [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.  
  
 `point`  
 Obsahuje [bodu](../../mfc/reference/point-structure1.md) struktura nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Druhý přetížení přidá bod, aby `CPoint`.  
  
 V obou případech se přidání provádí přidáním **x** (nebo **cx**) členem pravém operand **x** členem `CPoint` a přidání **y**  (nebo **cy**) členem pravém operand **y** členem `CPoint`.  
  
 Například přidání `CPoint(5, -7)` do proměnné, která obsahuje `CPoint(30, 40)` změny proměnnou `CPoint(35, 33)`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]  
  
##  <a name="operator_-_eq"></a>CPoint::operator-=  
 Odečte první přetížení velikost z `CPoint`.  
  
```  
void operator-=(SIZE size) throw(); 
void operator-=(POINT point) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Obsahuje [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.  
  
 `point`  
 Obsahuje [bodu](../../mfc/reference/point-structure1.md) struktura nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Druhý přetížení odečítá bod ze `CPoint`.  
  
 V obou případech se provádí odčítání odečtením **x** (nebo **cx**) členem pravém operand z **x** členem `CPoint` a odečítání **y** (nebo **cy**) členem pravém operand z **y** členem `CPoint`.  
  
 Například odečtením `CPoint(5, -7)` z proměnné, která obsahuje `CPoint(30, 40)` změny proměnnou `CPoint(25, 47)`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]  
  
##  <a name="operator_add"></a>CPoint::operator +  
 Použít tento operátor pro posun `CPoint` podle `CPoint` nebo `CSize` objekt, nebo k posunutí `CRect` podle `CPoint`.  
  
```  
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Obsahuje [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.  
  
 `point`  
 Obsahuje [bodu](../../mfc/reference/point-structure1.md) struktura nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.  
  
 `lpRect`  
 Obsahuje odkazy [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CPoint` , velikost, posunut **CPoint** bodem, který je posun nebo **CRect** posunut bod.  
  
### <a name="remarks"></a>Poznámky  
 Například pomocí jednoho z první dva přetížení k posunutí bodem `CPoint(25, -19)` bodem `CPoint(15, 5)` nebo velikost `CSize(15, 5)` vrátí hodnotu `CPoint(40, -14)`.  
  
 Přidání obdélníku do bodu vrátí rámeček po se posunut **x** a **y** hodnoty zadané v bodu. Například pomocí poslední přetížení k posunutí obdélníku `CRect(125, 219, 325, 419)` bodem `CPoint(25, -19)` vrátí `CRect(150, 200, 350, 400)`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]  
  
##  <a name="operator_-"></a>CPoint::operator-  
 Použijte jednu z první dva přetížení má odečíst `CPoint` nebo `CSize` objektu z `CPoint`.  
  
```  
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 A [bodu](../../mfc/reference/point-structure1.md) struktura nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objektu.  
  
 `size`  
 A [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.  
  
 `lpRect`  
 Ukazatel [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CSize` který je rozdíl mezi dvěma body `CPoint` je posunut negace velikosti, `CRect` je posunut negace bodu, nebo `CPoint` tedy negace bodu.  
  
### <a name="remarks"></a>Poznámky  
 Třetí přetížení odsazení `CRect` podle negace z `CPoint`. Nakonec pomocí unární operátor negate `CPoint`.  
  
 Například pomocí první přetížení rozdíl mezi dvěma body `CPoint(25, -19)` a `CPoint(15, 5)` vrátí `CSize(10, -24)`.  
  
 Odečtením `CSize` z `CPoint` nemá stejný výpočet, jak je uvedeno výše, ale vrací `CPoint` objektu není `CSize` objektu. Například pomocí druhého přetížení rozdíl mezi bodem `CPoint(25, -19)` a velikost `CSize(15, 5)` vrátí `CPoint(10, -24)`.  
  
 Odečtením obdélníku z bodu vrátí posunutí obdélníku podle negativy z **x** a **y** hodnoty zadané v bodu. Například pomocí poslední přetížení k posunutí rámeček `CRect(125, 200, 325, 400)` bodem `CPoint(25, -19)` vrátí `CRect(100, 219, 300, 419)`.  
  
 Operátor unární negate bod. Například pomocí unárního operátoru s bodem `CPoint(25, -19)` vrátí `CPoint(-25, 19)`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MDI](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [POINT – struktura](../../mfc/reference/point-structure1.md)   
 [CRect – třída](../../atl-mfc-shared/reference/crect-class.md)   
 [CSize – třída](../../atl-mfc-shared/reference/csize-class.md)



