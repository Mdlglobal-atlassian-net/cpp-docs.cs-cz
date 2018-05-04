---
title: Třída COleDateTimeSpan | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
dev_langs:
- C++
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1941984093879ba22921d19580618ce8caa04b38
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan – třída
Představuje relativní čas, časové období.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class COleDateTimeSpan
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|Vytvoří `COleDateTimeSpan` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDateTimeSpan::Format](#format)|Generuje formátovaný řetězcovou reprezentaci `COleDateTimeSpan` objektu.|  
|[COleDateTimeSpan::GetDays](#getdays)|Vrátí den část rozpětí to `COleDateTimeSpan` objekt představuje.|  
|[COleDateTimeSpan::GetHours](#gethours)|Vrátí hodinu část rozpětí to `COleDateTimeSpan` objekt představuje.|  
|[COleDateTimeSpan::GetMinutes](#getminutes)|Vrátí minutu část rozpětí to `COleDateTimeSpan` objekt představuje.|  
|[COleDateTimeSpan::GetSeconds](#getseconds)|Vrátí druhou část rozpětí to `COleDateTimeSpan` objekt představuje.|  
|[COleDateTimeSpan::GetStatus](#getstatus)|Získá stav (platnosti) to `COleDateTimeSpan` objektu.|  
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Vrátí počet dní, to `COleDateTimeSpan` objekt představuje.|  
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Vrátí počet hodin, to `COleDateTimeSpan` objekt představuje.|  
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Vrátí počet minut, to `COleDateTimeSpan` objekt představuje.|  
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Vrátí počet sekund, to `COleDateTimeSpan` objekt představuje.|  
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Nastaví hodnotu této `COleDateTimeSpan` objektu.|  
|[COleDateTimeSpan::SetStatus](#setstatus)|Nastaví stav (platnosti) tohoto `COleDateTimeSpan` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|||  
|-|-|  
|[operátor +, -](#operator_add_-)|Přidat, odečíst a změňte přihlášení pro `COleDateTimeSpan` hodnoty.|  
|[Operator +=-=](#operator_add_eq_-_eq)|Sčítání a odečítání `COleDateTimeSpan` hodnotu z tohoto `COleDateTimeSpan` hodnotu.|  
|[operátor =](#operator_eq)|Kopie `COleDateTimeSpan` hodnotu.|  
|[Operator ==, <, < =](#coledatetimespan_relational_operators)|Porovnat `COleDateTimeSpan` hodnoty.|  
|[operátor double](#operator_double)|Převede tento `COleDateTimeSpan` hodnotu **dvojité**.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDateTimeSpan::m_span](#m_span)|Obsahuje základní **dvojité** pro tento `COleDateTimeSpan` objektu.|  
|[COleDateTimeSpan::m_status](#m_status)|Obsahuje stav tohoto `COleDateTimeSpan` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `COleDateTimeSpan` nemá základní třídu.  
  
 A `COleDateTimeSpan` udržuje času ve dnech.  
  
 `COleDateTimeSpan` se používá s její doprovodné třída [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime` zapouzdří **datum** datový typ automatizace OLE. `COleDateTime` reprezentuje absolutním čase hodnoty. Všechny `COleDateTime` zahrnují výpočty `COleDateTimeSpan` hodnoty. Vztah mezi tyto třídy je podobná jeden mezi [CTime](../../atl-mfc-shared/reference/ctime-class.md) a [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).  
  
 Další informace o `COleDateTime` a `COleDateTimeSpan` třídy, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ATLComTime.h  
  
##  <a name="coledatetimespan_relational_operators"></a>  Relační operátory COleDateTimeSpan  
 Operátory porovnání.  
  
```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *dateSpan*  
 `COleDateTimeSpan` k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tyto operátory porovnání dvou hodnot datum nebo období a vrátí **true** Pokud je podmínka vyhodnocena jako true; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  ATLASSERT dojde, pokud buď operand je neplatný.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]  
  
##  <a name="coledatetimespan"></a>  COleDateTimeSpan::COleDateTimeSpan  
 Vytvoří `COleDateTimeSpan` objektu.  
  
```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dblSpanSrc`  
 Počet dní, které se mají zkopírovat do nové `COleDateTimeSpan` objektu.  
  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 Určení hodnoty den a čas, který se má zkopírovat do nové `COleDateTimeSpan` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Všechny tyto konstruktory vytvořit nový `COleDateTimeSpan` objekty inicializovat se zadanou hodnotou. Následuje stručný popis každého z těchto konstruktorů:  
  
- **(COleDateTimeSpan)** vytvoří `COleDateTimeSpan` objekt hodnotu 0.  
  
- **COleDateTimeSpan (** `dblSpanSrc` **)** vytvoří `COleDateTimeSpan` objekt z hodnoty s plovoucí desetinnou čárkou.  
  
- **COleDateTimeSpan (** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)**  Vytvoří `COleDateTimeSpan` objekt inicializována tak, aby zadaný číselné hodnoty.  
  
 Stav nové `COleDateTimeSpan` nastavena na platný objekt.  
  
 Další informace o hranice pro `COleDateTimeSpan` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]  
  
##  <a name="format"></a>  COleDateTimeSpan::Format  
 Generuje formátovaný řetězcovou reprezentaci `COleDateTimeSpan` objektu.  
  
```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pFormat`  
 Formátování řetězce podobně jako `printf` formátování řetězce. Formátování kódy, před sebou procento ( `%`) přihlásit, se nahrazují odpovídající `COleDateTimeSpan` součásti. Dalšími znaky v řetězci formátování se zkopírují na vrácený řetězec beze změny. Hodnota a význam formátování kódy pro **formát** jsou uvedeny níže:  
  
- **%H** čas do aktuálního dne  
  
- **%M** minut do aktuální hodiny  
  
- **%S** sekund do aktuální minuty  
  
- **%%** Znak procenta  
  
 Čtyři formátu kódy uvedené výše jsou pouze kód, který bude přijímat formátu.  
  
-  
  
 `nID`  
 ID prostředku pro řetězec formát ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` obsahující formátovanou hodnotu datum nebo období.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tyto funkce vytvořit formátovaný reprezentaci hodnoty časové rozpětí. Pokud se stav tohoto `COleDateTimeSpan` objekt má hodnotu null, vrácená hodnota je prázdný řetězec. Pokud je neplatný stav, vrácený řetězec určeného řetězce prostředků **IDS_INVALID_DATETIMESPAN**.  
  
 Následuje stručný popis formuláře pro tuto funkci:  
  
 **Formát (** `pFormat` **)**  
 Tento formulář naformátuje hodnotu pomocí řetězec formátu, který obsahuje speciální formátování kódy, které jsou uvozená znakem procent (%), jako v `printf`. Formátovací řetězec je jako parametr předaný funkci.  
  
 **Formát (** `nID` **)**  
 Tento formulář naformátuje hodnotu pomocí řetězec formátu, který obsahuje speciální formátování kódy, které jsou uvozená znakem procent (%), jako v `printf`. Formátovací řetězec je prostředek. ID prostředku tento řetězec je předán jako parametr.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]  
  
##  <a name="getdays"></a>  COleDateTimeSpan::GetDays  
 Načte část den tato hodnota datum/čas rozpětí.  
  
```
LONG GetDays() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Část den tato hodnota datum/čas rozpětí.  
  
### <a name="remarks"></a>Poznámky  
 Vrácení hodnoty z této funkce rozsahu přibližně - 3,615,000 a 3,615,000.  
  
 Pro další funkce, které dotaz na hodnotu `COleDateTimeSpan` objektu, viz následující členské funkce:  
  
- [Gethours –](#gethours)  
  
- [Getminutes –](#getminutes)  
  
- [Getseconds –](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]  
  
##  <a name="gethours"></a>  COleDateTimeSpan::GetHours  
 Načte část hodinu tato hodnota datum/čas rozpětí.  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Část hodin tato hodnota datum/čas rozpětí.  
  
### <a name="remarks"></a>Poznámky  
 Návratové hodnoty z této funkce rozsahu – 23 až 23.  
  
 Pro další funkce, které dotaz na hodnotu `COleDateTimeSpan` objektu, viz následující členské funkce:  
  
- [GetDays](#getdays)  
  
- [Getminutes –](#getminutes)  
  
- [Getseconds –](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]  
  
##  <a name="getminutes"></a>  COleDateTimeSpan::GetMinutes  
 Načte minutu část tato hodnota datum/čas rozpětí.  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Část minut tato hodnota datum/čas rozpětí.  
  
### <a name="remarks"></a>Poznámky  
 Návratové hodnoty z této funkce rozsahu - 59 až 59.  
  
 Pro další funkce, které dotaz na hodnotu `COleDateTimeSpan` objektu, viz následující členské funkce:  
  
- [GetDays](#getdays)  
  
- [Gethours –](#gethours)  
  
- [Getseconds –](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]  
  
##  <a name="getseconds"></a>  COleDateTimeSpan::GetSeconds  
 Načte druhou část tato hodnota datum/čas rozpětí.  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Část sekundy tato hodnota datum/čas rozpětí.  
  
### <a name="remarks"></a>Poznámky  
 Návratové hodnoty z této funkce rozsahu - 59 až 59.  
  
 Pro další funkce, které dotaz na hodnotu `COleDateTimeSpan` objektu, viz následující členské funkce:  
  
- [GetDays](#getdays)  
  
- [Gethours –](#gethours)  
  
- [Getminutes –](#getminutes)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]  
  
##  <a name="getstatus"></a>  COleDateTimeSpan::GetStatus  
 Získá stav (platnosti) to `COleDateTimeSpan` objektu.  
  
```
DateTimeSpanStatus GetStatus() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav tohoto `COleDateTimeSpan` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Návratová hodnota je definované **DateTimeSpanStatus** výčtového typu, která je definována v rámci `COleDateTimeSpan` třídy.  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
};  
```  
  
 Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:  
  
- **COleDateTimeSpan::valid** -označuje, že tato `COleDateTimeSpan` je objekt platný.  
  
- **COleDateTimeSpan::invalid** -označuje, že tato `COleDateTimeSpan` objektu je neplatné, který je jeho hodnota může být nesprávný.  
  
- **COleDateTimeSpan::null** -označuje, že tato `COleDateTimeSpan` objekt má hodnotu null, to znamená, že má žádná hodnota zadaná pro tento objekt. (Toto je "null" v tom smyslu, databáze "použití žádná hodnota" a C++ **NULL**.)  
  
 Stav `COleDateTimeSpan` objekt je neplatný v následujících případech:  
  
-   Pokud tento objekt došlo přetečení nebo podtečení během operace aritmetické přiřazení, konkrétně, `+=` nebo `-=`.  
  
-   Pokud je neplatná hodnota byl přiřazen k tomuto objektu.  
  
-   Pokud se stav tohoto objektu se explicitně nastavit na neplatné použití `SetStatus`.  
  
 Další informace o operacích, které může nastavit stav na neplatný najdete v tématu [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) a [COleDateTimeSpan::operator +=,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).  
  
 Další informace o hranice pro `COleDateTimeSpan` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="gettotaldays"></a>  COleDateTimeSpan::GetTotalDays  
 Načte tuto hodnotu datum nebo období, vyjádřené v dnech.  
  
```
double GetTotalDays() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato hodnota datum nebo období, vyjádřené v dnech. I když tato funkce je deklaraci vrátit datový typ double, vždy vrátí celočíselnou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Návratové hodnoty z tohoto rozsahu funkce přibližně - 3.65e6 a 3.65e6.  
  
 Pro další funkce, které dotaz na hodnotu `COleDateTimeSpan` objektu, viz následující členské funkce:  
  
- [GetDays](#getdays)  
  
- [Gethours –](#gethours)  
  
- [Getminutes –](#getminutes)  
  
- [Getseconds –](#getseconds)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]  
  
##  <a name="gettotalhours"></a>  COleDateTimeSpan::GetTotalHours  
 Načte tato hodnota datum/čas rozpětí vyjádřena v hodinách.  
  
```
double GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato hodnota datum/čas rozpětí, vyjádřené v hodinách. I když tato funkce je deklaraci vrátit datový typ double, vždy vrátí celočíselnou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Návratové hodnoty z tohoto rozsahu funkce přibližně - 8.77e7 a 8.77e7.  
  
 Pro další funkce, které dotaz na hodnotu `COleDateTimeSpan` objektu, viz následující členské funkce:  
  
- [GetDays](#getdays)  
  
- [Gethours –](#gethours)  
  
- [Getminutes –](#getminutes)  
  
- [Getseconds –](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetTotalDays](#gettotaldays).  
  
##  <a name="gettotalminutes"></a>  COleDateTimeSpan::GetTotalMinutes  
 Načte tuto hodnotu datum nebo období, vyjádřené v minutách.  
  
```
double GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato hodnota datum/čas rozpětí, vyjádřené v minutách. I když tato funkce je deklaraci vrátit datový typ double, vždy vrátí celočíselnou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Návratové hodnoty z tohoto rozsahu funkce přibližně - 5.26e9 a 5.26e9.  
  
 Pro další funkce, které dotaz na hodnotu `COleDateTimeSpan` objektu, viz následující členské funkce:  
  
- [GetDays](#getdays)  
  
- [Gethours –](#gethours)  
  
- [Getminutes –](#getminutes)  
  
- [Getseconds –](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetTotalDays](#gettotaldays).  
  
##  <a name="gettotalseconds"></a>  COleDateTimeSpan::GetTotalSeconds  
 Načte tuto hodnotu datum nebo období, v sekundách.  
  
```
double GetTotalSeconds() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato hodnota datum nebo období, v sekundách. I když tato funkce je deklaraci vrátit datový typ double, vždy vrátí celočíselnou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Návratové hodnoty z této funkce v rozsahu mezi přibližně – 3.16e11 k 3.16e11.  
  
 Pro další funkce, které dotaz na hodnotu `COleDateTimeSpan` objektu, viz následující členské funkce:  
  
- [GetDays](#getdays)  
  
- [Gethours –](#gethours)  
  
- [Getminutes –](#getminutes)  
  
- [Getseconds –](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetTotalDays](#gettotaldays).  
  
##  <a name="m_span"></a>  COleDateTimeSpan::m_span  
 Základní **dvojité** hodnotu pro tento `COleDateTime` objektu.  
  
```
double m_span;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota vyjadřuje datum nebo období ve dnech.  
  
> [!CAUTION]
>  Změna hodnoty v **dvojité** – datový člen změní hodnotu této `COleDateTimeSpan` objektu. Nezmění stav tohoto `COleDateTimeSpan` objektu.  
  
##  <a name="m_status"></a>  COleDateTimeSpan::m_status  
 Typ pro tento člen dat je Výčtový typ **DateTimeSpanStatus**, která je definována v rámci `COleDateTimeSpan` třídy.  
  
```
DateTimeSpanStatus m_status;
```  
  
### <a name="remarks"></a>Poznámky  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```  
  
 Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:  
  
- **COleDateTimeSpan::valid** -označuje, že tato `COleDateTimeSpan` je objekt platný.  
  
- **COleDateTimeSpan::invalid** -označuje, že tato `COleDateTimeSpan` objektu je neplatné, který je jeho hodnota může být nesprávný.  
  
- **COleDateTimeSpan::null** -označuje, že tato `COleDateTimeSpan` objekt má hodnotu null, to znamená, že má žádná hodnota zadaná pro tento objekt. (Toto je "null" v tom smyslu, databáze "použití žádná hodnota" a C++ **NULL**.)  
  
 Stav `COleDateTimeSpan` objekt je neplatný v následujících případech:  
  
-   Pokud tento objekt došlo přetečení nebo podtečení během operace aritmetické přiřazení, konkrétně, `+=` nebo `-=`.  
  
-   Pokud je neplatná hodnota byl přiřazen k tomuto objektu.  
  
-   Pokud se stav tohoto objektu se explicitně nastavit na neplatné použití [SetStatus](#setstatus).  
  
 Další informace o operacích, které může nastavit stav na neplatný najdete v tématu [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) a [COleDateTimeSpan::operator +=,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).  
  
> [!CAUTION]
>  Tento člen dat je pro pokročilé programovací situace. Měli byste použít vložené funkce člen [GetStatus](#getstatus) a [SetStatus](#setstatus). V tématu `SetStatus` pro další upozornění týkající se explicitně nastavení tohoto člena data.  
  
 Další informace o hranice pro `COleDateTimeSpan` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="operator_eq"></a>  COleDateTimeSpan::operator =  
 Kopie `COleDateTimeSpan` hodnotu.  
  
```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor přetížené přiřazení zkopíruje zdrojové datum nebo období hodnoty do této `COleDateTimeSpan` objektu.  
  
##  <a name="operator_add_-"></a>  COleDateTimeSpan::operator +, -  
 Přidat, odečíst a změňte přihlášení pro `COleDateTimeSpan` hodnoty.  
  
```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 První dva operátory umožňují sčítání a odečítání hodnoty datum nebo období. Třetí umožňuje změnit přihlašovací hodnotu datum nebo období.  
  
 Pokud některá z operandy null, stav výsledná `COleDateTimeSpan` hodnota je null.  
  
 Pokud některý z operandy je neplatný a dalších nemá hodnotu null, stav výsledná `COleDateTimeSpan` hodnota je neplatná.  
  
 Další informace o stavu platná, neplatný a hodnotu null. hodnoty, najdete v článku [m_status](#m_status) členské proměnné.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>  COleDateTimeSpan::operator +=-=  
 Sčítání a odečítání `COleDateTimeSpan` hodnotu z tohoto `COleDateTimeSpan` hodnotu.  
  
```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tyto operátory umožňují sčítání a odečítání datum nebo období hodnoty z tohoto `COleDateTimeSpan` objektu. Pokud některá z operandy null, stav výsledná `COleDateTimeSpan` hodnota je null.  
  
 Pokud některý z operandy je neplatný a dalších nemá hodnotu null, stav výsledná `COleDateTimeSpan` hodnota je neplatná.  
  
 Další informace o stavu platná, neplatný a hodnotu null. hodnoty, najdete v článku [m_status](#m_status) členské proměnné.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]  
  
##  <a name="operator_double"></a>  COleDateTimeSpan::operator double  
 Převede tento `COleDateTimeSpan` hodnotu **dvojité**.  
  
```
operator double() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor vrací hodnotu této `COleDateTimeSpan` hodnotu jako s plovoucí desetinnou čárkou počet dnů.  
  
##  <a name="setdatetimespan"></a>  COleDateTimeSpan::SetDateTimeSpan  
 Nastaví hodnotu této hodnoty datum nebo období.  
  
```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 Určení hodnoty rozsahu data a období, které se mají zkopírovat do této `COleDateTimeSpan` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pro funkce, které dotaz na hodnotu `COleDateTimeSpan` objektu, viz následující členské funkce:  
  
- [GetDays](#getdays)  
  
- [Gethours –](#gethours)  
  
- [Getminutes –](#getminutes)  
  
- [Getseconds –](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]  
  
##  <a name="setstatus"></a>  COleDateTimeSpan::SetStatus  
 Nastaví stav (platnosti) tohoto `COleDateTimeSpan` objektu.  
  
```
void SetStatus(DateTimeSpanStatus status) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *Stav*  
 Nová hodnota stav pro tento `COleDateTimeSpan` objektu.  
  
### <a name="remarks"></a>Poznámky  
 *Stav* hodnota parametru je definováno **DateTimeSpanStatus** výčtového typu, která je definována v rámci `COleDateTimeSpan` třídy.  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```  
  
 Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:  
  
- **COleDateTimeSpan::valid** -označuje, že tato `COleDateTimeSpan` je objekt platný.  
  
- **COleDateTimeSpan::invalid** -označuje, že tato `COleDateTimeSpan` objektu je neplatné, který je jeho hodnota může být nesprávný.  
  
- **COleDateTimeSpan::null** -označuje, že tato `COleDateTimeSpan` objekt má hodnotu null, to znamená, že má žádná hodnota zadaná pro tento objekt. (Toto je "null" v tom smyslu, databáze "použití žádná hodnota" a C++ **NULL**.)  
  
    > [!CAUTION]
    >  Tato funkce je pro pokročilé programovací situace. Tato funkce nezmění data v tomto objektu. Použije nejčastěji nastavit stav na `null` nebo **neplatný**. Všimněte si, že operátor přiřazení ( [operátor =](#eq)) a [SetDateTimeSpan](#setdatetimespan) nastavit stav objektu podle hodnoty zdroje.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [COleDateTime – třída](../../atl-mfc-shared/reference/coledatetime-class.md)   
 [CTime – třída](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan – třída](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)


