---
title: "Třída CSize | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
dev_langs:
- C++
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ac18decc8a2bb6bbc2d9e9677640eba67c85077e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="csize-class"></a>CSize – třída
Podobně jako Windows [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura, která implementuje relativní souřadnice nebo pozice.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSize : public tagSIZE 
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSize::CSize](#csize)|Vytvoří `CSize` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSize::operator-](#operator_-)|Odečítá od dvě velikosti.|  
|[CSize::operator! =](#operator_neq)|Kontroluje nerovnost mezi `CSize` a velikost.|  
|[CSize::operator +](#operator_add)|Přidá dvě velikosti.|  
|[CSize::operator +=](#operator_add_eq)|Přidá velikost tak, aby `CSize`.|  
|[CSize::operator-=](#operator_-_eq)|Odečítá od velikost z `CSize`.|  
|[CSize::operator ==](#operator_eq_eq)|Kontroluje rovnosti mezi `CSize` a velikost.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je odvozený od **velikost** struktura. To znamená, že můžete předat `CSize` v parametru, který volá pro **velikost** a že data členů **velikost** struktura jsou členy dat dostupný `CSize`.  
  
 **Cx** a **cy** členy **velikost** (a `CSize`) jsou veřejné. Kromě toho `CSize` implementuje členské funkce k manipulaci s **velikost** struktura.  
  
> [!NOTE]
>  Další informace o sdílených nástroj třídy (jako je `CSize`), najdete v části [sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `tagSIZE`  
  
 `CSize`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atltypes.h  
  
##  <a name="csize"></a>CSize::CSize  
 Vytvoří `CSize` objektu.  
  
```  
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 *initCX*  
 Nastaví **cx** člena `CSize`.  
  
 *initCY*  
 Nastaví **cy** člena `CSize`.  
  
 `initSize`  
 [VELIKOST](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura nebo `CSize` objekt použitý k inicializaci `CSize`.  
  
 `initPt`  
 [BOD](../../mfc/reference/point-structure1.md) struktura nebo `CPoint` objekt použitý k inicializaci `CSize`.  
  
 `dwSize`  
 `DWORD`použitý k inicializaci `CSize`. Je slovo nejnižší **cx** člena a horní slovo je **cy** člen.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou zadány žádné argumenty, **cx** a **cy** jsou inicializovány na nulu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]  
  
##  <a name="operator_eq_eq"></a>CSize::operator ==  
 Kontroly rovnosti mezi dvěma velikosti.  
  
```   
BOOL operator==(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí nenulové hodnoty, pokud jsou si rovny velikosti, otherwize 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]  
  
##  <a name="operator_neq"></a>CSize::operator! =  
 Kontroluje nerovnost mezi dvěma velikosti.  
  
```   
BOOL operator!=(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí nenulové hodnoty, pokud velikosti nejsou stejné, jinak hodnota 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]  
  
##  <a name="operator_add_eq"></a>CSize::operator +=  
 Přidá k tomuto velikost `CSize`.  
  
```   
void operator+=(SIZE size) throw(); 
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]  
  
##  <a name="operator_-_eq"></a>CSize::operator-=  
 Odečítá od velikost z tohoto `CSize`.  
  
```   
void operator-=(SIZE size) throw(); 
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]  
  
##  <a name="operator_add"></a>CSize::operator +  
 Přidejte tyto operátory `CSize` hodnotu na hodnotu parametru.  
  
```   
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw(); 
```  
  
### <a name="remarks"></a>Poznámky  
 V následujících popisech jednotlivých operátory:  
  
- **operátor + (** `size` **)**tuto operaci přidá dva `CSize` hodnoty.  
  
- **operátor + (** `point` **)**tuto operaci posune (přesune) [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) (nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) hodnotu to `CSize` hodnotu. **Cx** a **cy** členy této `CSize` hodnotu jsou přidány do **x** a **y** členy data **bodu**  hodnotu. Je to analogie verzi [CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) , která má [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametr.  
  
- **operátor + (** `lpRect` **)**tuto operaci posune (přesune) [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) (nebo [CRect](../../atl-mfc-shared/reference/crect-class.md)) hodnotu to `CSize` hodnotu. **Cx** a **cy** členy této `CSize` hodnotu jsou přidány do **levém**, **horní**, **vpravo**, a **dolní** datových členů `RECT` hodnotu. Je to analogie verzi [CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) , která má [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametr.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]  
  
##  <a name="operator_-"></a>CSize::operator-  
 První tři tyto operátory odečtena to `CSize` hodnotu na hodnotu parametru.  
  
```   
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Čtvrtý operátor Unární minus, změní znaménko `CSize` hodnotu. V následujících popisech jednotlivých operátory:  
  
- **-– operátor (** `size` **)**tuto operaci odečítá dva `CSize` hodnoty.  
  
- **-– operátor (** `point` **)**tuto operaci posune (přesune) [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) hodnoty doplňkové inverzní to `CSize` hodnota. **Cx** a **cy** tohoto `CSize` hodnota je odečten od **x** a **y** členy data **bodu**  hodnotu. Je to analogie verzi [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) , která má [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametr.  
  
- **-– operátor (** `lpRect` **)**tuto operaci posune (přesune) [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) hodnoty doplňkové inverzní to `CSize` hodnota. **Cx** a **cy** členy této `CSize` hodnota je odečten od **levém**, **horní**, **vpravo**, a **dolní** datových členů `RECT` hodnotu. Je to analogie verzi [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) , která má [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametr.  
  
- **operátor-()**tuto operaci Vrátí inverzní hodnotu doplňkové tohoto `CSize` hodnotu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MDI](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CRect – třída](../../atl-mfc-shared/reference/crect-class.md)   
 [CPoint – třída](../../atl-mfc-shared/reference/cpoint-class.md)

