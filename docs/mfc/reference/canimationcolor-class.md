---
title: Třída CAnimationColor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationColor::GetB
- AFXANIMATIONCONTROLLER/CAnimationColor::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetG
- AFXANIMATIONCONTROLLER/CAnimationColor::GetR
- AFXANIMATIONCONTROLLER/CAnimationColor::GetValue
- AFXANIMATIONCONTROLLER/CAnimationColor::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationColor::m_bValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_gValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_rValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationColor [MFC], CAnimationColor
- CAnimationColor [MFC], AddTransition
- CAnimationColor [MFC], GetB
- CAnimationColor [MFC], GetDefaultValue
- CAnimationColor [MFC], GetG
- CAnimationColor [MFC], GetR
- CAnimationColor [MFC], GetValue
- CAnimationColor [MFC], SetDefaultValue
- CAnimationColor [MFC], GetAnimationVariableList
- CAnimationColor [MFC], m_bValue
- CAnimationColor [MFC], m_gValue
- CAnimationColor [MFC], m_rValue
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f564b70e850f3020956711ef15ab1fe9285a6ae4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="canimationcolor-class"></a>CAnimationColor – třída
Implementuje funkce barvu, která může být animovaný jejichž červené, zelené a modré součásti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationColor : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationColor::CAnimationColor](#canimationcolor)|Přetíženo. Vytvoří objekt barvu animace.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationColor::AddTransition](#addtransition)|Přidá přechody pro červená, zelená a modrá součásti.|  
|[CAnimationColor::GetB](#getb)|Poskytuje přístup k CAnimationVariable představující modré součásti.|  
|[CAnimationColor::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro součásti barev.|  
|[CAnimationColor::GetG](#getg)|Poskytuje přístup k CAnimationVariable představující zelená součásti.|  
|[CAnimationColor::GetR](#getr)|Poskytuje přístup k CAnimationVariable představující Red součásti.|  
|[CAnimationColor::GetValue](#getvalue)|Vrací aktuální hodnotu.|  
|[CAnimationColor::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationColor::GetAnimationVariableList](#getanimationvariablelist)|Zařadí do seznamu proměnných zapouzdřené animace. (Přepisuje [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationColor::operator COLORREF](#operator_colorref)||  
|[CAnimationColor::operator =](#operator_eq)|Barva přiřadí CAnimationColor.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationColor::m_bValue](#m_bvalue)|Obsah zapouzdřeného animace proměnné, která představuje Blue součást barvy animace.|  
|[CAnimationColor::m_gValue](#m_gvalue)|Obsah zapouzdřeného animace proměnné, která představuje zelenou součást barvy animace.|  
|[CAnimationColor::m_rValue](#m_rvalue)|Obsah zapouzdřeného animace proměnné, která představuje Red součást barvy animace.|  
  
## <a name="remarks"></a>Poznámky  
 Třída CAnimationColor zapouzdří tři objekty CAnimationVariable a může představovat v aplikacích barvy. Tuto třídu můžete použít například k animace barvy libovolného objektu na obrazovce (například barvy, barva pozadí atd). K použití této třídy v aplikaci, pouze vytvoří instanci objektu této třídy, přidejte k řadiči animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod má být použita pro součásti červená, zelená a modrá.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationColor`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>  CAnimationColor::AddTransition  
 Přidá přechody pro červená, zelená a modrá součásti.  
  
```  
void AddTransition(
    CBaseTransition* pRTransition,  
    CBaseTransition* pGTransition,  
    CBaseTransition* pBTransition);
```  
  
### <a name="parameters"></a>Parametry  
 `pRTransition`  
 Přechodu červenou součásti.  
  
 `pGTransition`  
 Přechod pro zelenou součást.  
  
 `pBTransition`  
 Přechod pro Blue součást.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce lze přidat zadané přechody do seznamu interní přechodů má být použita pro proměnné animace představující součásti barev. Když přidáte přechody, jejich nejsou použije okamžitě a uložená v interní seznamu. Přechody se použijí (přidané do scénáře pro konkrétní hodnotu) při volání CAnimationController::AnimateGroup. Pokud nemusíte použít přechod na jednu z komponenty barvu, můžete předat hodnotu NULL.  
  
##  <a name="canimationcolor"></a>  CAnimationColor::CAnimationColor  
 Vytvoří objekt CAnimationColor.  
  
```  
CAnimationColor();
 
CAnimationColor(
    COLORREF color,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Určuje výchozí barvu.  
  
 `nGroupID`  
 Určuje ID skupiny.  
  
 `nObjectID`  
 Určuje ID objektu.  
  
 `dwUserData`  
 Určuje uživatelská data.  
  
### <a name="remarks"></a>Poznámky  
 Objekt je vytvořený pomocí výchozí hodnoty pro červená, zelená, blue ID objektu a ID skupiny, které bude nastavena na hodnotu 0. Může se změnit později v době běhu pomocí SetDefaultValue a ID sady.  
  
##  <a name="getanimationvariablelist"></a>  CAnimationColor::GetAnimationVariableList  
 Zařadí do seznamu proměnných zapouzdřené animace.  
  
```  
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parametry  
 `lst`  
 Když funkce vrátí hodnotu, obsahuje odkazy na tři objekty CAnimationVariable představující červené, zelené a modré součásti.  
  
##  <a name="getb"></a>  CAnimationColor::GetB  
 Poskytuje přístup k CAnimationVariable představující modré součásti.  
  
```  
CAnimationVariable& GetB();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na zapouzdřené CAnimationVariable představující modré součásti.  
  
### <a name="remarks"></a>Poznámky  
 Můžete volat tuto metodu za účelem získání přímý přístup k podkladové CAnimationVariable představující modré součásti.  
  
##  <a name="getdefaultvalue"></a>  CAnimationColor::GetDefaultValue  
 Vrátí výchozí hodnoty pro součásti barev.  
  
```  
COLORREF GetDefaultValue();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu COLORREF obsahující výchozí hodnoty pro součásti RGB.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se načíst výchozí hodnotu, která byla dříve nastavena pomocí konstruktoru nebo SetDefaultValue.  
  
##  <a name="getg"></a>  CAnimationColor::GetG  
 Poskytuje přístup k CAnimationVariable představující zelená součásti.  
  
```  
CAnimationVariable& GetG();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na obsah zapouzdřeného CAnimationVariable představující zelená komponentu.  
  
### <a name="remarks"></a>Poznámky  
 Můžete volat tuto metodu za účelem získání přímý přístup k podkladové CAnimationVariable představující zelená součásti.  
  
##  <a name="getr"></a>  CAnimationColor::GetR  
 Poskytuje přístup k CAnimationVariable představující Red součásti.  
  
```  
CAnimationVariable& GetR();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na obsah zapouzdřeného CAnimationVariable představující Red součásti.  
  
### <a name="remarks"></a>Poznámky  
 Můžete volat tuto metodu za účelem získání přímý přístup k podkladové CAnimationVariable představující Red součásti.  
  
##  <a name="getvalue"></a>  CAnimationColor::GetValue  
 Vrací aktuální hodnotu.  
  
```  
BOOL GetValue(COLORREF& color);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Výstup. Po návratu tato metoda obsahuje aktuální hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud aktuální hodnota byla úspěšně načtena; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se načíst aktuální hodnotu barvy animace. Pokud tato metoda selže nebo neinicializovali základní COM – objekty pro barvu součásti, barva obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo SetDefaultValue.  
  
##  <a name="m_bvalue"></a>  CAnimationColor::m_bValue  
 Obsah zapouzdřeného animace proměnné, která představuje Blue součást barvy animace.  
  
```  
CAnimationVariable m_bValue;  
```  
  
##  <a name="m_gvalue"></a>  CAnimationColor::m_gValue  
 Obsah zapouzdřeného animace proměnné, která představuje zelenou součást barvy animace.  
  
```  
CAnimationVariable m_gValue;  
```  
  
##  <a name="m_rvalue"></a>  CAnimationColor::m_rValue  
 Obsah zapouzdřeného animace proměnné, která představuje Red součást barvy animace.  
  
```  
CAnimationVariable m_rValue;  
```  
  
##  <a name="operator_colorref"></a>  CAnimationColor::operator COLORREF  
  
```  
operator COLORREF();
```   
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_eq"></a>  CAnimationColor::operator =  
 Barva přiřadí CAnimationColor.  
  
```  
void operator=(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Určuje nová hodnota barvy animace.  
  
### <a name="remarks"></a>Poznámky  
 Se doporučuje udělat před animace spustit, protože tento operátor volání SetDefaultValue, který vytvoří základní objekty modelu COM pro barvu součásti, pokud byly vytvořeny. Pokud odebíráte tento objekt animace události (ValueChanged nebo IntegerValueChanged), budete muset znovu povolit tyto události.  
  
##  <a name="setdefaultvalue"></a>  CAnimationColor::SetDefaultValue  
 Nastaví výchozí hodnotu.  
  
```  
void SetDefaultValue(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Určuje nové výchozí hodnoty pro součásti červené, zelené a modré.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete nastavit výchozí hodnotu do objektu animace. Tyto metody přiřadí výchozí hodnoty barev součástí barvy animace. Také vytvoří základní objekty modelu COM, pokud byly vytvořeny. Pokud odebíráte tento objekt animace události (ValueChanged nebo IntegerValueChanged), budete muset znovu povolit tyto události.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
