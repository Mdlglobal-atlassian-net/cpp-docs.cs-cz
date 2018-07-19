---
title: Csize – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0494b22d3166ebfd75a6aeaceba839f80b84bc1
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884402"
---
# <a name="csize-class"></a>Csize – třída
Podobně jako Windows [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura, která implementuje relativní souřadnice nebo pozici.  
  
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
|[CSize::operator-](#operator_-)|Odečte dvou velikostech.|  
|[CSize::operator! =](#operator_neq)|Zkontroluje nerovnost mezi `CSize` a velikost.|  
|[CSize::operator +](#operator_add)|Přidá dvě velikosti.|  
|[CSize::operator +=](#operator_add_eq)|Přidá velikost pro `CSize`.|  
|[CSize::operator-=](#operator_-_eq)|Odečte velikost z `CSize`.|  
|[CSize::operator ==](#operator_eq_eq)|Vyhledá rovnost mezi `CSize` a velikost.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je odvozena z `SIZE` struktury. To znamená, že můžete předat `CSize` parametrem, který volá `SIZE` a datové členy `SIZE` struktury jsou dostupné datové členy `CSize`.  
  
 `cx` a `cy` členy `SIZE` (a `CSize`) jsou veřejné. Kromě toho `CSize` implementuje členské funkce pro manipulaci s `SIZE` struktury.  
  
> [!NOTE]
>  Další informace o sdílené třídy nástroje (jako je `CSize`), najdete v článku [sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `tagSIZE`  
  
 `CSize`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atltypes.h  
  
##  <a name="csize"></a>  CSize::CSize  
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
 Nastaví `cx` člena `CSize`.  
  
 *initCY*  
 Nastaví `cy` člena `CSize`.  
  
 *initSize*  
 [VELIKOST](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury nebo `CSize` objekt použitý k inicializaci `CSize`.  
  
 *initPt*  
 [BOD](../../mfc/reference/point-structure1.md) struktury nebo `CPoint` objekt použitý k inicializaci `CSize`.  
  
 *dwSize*  
 DWORD použitý k inicializaci `CSize`. Je nižší řád slova `cx` člen a vyšší řád slova je `cy` člena.  
  
### <a name="remarks"></a>Poznámky  
 Pokud nejsou zadány žádné argumenty, `cx` a `cy` jsou inicializovány na nulu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]  
  
##  <a name="operator_eq_eq"></a>  CSize::operator ==  
 Kontroly pro rovnost mezi dvěma formáty.  
  
```   
BOOL operator==(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí nenulovou hodnotu, pokud jsou stejné velikosti, otherwize 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]  
  
##  <a name="operator_neq"></a>  CSize::operator! =  
 Kontroly pro nerovnost mezi dvěma formáty.  
  
```   
BOOL operator!=(SIZE size) const throw(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí nenulovou hodnotu, pokud velikosti nejsou stejné, jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]  
  
##  <a name="operator_add_eq"></a>  CSize::operator +=  
 Přidá k tomuto velikost `CSize`.  
  
```   
void operator+=(SIZE size) throw(); 
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]  
  
##  <a name="operator_-_eq"></a>  CSize::operator-=  
 Odečte velikost z tohoto `CSize`.  
  
```   
void operator-=(SIZE size) throw(); 
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]  
  
##  <a name="operator_add"></a>  CSize::operator +  
 Přidejte tyto operátory `CSize` hodnotu k hodnotě parametru.  
  
```   
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw(); 
```  
  
### <a name="remarks"></a>Poznámky  
 V následujících popisech jednotlivé operátory:  
  
- **operátor + (** `size` **)** tato operace přidá dvě `CSize` hodnoty.  
  
- **operátor + (** `point` **)** tuto operaci posun (přesun) [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) (nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) hodnotu situace `CSize` hodnotu. **Cx** a **cy** členy tohoto `CSize` hodnoty se přidají do **x** a **y** datové členy **bodu**  hodnotu. Je obdobou verzi [CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) , která přijímá [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametru.  
  
- **operátor + (** `lpRect` **)** tuto operaci posun (přesun) [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) (nebo [crect –](../../atl-mfc-shared/reference/crect-class.md)) hodnotu situace `CSize` hodnotu. **Cx** a **cy** členy tohoto `CSize` hodnoty se přidají do **levé**, **horní**, **vpravo**, a **dolní** datové členy `RECT` hodnotu. Je obdobou verzi [CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) , která přijímá [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]  
  
##  <a name="operator_-"></a>  CSize::operator-  
 První tři z těchto operátorů odečíst to `CSize` hodnotu k hodnotě parametru.  
  
```   
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Čtvrtý operátor Unární minus, změní znaménko `CSize` hodnotu. V následujících popisech jednotlivé operátory:  
  
- **operátor-(** `size` **)** tuto operaci odečte dvě `CSize` hodnoty.  
  
- **operátor-(** `point` **)** tuto operaci posun (přesun) [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) nebo [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) hodnoty additive inverzní to `CSize` hodnota. **Cx** a **cy** tohoto `CSize` jsou hodnota odečtena od **x** a **y** datové členy **bodu**  hodnotu. Je obdobou verzi [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) , která přijímá [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametr.  
  
- **operátor-(** `lpRect` **)** tuto operaci posun (přesun) [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) nebo [crect –](../../atl-mfc-shared/reference/crect-class.md) hodnoty additive inverzní to `CSize` hodnotu. **Cx** a **cy** členy tohoto `CSize` jsou hodnota odečtena od **levé**, **horní**, **vpravo**, a **dolní** datové členy `RECT` hodnotu. Je obdobou verzi [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) , která přijímá [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) parametr.  
  
- **operátor-()** tato operace Vrátí inverzní additive tohoto `CSize` hodnotu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC MDI](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Crect – třída](../../atl-mfc-shared/reference/crect-class.md)   
 [CPoint – třída](../../atl-mfc-shared/reference/cpoint-class.md)

