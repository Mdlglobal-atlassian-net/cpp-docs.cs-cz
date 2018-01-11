---
title: "Třída CAnimationRect | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
dev_langs: C++
helpviewer_keywords:
- CAnimationRect [MFC], CAnimationRect
- CAnimationRect [MFC], AddTransition
- CAnimationRect [MFC], GetBottom
- CAnimationRect [MFC], GetDefaultValue
- CAnimationRect [MFC], GetLeft
- CAnimationRect [MFC], GetRight
- CAnimationRect [MFC], GetTop
- CAnimationRect [MFC], GetValue
- CAnimationRect [MFC], SetDefaultValue
- CAnimationRect [MFC], GetAnimationVariableList
- CAnimationRect [MFC], m_bFixedSize
- CAnimationRect [MFC], m_bottomValue
- CAnimationRect [MFC], m_leftValue
- CAnimationRect [MFC], m_rightValue
- CAnimationRect [MFC], m_szInitial
- CAnimationRect [MFC], m_topValue
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b38b1225dbce3f747efeaa7aa1e5384f7931efe0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="canimationrect-class"></a>CAnimationRect – třída
Implementuje funkce obdélníku, jehož strany může být animace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationRect : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationRect::CAnimationRect](#canimationrect)|Přetíženo. Vytvoří objekt Rect – animace.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationRect::AddTransition](#addtransition)|Přidá přechodů mezi pro vlevo, horní, pravé a dolní souřadnice.|  
|[CAnimationRect::GetBottom](#getbottom)|Poskytuje přístup k CAnimationVariable představující souřadnice dolního.|  
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Vrátí výchozí hodnoty pro obdélníku hranice.|  
|[CAnimationRect::GetLeft](#getleft)|Poskytuje přístup k CAnimationVariable představující levou souřadnici.|  
|[CAnimationRect::GetRight](#getright)|Poskytuje přístup k CAnimationVariable představující správné souřadnice.|  
|[CAnimationRect::GetTop](#gettop)|Poskytuje přístup k CAnimationVariable představující horní souřadnici.|  
|[CAnimationRect::GetValue](#getvalue)|Vrací aktuální hodnotu.|  
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Nastaví výchozí hodnotu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Zařadí do seznamu proměnných zapouzdřené animace. (Přepisuje [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Rect – CAnimationRect::operator](#operator_rect)|Převede CAnimationRect obdélníkový|  
|[CAnimationRect::operator =](#operator_eq)|Rect – přiřadí CAnimationRect.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Určuje, zda rámeček má pevnou velikost.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|Obsah zapouzdřeného animace proměnné, která představuje dolní hranice elementu obdélníku animace.|  
|[CAnimationRect::m_leftValue](#m_leftvalue)|Obsah zapouzdřeného animace proměnné, která představuje vlevo hranice elementu obdélníku animace.|  
|[CAnimationRect::m_rightValue](#m_rightvalue)|Obsah zapouzdřeného animace proměnné, která představuje vpravo hranice elementu obdélníku animace.|  
|[CAnimationRect::m_szInitial](#m_szinitial)|Určuje počáteční velikost obdélníku animace.|  
|[CAnimationRect::m_topValue](#m_topvalue)|Obsah zapouzdřeného animace proměnné, která představuje horní hranice elementu obdélníku animace.|  
  
## <a name="remarks"></a>Poznámky  
 Třída CAnimationRect zapouzdří čtyři CAnimationVariable objekty a může představovat v aplikacích obdélníku. K použití této třídy v aplikaci, pouze vytvoří instanci objektu této třídy, přidejte k řadiči animace pomocí CAnimationController::AddAnimationObject a volání AddTransition pro každý přechod, který bude použit na levé, pravé horní a dolní souřadnice.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationRect`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationRect::AddTransition  
 Přidá přechodů mezi pro vlevo, horní, pravé a dolní souřadnice.  
  
```  
void AddTransition(
    CBaseTransition* pLeftTransition,  
    CBaseTransition* pTopTransition,  
    CBaseTransition* pRightTransition,  
    CBaseTransition* pBottomTransition);
```  
  
### <a name="parameters"></a>Parametry  
 `pLeftTransition`  
 Určuje přechodu pro levé straně.  
  
 `pTopTransition`  
 Určuje přechodu pro horní straně.  
  
 `pRightTransition`  
 Určuje přechodu pro pravé straně.  
  
 `pBottomTransition`  
 Určuje přechodu pro dole.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce lze přidat zadané přechody do seznamu interní přechodů má být použita pro animace proměnných pro každý rámeček stranách. Když přidáte přechody, jejich nejsou použije okamžitě a uložená v interní seznamu. Přechody se použijí (přidané do scénáře pro konkrétní hodnotu) při volání CAnimationController::AnimateGroup. Pokud nemusíte vztahují přechod na jeden rámeček postranní, můžete předat hodnotu NULL.  
  
##  <a name="canimationrect"></a>CAnimationRect::CAnimationRect  
 Vytvoří objekt CAnimationRect.  
  
```  
CAnimationRect();

 
CAnimationRect(
    const CRect& rect,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);

 
CAnimationRect(
    const CPoint& pt,  
    const CSize& sz,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);

 
CAnimationRect(
    int nLeft,  
    int nTop,  
    int nRight,  
    int nBottom,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Určuje výchozí obdélník.  
  
 `nGroupID`  
 Určuje ID skupiny.  
  
 `nObjectID`  
 Určuje ID objektu.  
  
 `dwUserData`  
 Určuje uživatelská data.  
  
 `pt`  
 Souřadnice levého horního rohu.  
  
 `sz`  
 Velikost rámečku.  
  
 `nLeft`  
 Určuje souřadnice levého hranice.  
  
 `nTop`  
 Určuje souřadnici horní vázána.  
  
 `nRight`  
 Určuje souřadnici správné hranice.  
  
 `nBottom`  
 Určuje souřadnici dolní vázána.  
  
### <a name="remarks"></a>Poznámky  
 Objekt je vytvořený pomocí výchozí hodnoty pro vlevo, horní, pravé a dolní, ID objektu a ID skupiny, které bude nastavena na hodnotu 0. Může se změnit později v době běhu pomocí SetDefaultValue a ID sady.  
  
##  <a name="getanimationvariablelist"></a>CAnimationRect::GetAnimationVariableList  
 Zařadí do seznamu proměnných zapouzdřené animace.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parametry  
 `lst`  
 Když funkce vrátí hodnotu, obsahuje odkazy na čtyři CAnimationVariable objekty, které představují souřadnice obdélník.  
  
##  <a name="getbottom"></a>CAnimationRect::GetBottom  
 Poskytuje přístup k CAnimationVariable představující souřadnice dolního.  
  
```  
CAnimationVariable& GetBottom();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na obsah zapouzdřeného CAnimationVariable představující souřadnice dolního.  
  
### <a name="remarks"></a>Poznámky  
 Můžete volat tuto metodu za účelem získání přímý přístup k podkladové CAnimationVariable představující souřadnice dolního.  
  
##  <a name="getdefaultvalue"></a>CAnimationRect::GetDefaultValue  
 Vrátí výchozí hodnoty pro obdélníku hranice.  
  
```  
CRect GetDefaultValue();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu CRect obsahující výchozí hodnoty pro levé, pravé, horní a dolní.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se načíst výchozí hodnotu, která byla dříve nastavena pomocí konstruktoru nebo SetDefaultValue.  
  
##  <a name="getleft"></a>CAnimationRect::GetLeft  
 Poskytuje přístup k CAnimationVariable představující levou souřadnici.  
  
```  
CAnimationVariable& GetLeft();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na obsah zapouzdřeného CAnimationVariable představující levou souřadnici.  
  
### <a name="remarks"></a>Poznámky  
 Můžete volat tuto metodu za účelem získání přímý přístup k podkladové CAnimationVariable představující levou souřadnici.  
  
##  <a name="getright"></a>CAnimationRect::GetRight  
 Poskytuje přístup k CAnimationVariable představující správné souřadnice.  
  
```  
CAnimationVariable& GetRight();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na obsah zapouzdřeného CAnimationVariable představující správné souřadnice.  
  
### <a name="remarks"></a>Poznámky  
 Můžete volat tuto metodu za účelem získání přímý přístup k podkladové CAnimationVariable představující souřadnici správné.  
  
##  <a name="gettop"></a>CAnimationRect::GetTop  
 Poskytuje přístup k CAnimationVariable představující horní souřadnici.  
  
```  
CAnimationVariable& GetTop();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na obsah zapouzdřeného CAnimationVariable představující horní souřadnici.  
  
### <a name="remarks"></a>Poznámky  
 Můžete volat tuto metodu za účelem získání přímý přístup k podkladové CAnimationVariable představující horní souřadnici.  
  
##  <a name="getvalue"></a>CAnimationRect::GetValue  
 Vrací aktuální hodnotu.  
  
```  
BOOL GetValue(CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Výstup. Po návratu tato metoda obsahuje aktuální hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud aktuální hodnota byla úspěšně načtena; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce načíst aktuální hodnota obdélníku animace. Pokud tato metoda selže nebo základní COM objekty pro vlevo nahoře, vpravo a dole nebyly inicializovány, Rect – obsahuje výchozí hodnotu, která byla dříve nastavena v konstruktoru nebo SetDefaultValue.  
  
##  <a name="m_bfixedsize"></a>CAnimationRect::m_bFixedSize  
 Určuje, zda rámeček má pevnou velikost.  
  
```  
BOOL m_bFixedSize;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je tento člen pravdivá, velikost obdélníku je pevné a vpravo a dolní hodnoty jsou přepočítána pokaždé, když je přesunut levého horního rohu podle pevné velikosti. Tuto hodnotu nastavte na hodnotu TRUE snadno přesunout rámeček po obrazovce. V takovém případě přechody u souřadnice vpravo a dole se ignorují. Velikost je uložen interně při sestavení objektu nebo volání SetDefaultValue. Ve výchozím nastavení je tento člen nastavena na hodnotu FALSE.  
  
##  <a name="m_bottomvalue"></a>CAnimationRect::m_bottomValue  
 Obsah zapouzdřeného animace proměnné, která představuje dolní hranice elementu obdélníku animace.  
  
```  
CAnimationVariable m_bottomValue;  
```  
  
##  <a name="m_leftvalue"></a>CAnimationRect::m_leftValue  
 Obsah zapouzdřeného animace proměnné, která představuje vlevo hranice elementu obdélníku animace.  
  
```  
CAnimationVariable m_leftValue;  
```  
  
##  <a name="m_rightvalue"></a>CAnimationRect::m_rightValue  
 Obsah zapouzdřeného animace proměnné, která představuje vpravo hranice elementu obdélníku animace.  
  
```  
CAnimationVariable m_rightValue;  
```  
  
##  <a name="m_szinitial"></a>CAnimationRect::m_szInitial  
 Určuje počáteční velikost obdélníku animace.  
  
```  
CSize m_szInitial;  
```  
  
##  <a name="m_topvalue"></a>CAnimationRect::m_topValue  
 Obsah zapouzdřeného animace proměnné, která představuje horní hranice elementu obdélníku animace.  
  
```  
CAnimationVariable m_topValue;  
```  
  
##  <a name="operator_rect"></a>Rect – CAnimationRect::operator  
 Převede CAnimationRect obdélníkový  
  
```  
operator RECT();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota obdélníku animace jako obdélníkový  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce interně volá GetValue. Pokud GetValue z nějakého důvodu selže, bude obsahovat vrácený Rect – výchozí hodnoty pro všechny obdélníku souřadnice.  
  
##  <a name="operator_eq"></a>CAnimationRect::operator =  
 Rect – přiřadí CAnimationRect.  
  
```  
void operator=(const RECT& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Nová hodnota obdélníku animace.  
  
### <a name="remarks"></a>Poznámky  
 Se doporučuje udělat před animace spustit, protože tento operátor volání SetDefaultValue, který vytvoří základní objekty modelu COM pro barvu součásti, pokud byly vytvořeny. Pokud odebíráte tento objekt animace události (ValueChanged nebo IntegerValueChanged), budete muset znovu povolit tyto události.  
  
##  <a name="setdefaultvalue"></a>CAnimationRect::SetDefaultValue  
 Nastaví výchozí hodnotu.  
  
```  
void SetDefaultValue(const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Určuje nové výchozí hodnoty pro vlevo, horní, pravé a dolní.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete nastavit výchozí hodnotu do objektu animace. Tyto metody přiřadí obdélníku hranice výchozí hodnoty. Také vytvoří základní objekty modelu COM, pokud byly vytvořeny. Pokud odebíráte tento objekt animace události (ValueChanged nebo IntegerValueChanged), budete muset znovu povolit tyto události.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
