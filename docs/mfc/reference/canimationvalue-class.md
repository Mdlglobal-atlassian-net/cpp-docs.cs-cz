---
title: "Třída CAnimationValue | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationValue::GetValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationValue::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationValue::m_value
dev_langs: C++
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6abda25cf23e83873d1611e45f78ef7c51e87709
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="canimationvalue-class"></a>CAnimationValue – třída
Implementuje funkce animace objektu, který má jednu hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationValue : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationValue::CAnimationValue](#canimationvalue)|Přetíženo. Vytvoří objekt CAnimationValue.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationValue::AddTransition](#addtransition)|Přidá přechod má být použita pro hodnotu.|  
|[CAnimationValue::GetValue](#getvalue)|Přetíženo. Načte aktuální hodnotu.|  
|[CAnimationValue::GetVariable](#getvariable)|Poskytuje přístup k proměnné zapouzdřené animace.|  
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Vloží proměnnou zapouzdřené animace do seznamu. (Přepisuje [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationValue::operator DOUBLE](#operator_double)|Poskytuje převody mezi CAnimationValue a DVOJITOU hodnotu.|  
|[CAnimationValue::operator INT32](#operator_int32)|Poskytuje převody mezi CAnimationValue a INT32.|  
|[CAnimationValue::operator =](#operator_eq)|Přetíženo. Přiřadí hodnoty INT32 CAnimationValue.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationValue::m_value](#m_value)|Obsah zapouzdřeného animace proměnné, která představuje hodnotu animace.|  
  
## <a name="remarks"></a>Poznámky  
 Třída CAnimationValue zapouzdří jednoho objektu CAnimationVariable a může představovat v aplikacích animovaný jedné hodnoty. Například můžete použít tuto třídu pro animovaný průhlednost (objevování účinek), úhel (Chcete-li otočit objekty), nebo u všech ostatních případech, když potřebujete vytvořit animace v závislosti na animovaný jedné hodnoty. K použití této třídy v aplikaci, právě vytvoří instanci objektu této třídy, přidejte ji do řadiče animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod má být použita pro hodnotu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationValue`
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationValue::AddTransition  
 Přidá přechod má být použita pro hodnotu.  
  
```  
void AddTransition(CBaseTransition* pTransition);
```  
  
### <a name="parameters"></a>Parametry  
 `pTransition`  
 Ukazatel na přechod objektu.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce můžete přidat přechod do interní seznamu přechodů má být použita pro proměnnou animace. Když přidáte přechody, jejich nejsou použije okamžitě a uložená v interní seznamu. Přechody se použijí (přidané do scénáře pro konkrétní hodnotu) při volání CAnimationController::AnimateGroup.  
  
##  <a name="canimationvalue"></a>CAnimationValue::CAnimationValue  
 Vytvoří objekt CAnimationValue.  
  
```  
CAnimationValue();

 
CAnimationValue(
    DOUBLE dblDefaultValue,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `dblDefaultValue`  
 Určuje výchozí hodnotu.  
  
 `nGroupID`  
 Určuje ID skupiny.  
  
 `nObjectID`  
 Určuje ID objektu.  
  
 `dwUserData`  
 Určuje uživatelská data.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří objekt CAnimationValue s výchozí vlastnosti: výchozí, ID skupiny a ID objektu je nastavena na hodnotu 0.  
  
##  <a name="getanimationvariablelist"></a>CAnimationValue::GetAnimationVariableList  
 Vloží proměnnou zapouzdřené animace do seznamu.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parametry  
 `lst`  
 Když funkce vrátí hodnotu, obsahuje ukazatel na CAnimationVariable představující animovaný hodnotu.  
  
##  <a name="getvalue"></a>CAnimationValue::GetValue  
 Načte aktuální hodnotu.  
  
```  
BOOL GetValue(DOUBLE& dblValue);  
BOOL GetValue(INT32& nValue);
```  
  
### <a name="parameters"></a>Parametry  
 `dblValue`  
 Výstup. Když funkce vrátí hodnotu obsahuje aktuální hodnotu proměnné animace.  
  
 `nValue`  
 Výstup. Když funkce vrátí hodnotu obsahuje aktuální hodnotu proměnné animace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud aktuální hodnota byl načteny; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se načíst aktuální hodnotu. Tato implementace volá zapouzdřené objektu COM, a pokud volání selže, vrátí tato metoda výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo s SetDefaultValue.  
  
##  <a name="getvariable"></a>CAnimationValue::GetVariable  
 Poskytuje přístup k proměnné zapouzdřené animace.  
  
```  
CAnimationVariable& GetVariable();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na proměnnou zapouzdřené animace.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte pro přístup k proměnné zapouzdřené animace. Z CAnimationVariable získat přístup k základní IUIAnimationVariable objekt, jehož ukazatel může mít hodnotu NULL, pokud nebyla vytvořena proměnná animace.  
  
##  <a name="m_value"></a>CAnimationValue::m_value  
 Obsah zapouzdřeného animace proměnné, která představuje hodnotu animace.  
  
```  
CAnimationVariable m_value;  
```  
  
##  <a name="operator_double"></a>CAnimationValue::operator DOUBLE  
 Poskytuje převody mezi CAnimationValue a DVOJITOU hodnotu.  
  
```  
operator DOUBLE();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota hodnoty animace.  
  
### <a name="remarks"></a>Poznámky  
 Poskytuje převody mezi CAnimationValue a DVOJITOU hodnotu. Interně tato metoda volá GetValue a neohlásí chyby. Pokud GetValue selže, bude vrácená hodnota obsahovat výchozí hodnotu, dříve nastavené v konstruktoru nebo s SetDefaultValue.  
  
##  <a name="operator_int32"></a>CAnimationValue::operator INT32  
 Poskytuje převody mezi CAnimationValue a INT32.  
  
```  
operator INT32();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota animace hodnoty jako celé číslo.  
  
### <a name="remarks"></a>Poznámky  
 Poskytuje převody mezi CAnimationValue a INT32. Interně tato metoda volá GetValue a neohlásí chyby. Pokud GetValue selže, bude vrácená hodnota obsahovat výchozí hodnotu, dříve nastavené v konstruktoru nebo s SetDefaultValue.  
  
##  <a name="operator_eq"></a>CAnimationValue::operator =  
 Hodnota typu DOUBLE přiřadí CAnimationValue.  
  
```  
void operator=(DOUBLE dblVal);  
void operator=(INT32 nVal);
```  
  
### <a name="parameters"></a>Parametry  
 `dblVal`  
 Určuje hodnotu přiřazení hodnoty animace.  
  
 `nVal`  
 Určuje hodnotu přiřazení hodnoty animace.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota typu DOUBLE přiřadí CAnimationValue. Tato hodnota nastavena jako výchozí hodnotu pro proměnnou zapouzdřené animace. Pokud odebíráte tento objekt animace události (ValueChanged nebo IntegerValueChanged), budete muset znovu povolit tyto události.  
  
##  <a name="setdefaultvalue"></a>CAnimationValue::SetDefaultValue  
 Nastaví výchozí hodnotu.  
  
```  
void SetDefaultValue(DOUBLE dblDefaultValue);
```  
  
### <a name="parameters"></a>Parametry  
 `dblDefaultValue`  
 Určuje výchozí hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li nastavit výchozí hodnotu. Výchozí hodnota je vrácen do aplikace, pokud animace nebyl spuštěn a/nebo základní objekt COM nebyl vytvořen. Pokud již bylo vytvořeno základní objekt COM zapouzdřené v CAnimationVarible, znovu vytvoří tuto metodu, proto možná budete muset volat metody EnableValueChanged nebo EnableIntegerValueChanged znovu.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
