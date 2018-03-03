---
title: "Třída CAnimationPoint | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetX
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetY
- AFXANIMATIONCONTROLLER/CAnimationPoint::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_xValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_yValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationPoint [MFC], CAnimationPoint
- CAnimationPoint [MFC], AddTransition
- CAnimationPoint [MFC], GetDefaultValue
- CAnimationPoint [MFC], GetValue
- CAnimationPoint [MFC], GetX
- CAnimationPoint [MFC], GetY
- CAnimationPoint [MFC], SetDefaultValue
- CAnimationPoint [MFC], GetAnimationVariableList
- CAnimationPoint [MFC], m_xValue
- CAnimationPoint [MFC], m_yValue
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ab685c223c4a86c35ba0feb578d93f58844734b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="canimationpoint-class"></a>CAnimationPoint – třída
Implementuje funkce, které může být animovaný jejichž souřadnice bodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationPoint : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|Přetíženo. Vytvoří objekt CAnimationPoint.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationPoint::AddTransition](#addtransition)|Přidá přechody pro X a Y souřadnice.|  
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro X a Y souřadnice.|  
|[CAnimationPoint::GetValue](#getvalue)|Vrací aktuální hodnotu.|  
|[CAnimationPoint::GetX](#getx)|Poskytuje přístup k CAnimationVariable pro souřadnici X.|  
|[CAnimationPoint::GetY](#gety)|Poskytuje přístup k CAnimationVariable pro souřadnici Y.|  
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Zařadí do seznamu proměnných zapouzdřené animace. (Přepisuje [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationPoint::operator CPoint](#operator_cpoint)|Převede CAnimationPoint CPoint.|  
|[CAnimationPoint::operator =](#operator_eq)|Přiřadí ptSrc CAnimationPoint.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationPoint::m_xValue](#m_xvalue)|Obsah zapouzdřeného animace proměnné, která představuje X souřadnice bodu animace.|  
|[CAnimationPoint::m_yValue](#m_yvalue)|Obsah zapouzdřeného animace proměnné, která představuje souřadnici Y bodu animace.|  
  
## <a name="remarks"></a>Poznámky  
 Třída CAnimationPoint zapouzdří dva objekty CAnimationVariable a může představovat v aplikacích bod. Tuto třídu můžete například použít pro animaci pozice všech objektů na obrazovce (například textový řetězec, kruh, bod atd). Tato třída slouží v aplikaci, právě vytvoří instanci objektu této třídy, přidejte ji do řadiče animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod má být použita pro souřadnice X a Y.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationPoint`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationPoint::AddTransition  
 Přidá přechody pro X a Y souřadnice.  
  
```  
void AddTransition(
    CBaseTransition* pXTransition,  
    CBaseTransition* pYTransition);
```  
  
### <a name="parameters"></a>Parametry  
 `pXTransition`  
 Ukazatel na přechodu pro souřadnice X.  
  
 `pYTransition`  
 Ukazatel na přechodu pro Y koordinovat.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce, které chcete přidat zadané přechody do seznamu interní přechodů má být použita pro proměnné animace pro X a Y souřadnice. Když přidáte přechody, jejich nejsou použije okamžitě a uložená v interní seznamu. Přechody se použijí (přidané do scénáře pro konkrétní hodnotu) při volání CAnimationController::AnimateGroup. Pokud nemusíte použít přechod na jednu z souřadnice, lze předat hodnotu NULL.  
  
##  <a name="canimationpoint"></a>CAnimationPoint::CAnimationPoint  
 Vytvoří objekt CAnimationPoint.  
  
```  
CAnimationPoint();

 
CAnimationPoint(
    const CPoint& ptDefault,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `ptDefault`  
 Určuje souřadnice bodu výchozí.  
  
 `nGroupID`  
 Určuje ID skupiny.  
  
 `nObjectID`  
 Určuje ID objektu.  
  
 `dwUserData`  
 Určuje uživatelská data.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří objekt CAnimationPoint s výchozí vlastnosti: výchozí bod souřadnice, ID skupiny a ID objektu jsou nastaveny na hodnotu 0.  
  
##  <a name="getanimationvariablelist"></a>CAnimationPoint::GetAnimationVariableList  
 Zařadí do seznamu proměnných zapouzdřené animace.  
  
```  
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parametry  
 `lst`  
 Když funkce vrátí hodnotu, obsahuje odkazy na dva objekty CAnimationVariable představující souřadnice X a Y.  
  
##  <a name="getdefaultvalue"></a>CAnimationPoint::GetDefaultValue  
 Vrátí výchozí hodnoty pro X a Y souřadnice.  
  
```  
CPoint GetDefaultValue();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Bod obsahující výchozí hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se načíst výchozí hodnotu, která byla dříve nastavena pomocí konstruktoru nebo SetDefaultValue.  
  
##  <a name="getvalue"></a>CAnimationPoint::GetValue  
 Vrací aktuální hodnotu.  
  
```  
BOOL GetValue(CPoint& ptValue);
```  
  
### <a name="parameters"></a>Parametry  
 `ptValue`  
 Výstup. Po návratu tato metoda obsahuje aktuální hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud aktuální hodnota byla úspěšně načtena; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se načíst aktuální hodnotu bodu animace. Pokud tato metoda selže nebo základní COM objekty pro X a Y souřadnice nebyly inicializovány, ptValue obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo SetDefaultValue.  
  
##  <a name="getx"></a>CAnimationPoint::GetX  
 Poskytuje přístup k CAnimationVariable pro souřadnici X.  
  
```  
CAnimationVariable& GetX();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na obsah zapouzdřeného CAnimationVariable představující X koordinaci.  
  
### <a name="remarks"></a>Poznámky  
 Můžete volat tuto metodu za účelem získání přímý přístup k podkladové CAnimationVariable představující X koordinaci.  
  
##  <a name="gety"></a>CAnimationPoint::GetY  
 Poskytuje přístup k CAnimationVariable pro souřadnici Y.  
  
```  
CAnimationVariable& GetY();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na obsah zapouzdřeného CAnimationVariable představující souřadnici Y.  
  
### <a name="remarks"></a>Poznámky  
 Můžete volat tuto metodu za účelem získání přímý přístup k podkladové CAnimationVariable představující souřadnici Y.  
  
##  <a name="m_xvalue"></a>CAnimationPoint::m_xValue  
 Obsah zapouzdřeného animace proměnné, která představuje X souřadnice bodu animace.  
  
```  
CAnimationVariable m_xValue;  
```  
  
##  <a name="m_yvalue"></a>CAnimationPoint::m_yValue  
 Obsah zapouzdřeného animace proměnné, která představuje souřadnici Y bodu animace.  
  
```  
CAnimationVariable m_yValue;  
```  
  
##  <a name="operator_cpoint"></a>CAnimationPoint::operator CPoint  
 Převede CAnimationPoint CPoint.  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota CAnimationPoint jako CPoint.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce interně volá GetValue. Pokud GetValue z nějakého důvodu selže, bude vrácená bodu obsahovat výchozí hodnoty pro X a Y souřadnice.  
  
##  <a name="operator_eq"></a>CAnimationPoint::operator =  
 Přiřadí ptSrc CAnimationPoint.  
  
```  
void operator=(const CPoint& ptSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `ptSrc`  
 Odkazuje na CPoint nebo bodu.  
  
### <a name="remarks"></a>Poznámky  
 Přiřadí ptSrc CAnimationPoint. Se doporučuje se, že před animace start a vzhledem k tomu tento operátor volání SetDefaultValue, který vytvoří základní COM objekty pro souřadnice X a Y Pokud byly vytvořeny. Pokud odebíráte tento objekt animace události (ValueChanged nebo IntegerValueChanged), budete muset znovu povolit tyto události.  
  
##  <a name="setdefaultvalue"></a>CAnimationPoint::SetDefaultValue  
 Nastaví výchozí hodnotu.  
  
```  
void SetDefaultValue(const POINT& ptDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `ptDefault`  
 Určuje hodnotu, výchozí bod.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete nastavit výchozí hodnotu do objektu animace. Toto výchozí nastavení přiřadí metody hodnoty k souřadnice X a Y bodu animace. Také vytvoří základní objekty modelu COM, pokud byly vytvořeny. Pokud odebíráte tento objekt animace události (ValueChanged nebo IntegerValueChanged), budete muset znovu povolit tyto události.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
