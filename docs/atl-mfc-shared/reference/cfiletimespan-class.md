---
title: Třída CFileTimeSpan | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: facf4abc01ed55ec7c6d84755530a776c68e166d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan – třída
Tato třída poskytuje metody pro správu relativní datum a čas hodnoty přidružené k souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CFileTimeSpan
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Volat tuto metodu za účelem načtení časové rozpětí z `CFileTimeSpan` objektu.|  
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Volat tuto metodu a nastavit časový rozsah `CFileTimeSpan` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileTimeSpan::operator-](#operator_-)|Provádí odčítání `CFileTimeSpan` objektu.|  
|[CFileTimeSpan::operator! =](#operator_neq)|Porovná dva `CFileTimeSpan` objekty nerovnost.|  
|[CFileTimeSpan::operator +](#operator_add)|Provede přidání `CFileTimeSpan` objektu.|  
|[CFileTimeSpan::operator +=](#operator_add_eq)|Provede přidání `CFileTimeSpan` objektu a výsledek přiřadit aktuální objekt.|  
|[CFileTimeSpan::operator &lt;](#operator_lt)|Porovná dva `CFileTimeSpan` objekty, které chcete určit menší.|  
|[CFileTimeSpan::operator &lt;=](#operator_lt_eq)|Porovná dva `CFileTimeSpan` objekty k určení rovnosti nebo menší.|  
|[CFileTimeSpan::operator =](#operator_eq)|Operátor přiřazení.|  
|[CFileTimeSpan::operator-=](#operator_-_eq)|Provádí odčítání `CFileTimeSpan` objektu a výsledek přiřadit aktuální objekt.|  
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Porovná dva `CFileTimeSpan` objekty rovnosti.|  
|[CFileTimeSpan::operator &gt;](#operator_gt)|Porovná dva `CFileTimeSpan` objekty, které chcete určit delší.|  
|[CFileTimeSpan::operator &gt;=](#operator_gt_eq)|Porovná dva `CFileTimeSpan` objekty k určení rovnosti nebo delší.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje metody pro správu relativní období času často došlo při provádění operací týkajících se při se vytvoření, posledního přístupu nebo poslední změny souboru. Metody této třídy se často používají ve spojení s [CFileTime třída](../../atl-mfc-shared/reference/cfiletime-class.md) objekty.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atltime.h  
  
##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan  
 Konstruktor  
  
```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 Existující objekt `CFileTimeSpan`.  
  
 `nSpan`  
 Období čas v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 `CFileTimeSpan` Objekt lze vytvořit pomocí existující `CFileTimeSpan` objektu nebo vyjádřený jako hodnotu 64-bit. Výchozí konstruktor nastaví časové rozpětí na hodnotu 0.  
  
##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan  
 Volat tuto metodu za účelem načtení časové rozpětí z `CFileTimeSpan` objektu.  
  
```
LONGLONG GetTimeSpan() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí časový interval v milisekundách.  
  
##  <a name="operator_-"></a>  CFileTimeSpan::operator-  
 Provádí odčítání **CFileTimeSpan** objektu.  
  
```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CFileTimeSpan` objekt reprezentující výsledek rozdíl mezi dvěma časové úseky.  
  
##  <a name="operator_neq"></a>  CFileTimeSpan::operator! =  
 Porovná dva `CFileTimeSpan` objekty nerovnost.  
  
```
bool operator!=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud položka porovnávané není rovno `CFileTimeSpan` objektu; v opačném případě **false**.  
  
##  <a name="operator_add"></a>  CFileTimeSpan::operator +  
 Provede přidání `CFileTimeSpan` objektu.  
  
```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CFileTimeSpan` objektu, který obsahuje součet dvou čas zahrnuje.  
  
##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=  
 Provede přidání `CFileTimeSpan` objektu a přiřadí výsledek jako aktuální objekt.  
  
```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CFileTimeSpan` objektu, který obsahuje součet dvou čas zahrnuje.  
  
##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;  
 Porovná dva `CFileTimeSpan` objekty, které chcete určit menší.  
  
```
bool operator<(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je první objekt menší (představuje za kratší časové období) než druhý, jinak **false**.  
  
##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=  
 Porovná dva `CFileTimeSpan` objekty k určení rovnosti nebo menší.  
  
```
bool operator<=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je první objekt menší než (představuje za kratší časové období) nebo roven hodnotě druhou, jinak **false**.  
  
##  <a name="operator_eq"></a>  CFileTimeSpan::operator =  
 Operátor přiřazení.  
  
```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CFileTimeSpan` objektu.  
  
##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator-=  
 Provádí odčítání `CFileTimeSpan` objektu a přiřadí výsledek jako aktuální objekt.  
  
```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CFileTimeSpan` objektu.  
  
##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==  
 Porovná dva `CFileTimeSpan` objekty rovnosti.  
  
```
bool operator==(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud objekty jsou stejné, jinak **false**.  
  
##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;  
 Porovná dva `CFileTimeSpan` objekty, které chcete určit delší.  
  
```
bool operator>(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je první objekt větší než (představuje delší časové období) než druhý, jinak **false**.  
  
##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=  
 Porovná dva `CFileTimeSpan` objekty k určení rovnosti nebo delší.  
  
```
bool operator>=(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CFileTimeSpan` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je první objekt větší než (představuje delší časové období) nebo roven hodnotě druhou, jinak **false**.  
  
##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan  
 Volat tuto metodu a nastavit časový rozsah `CFileTimeSpan` objektu.  
  
```
void SetTimeSpan(LONGLONG nSpan) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nSpan`  
 Nová hodnota pro časový interval v milisekundách.  
  
## <a name="see-also"></a>Viz také  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [CFileTime – třída](../../atl-mfc-shared/reference/cfiletime-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)


