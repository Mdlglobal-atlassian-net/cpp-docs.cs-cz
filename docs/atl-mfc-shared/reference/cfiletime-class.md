---
title: "Třída CFileTime | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileTime
- ATLTIME/ATL::CFileTime
- ATLTIME/ATL::CFileTime::CFileTime
- ATLTIME/ATL::CFileTime::GetCurrentTime
- ATLTIME/ATL::CFileTime::GetTime
- ATLTIME/ATL::CFileTime::LocalToUTC
- ATLTIME/ATL::CFileTime::SetTime
- ATLTIME/ATL::CFileTime::UTCToLocal
- ATLTIME/ATL::CFileTime::Day
- ATLTIME/ATL::CFileTime::Hour
- ATLTIME/ATL::CFileTime::Millisecond
- ATLTIME/ATL::CFileTime::Minute
- ATLTIME/ATL::CFileTime::Second
- ATLTIME/ATL::CFileTime::Week
dev_langs:
- C++
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d48e899bb058ed27559a4ef699a3a53267064f98
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cfiletime-class"></a>CFileTime – třída
Tato třída poskytuje metody pro správu hodnoty data a času, které jsou přidružené k souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CFileTime :  public FILETIME
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileTime::CFileTime](#cfiletime)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileTime::GetCurrentTime](#getcurrenttime)|Volání této funkce statický načíst `CFileTime` objekt, který představuje aktuální systémový datum a čas.|  
|[CFileTime::GetTime](#gettime)|Volat tuto metodu za účelem načtení času z `CFileTime` objektu.|  
|[CFileTime::LocalToUTC](#localtoutc)|Voláním této metody lze převést místního času na čas souboru na základě na koordinovaný světový čas (UTC).|  
|[CFileTime::SetTime](#settime)|Volat tuto metodu a nastavit datum a čas, které jsou uložené `CFileTime` objektu.|  
|[CFileTime::UTCToLocal](#utctolocal)|Voláním této metody lze převádět na základě na na koordinovaný světový čas (UTC) na místní čas a čas.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileTime::operator-](#operator_-)|Tento operátor slouží k provádění odčítání na `CFileTime` nebo `CFileTimeSpan` objektu.|  
|[CFileTime::operator! =](#operator_neq)|Tento operátor porovná dvě `CFileTime` objekty nerovnost.|  
|[CFileTime::operator +](#operator_add)|Tento operátor slouží k přidání plnění `CFileTimeSpan` objektu.|  
|[CFileTime::operator +=](#operator_add_eq)|Tento operátor slouží k přidání plnění `CFileTimeSpan` objektu a výsledek přiřadit aktuální objekt.|  
|[CFileTime::operator&lt;](#operator_lt)|Tento operátor porovná dvě `CFileTime` objekty, které chcete určit menší.|  
|[CFileTime::operator&lt;=](#operator_lt_eq)|Tento operátor porovná dvě `CFileTime` objekty k určení rovnosti nebo menší.|  
|[CFileTime::operator =](#operator_eq)|Operátor přiřazení.|  
|[CFileTime::operator-=](#operator_-_eq)|Tento operátor slouží k provádění odčítání na `CFileTimeSpan` objektu a výsledek přiřadit aktuální objekt.|  
|[CFileTime::operator ==](#operator_eq_eq)|Tento operátor porovná dvě `CFileTime` objekty rovnosti.|  
|[CFileTime::operator&gt;](#operator_gt)|Tento operátor porovná dvě `CFileTime` objekty, které chcete určit delší.|  
|[CFileTime::operator&gt;=](#operator_gt_eq)|Tento operátor porovná dvě `CFileTime` objekty k určení rovnosti nebo delší.|  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[CFileTime::Day](#day)|Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jeden den.|  
|[CFileTime::Hour](#hour)|Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jednu hodinu.|  
|[CFileTime::Millisecond](#millisecond)|Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jeden milisekundu.|  
|[CFileTime::Minute](#minute)|Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jednu minutu.|  
|[CFileTime::Second](#second)|Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jedna sekunda.|  
|[CFileTime::Week](#week)|Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jeden týden.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje metody pro správu hodnoty data a času, které jsou přidružené k vytváření, přístup a úpravy souborů. Metody a data této třídy se často používají ve spojení s `CFileTimeSpan` objekty, které řeší relativní časové hodnoty.  
  
 Hodnota data a času se ukládají jako 64 bitů hodnotu představující počet 100nanosekundových intervalů od 1. ledna 1601. To je formát koordinovaný světový čas (UTC).  
  
 Následující statické const členské proměnné jsou k dispozici pro zjednodušení výpočty:  
  
|Členské proměnné|Počet 100nanosekundových intervalů|  
|---------------------|-----------------------------------------|  
|Milisekund|10,000|  
|Sekunda|Milisekundu * 1 000|  
|Minuta|Druhý * 60|  
|Hodina|Minutu * 60|  
|Den|Hodina * 24|  
|Týden|Den * 7|  
  
 **Poznámka:** ne všechny systémy souborů můžete záznam vytvoření a čas posledního přístupu a ne všechny systémy souborů je záznam stejným způsobem. Pro příklad, v systému Windows NT FAT systému souborů, vytvoření čas má rozlišení 10 milisekund, doba zápisu má rozlišení 2 sekundy a doba přístupu k má rozlišení 1 den (data access). V systému souborů NTFS čas přístupu má rozlišení 1 hodina. Kromě toho FAT zaznamenává časy na disku v místním čase, ale NTFS zaznamenává časy na disku ve standardu UTC. Další informace najdete v tématu [časy](http://msdn.microsoft.com/library/windows/desktop/ms724290).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `FILETIME`  
  
 `CFileTime`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atltime.h  
  
##  <a name="cfiletime"></a>CFileTime::CFileTime  
 Konstruktor  
  
```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 A [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktury.  
  
 `nTime`  
 Datum a čas vyjádřený jako hodnotu 64-bit.  
  
### <a name="remarks"></a>Poznámky  
 `CFileTime` Můžete vytvořit objekt použití existující datum a čas z `FILETIME` struktury nebo vyjádřený jako hodnotu 64-bit (ve formátu času koordinovaný světový čas (UTC) nebo místní). Výchozí konstruktor nastaví čas na hodnotu 0.  
  
##  <a name="day"></a>CFileTime::Day  
 Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jeden den.  
  
```
static const ULONGLONG Day = Hour* 24;
```  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CFileTime::Millisecond](#millisecond).  
  
##  <a name="getcurrenttime"></a>CFileTime::GetCurrentTime  
 Volání této funkce statický načíst `CFileTime` objekt, který představuje aktuální systémový datum a čas.  
  
```
static CFileTime GetCurrentTime() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktuální systémový datum a čas ve formátu koordinovaný světový čas (UTC).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]  
  
##  <a name="gettime"></a>CFileTime::GetTime  
 Volat tuto metodu za účelem načtení času z `CFileTime` objektu.  
  
```
ULONGLONG GetTime() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí datum a čas jako 64bitové číslo, které mohou být ve formátu koordinovaný světový čas (UTC) nebo místní.  
  
##  <a name="hour"></a>CFileTime::Hour  
 Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jednu hodinu.  
  
```
static const ULONGLONG Hour = Minute* 60;
```  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CFileTime::Millisecond](#millisecond).  
  
##  <a name="localtoutc"></a>CFileTime::LocalToUTC  
 Voláním této metody lze převést místního času na čas souboru na základě na koordinovaný světový čas (UTC).  
  
```
CFileTime LocalToUTC() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CFileTime` objekt obsahující čas ve formátu UTC.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CFileTime::UTCToLocal](#utctolocal).  
  
##  <a name="millisecond"></a>CFileTime::Millisecond  
 Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jeden milisekundu.  
  
```
static const ULONGLONG Millisecond = 10000;
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]  
  
##  <a name="minute"></a>CFileTime::Minute  
 Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jednu minutu.  
  
```
static const ULONGLONG Minute = Second* 60;
```  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CFileTime::Millisecond](#millisecond).  
  
##  <a name="operator_-"></a>CFileTime::operator-  
 Tento operátor slouží k provádění odčítání na `CFileTime` nebo `CFileTimeSpan` objektu.  
  
```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` objektu.  
  
 `ft`  
 A `CFileTime` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CFileTime` objekt nebo `CFileTimeSpan` objekt reprezentující výsledek časový rozdíl mezi dvěma objekty.  
  
##  <a name="operator_neq"></a>CFileTime::operator! =  
 Tento operátor porovná dvě `CFileTime` objekty nerovnost.  
  
```
bool operator!=(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud položka porovnávané není rovno `CFileTime` objektu, jinak hodnota **false**.  
  
##  <a name="operator_add"></a>CFileTime::operator +  
 Tento operátor slouží k přidání plnění `CFileTimeSpan` objektu.  
  
```
CFileTime operator+(CFileTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CFileTime` objekt reprezentující výsledek původní čas a relativní časové.  
  
##  <a name="operator_add_eq"></a>CFileTime::operator +=  
 Tento operátor slouží k přidání plnění `CFileTimeSpan` objektu a výsledek přiřadit aktuální objekt.  
  
```
CFileTime& operator+=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CFileTime` objektu, která reprezentuje výsledek původní čas a relativní časové.  
  
##  <a name="operator_lt"></a>CFileTime::operator&lt;  
 Tento operátor porovná dvě `CFileTime` objekty, které chcete určit menší.  
  
```
bool operator<(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je první objekt menší (dříve v čase) než druhý, **false** jinak.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]  
  
##  <a name="operator_lt_eq"></a>CFileTime::operator&lt;=  
 Tento operátor porovná dvě `CFileTime` objekty k určení rovnosti nebo menší.  
  
```
bool operator<=(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je první objekt menší než (starší v čase) nebo rovna hodnotě druhého, jinak **false**.  
  
##  <a name="operator_eq"></a>CFileTime::operator =  
 Operátor přiřazení.  
  
```
CFileTime& operator=(const FILETIME& ft) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 A `CFileTime` objekt obsahující nové data a času.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CFileTime` objektu.  
  
##  <a name="operator_-_eq"></a>CFileTime::operator-=  
 Tento operátor slouží k provádění odčítání na `CFileTimeSpan` objektu a výsledek přiřadit aktuální objekt.  
  
```
CFileTime& operator-=(CFileTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 A `CFileTimeSpan` objekt obsahující relativní časové má odečíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CFileTime` objektu.  
  
##  <a name="operator_eq_eq"></a>CFileTime::operator ==  
 Tento operátor porovná dvě `CFileTime` objekty rovnosti.  
  
```
bool operator==(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Objekt k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud objekty jsou stejné, jinak **false**.  
  
##  <a name="operator_gt"></a>CFileTime::operator&gt;  
 Tento operátor porovná dvě `CFileTime` objekty, které chcete určit delší.  
  
```
bool operator>(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je první objekt větší než (později v čase) než druhý, jinak **false**.  
  
##  <a name="operator_gt_eq"></a>CFileTime::operator&gt;=  
 Tento operátor porovná dvě `CFileTime` objekty k určení rovnosti nebo delší.  
  
```
bool operator>=(CFileTime ft) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ft`  
 `CFileTime` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud první objekt větší než (později v čase) nebo rovna hodnotě druhého, jinak **false**.  
  
##  <a name="second"></a>CFileTime::Second  
 Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jeden den.  
  
```
static const ULONGLONG Second = Millisecond* 1000;
```  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CFileTime::Millisecond](#millisecond).  
  
##  <a name="settime"></a>CFileTime::SetTime  
 Volat tuto metodu a nastavit datum a čas, které jsou uložené `CFileTime` objektu.  
  
```
void SetTime(ULONGLONG nTime) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nTime`  
 64bitová verze hodnota představující datum a čas ve formátu koordinovaný světový čas (UTC) nebo místní.  
  
##  <a name="utctolocal"></a>CFileTime::UTCToLocal  
 Voláním této metody lze převádět na základě na na koordinovaný světový čas (UTC) na místní čas a čas.  
  
```
CFileTime UTCToLocal() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `CFileTime` objekt obsahující čas ve formátu času místního souboru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]  
  
##  <a name="week"></a>CFileTime::Week  
 Člen statických dat ukládání počtu 100nanosekundových intervalů, které tvoří jeden týden.  
  
```
static const ULONGLONG Week = Day* 7;
```  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CFileTime::Millisecond](#millisecond).  
  
## <a name="see-also"></a>Viz také  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [CFileTimeSpan – třída](../../atl-mfc-shared/reference/cfiletimespan-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)


