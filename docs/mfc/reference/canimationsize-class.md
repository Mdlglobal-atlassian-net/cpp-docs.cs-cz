---
title: Třída CAnimationSize | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3da7c168cc547ea32f57a145347d8ab2479482a6
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954673"
---
# <a name="canimationsize-class"></a>CAnimationSize – třída
Implementuje funkce velikost objektu může být animovaný jejíž dimenze.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationSize : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationSize::CAnimationSize](#canimationsize)|Přetíženo. Vytvoří objekt velikost animace.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationSize::AddTransition](#addtransition)|Přidá přechody pro šířku a výšku.|  
|[CAnimationSize::GetCX](#getcx)|Poskytuje přístup k CAnimationVariable představující šířku.|  
|[CAnimationSize::GetCY](#getcy)|Poskytuje přístup k CAnimationVariable představující výšku.|  
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro šířku a výšku.|  
|[CAnimationSize::GetValue](#getvalue)|Vrací aktuální hodnotu.|  
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Zařadí do seznamu proměnných zapouzdřené animace. (Přepisuje [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationSize::operator CSize](#operator_csize)|Převede CAnimationSize CSize.|  
|[CAnimationSize::operator =](#operator_eq)|Přiřadí szSrc CAnimationSize.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationSize::m_cxValue](#m_cxvalue)|Obsah zapouzdřeného animace proměnné, která představuje šířku velikosti animace.|  
|[CAnimationSize::m_cyValue](#m_cyvalue)|Obsah zapouzdřeného animace proměnné, která představuje výšku velikosti animace.|  
  
## <a name="remarks"></a>Poznámky  
 Třída CAnimationSize zapouzdří dva objekty CAnimationVariable a může představovat v aplikacích s velikostí. Tuto třídu můžete použít například k animace velikost jakékoliv dva dimenzí objektu na obrazovce (například obdélníku, řídit atd). K použití této třídy v aplikaci, právě vytvoří instanci objektu této třídy, přidejte ji do řadiče animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod má být použita pro šířku a výšku.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationSize` 
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>  CAnimationSize::AddTransition  
 Přidá přechody pro šířku a výšku.  
  
```  
void AddTransition(
    CBaseTransition* pCXTransition,  
    CBaseTransition* pCYTransition);
```  
  
### <a name="parameters"></a>Parametry  
 *pCXTransition*  
 Ukazatel na přechod pro šířku.  
  
 *pCYTransition*  
 Ukazatel na přechodu pro výšku.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce, které chcete přidat zadaný přechody do seznamu interní přechodů má být použita pro proměnné animace pro šířku a výšku. Když přidáte přechody, jejich nejsou použije okamžitě a uložená v interní seznamu. Přechody se použijí (přidané do scénáře pro konkrétní hodnotu) při volání CAnimationController::AnimateGroup. Pokud nemusíte použít přechod na jednu z dimenzí, můžete předat hodnotu NULL.  
  
##  <a name="canimationsize"></a>  CAnimationSize::CAnimationSize  
 Vytvoří objekt velikost animace.  
  
```  
CAnimationSize();

 
CAnimationSize(
    const CSize& szDefault,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *szDefault*  
 Určuje výchozí velikost.  
  
 *nGroupID*  
 Určuje ID skupiny.  
  
 *nObjectID*  
 Určuje ID objektu.  
  
 *dwUserData*  
 Určuje uživatelská data.  
  
### <a name="remarks"></a>Poznámky  
 Objekt je vytvořený pomocí výchozí hodnoty pro šířky, výšky objekt ID a ID skupiny, které bude nastavena na hodnotu 0. Může se změnit později v době běhu pomocí SetDefaultValue a ID sady.  
  
##  <a name="getanimationvariablelist"></a>  CAnimationSize::GetAnimationVariableList  
 Zařadí do seznamu proměnných zapouzdřené animace.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parametry  
 *obrázků*  
 Když funkce vrátí hodnotu, obsahuje odkazy na dva objekty CAnimationVariable představující šířku a výšku.  
  
##  <a name="getcx"></a>  CAnimationSize::GetCX  
 Poskytuje přístup k CAnimationVariable představující šířku.  
  
```  
CAnimationVariable& GetCX();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na obsah zapouzdřeného CAnimationVariable představující šířku.  
  
### <a name="remarks"></a>Poznámky  
 Můžete volat tuto metodu za účelem získání přímý přístup k podkladové CAnimationVariable představující šířku.  
  
##  <a name="getcy"></a>  CAnimationSize::GetCY  
 Poskytuje přístup k CAnimationVariable představující výšku.  
  
```  
CAnimationVariable& GetCY();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na obsah zapouzdřeného CAnimationVariable představující výšku.  
  
### <a name="remarks"></a>Poznámky  
 Můžete volat tuto metodu za účelem získání přímý přístup k podkladové CAnimationVariable představující výšku.  
  
##  <a name="getdefaultvalue"></a>  CAnimationSize::GetDefaultValue  
 Vrátí výchozí hodnoty pro šířku a výšku.  
  
```  
CSize GetDefaultValue();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt CSize obsahující výchozí hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se načíst výchozí hodnotu, která byla dříve nastavena pomocí konstruktoru nebo SetDefaultValue.  
  
##  <a name="getvalue"></a>  CAnimationSize::GetValue  
 Vrací aktuální hodnotu.  
  
```  
BOOL GetValue(CSize& szValue);
```  
  
### <a name="parameters"></a>Parametry  
 *szValue*  
 Výstup. Po návratu tato metoda obsahuje aktuální hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud aktuální hodnota byla úspěšně načtena; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se načíst aktuální hodnotu velikosti animace. Pokud tato metoda selže nebo neinicializovali základní COM – objekty pro šířku a velikost, szValue obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo SetDefaultValue.  
  
##  <a name="m_cxvalue"></a>  CAnimationSize::m_cxValue  
 Obsah zapouzdřeného animace proměnné, která představuje šířku velikosti animace.  
  
```  
CAnimationVariable m_cxValue;  
```  
  
##  <a name="m_cyvalue"></a>  CAnimationSize::m_cyValue  
 Obsah zapouzdřeného animace proměnné, která představuje výšku velikosti animace.  
  
```  
CAnimationVariable m_cyValue;  
```  
  
##  <a name="operator_csize"></a>  CAnimationSize::operator CSize  
 Převede CAnimationSize CSize.  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota velikosti animace jako CSize.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce interně volá GetValue. Pokud GetValue z nějakého důvodu selže, bude vrácená velikost obsahovat výchozí hodnoty pro šířku a výšku.  
  
##  <a name="operator_eq"></a>  CAnimationSize::operator =  
 Přiřadí szSrc CAnimationSize.  
  
```  
void operator=(const CSize& szSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *szSrc*  
 Odkazuje na CSize nebo velikost.  
  
### <a name="remarks"></a>Poznámky  
 Přiřadí szSrc CAnimationSize. Se doporučuje udělat před animace spustit, protože tento operátor volání SetDefaultValue, který vytvoří základní objektů COM pro šířku a výšku, pokud byly vytvořeny. Pokud odebíráte tento objekt animace události (ValueChanged nebo IntegerValueChanged), budete muset znovu povolit tyto události.  
  
##  <a name="setdefaultvalue"></a>  CAnimationSize::SetDefaultValue  
 Nastaví výchozí hodnotu.  
  
```  
void SetDefaultValue(const CSize& szDefault);
```  
  
### <a name="parameters"></a>Parametry  
 *szDefault*  
 Určuje nové výchozí velikost.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete nastavit výchozí hodnotu do objektu animace. Tyto metody přiřadí výchozí hodnoty pro šířku a výšku velikosti animace. Také vytvoří základní objekty modelu COM, pokud byly vytvořeny. Pokud odebíráte tento objekt animace události (ValueChanged nebo IntegerValueChanged), budete muset znovu povolit tyto události.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
