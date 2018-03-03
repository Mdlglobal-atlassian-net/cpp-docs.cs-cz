---
title: "Třída CTimeSpan | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
dev_langs:
- C++
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cedf05bd8f5af198569891b4d6d59610d5098eb6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ctimespan-class"></a>CTimeSpan – třída
Určenou dobu, která je uložena interně jako počet sekund v časové rozpětí.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CTimeSpan
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CTimeSpan::CTimeSpan](#ctimespan)|Vytvoří `CTimeSpan` objekty různými způsoby.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTimeSpan::Format](#format)|Převede `CTimeSpan` do formátovaný řetězec.|  
|[CTimeSpan::GetDays](#getdays)|Vrátí hodnotu, která představuje počet dnů dokončení v tomto `CTimeSpan`.|  
|[CTimeSpan::GetHours](#gethours)|Vrátí hodnotu, která představuje počet hodin, do aktuálního dne (až 23 -23).|  
|[CTimeSpan::GetMinutes](#getminutes)|Vrátí hodnotu, která představuje počet minut do aktuální hodiny (-59 do 59).|  
|[CTimeSpan::GetSeconds](#getseconds)|Vrátí hodnotu, která představuje počet sekund do aktuální minuty (-59 do 59).|  
|[CTimeSpan::GetTimeSpan](#gettimespan)|Vrátí hodnotu `CTimeSpan` objektu.|  
|[CTimeSpan::GetTotalHours](#gettotalhours)|Vrátí hodnotu, která představuje celkový počet hodin dokončení v tomto `CTimeSpan`.|  
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|Vrátí hodnotu, která představuje celkový počet minut dokončení v tomto `CTimeSpan`.|  
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|Vrátí hodnotu, která představuje celkový počet sekund dokončení v tomto `CTimeSpan`.|  
|[CTimeSpan::Serialize64](#serialize64)|Serializuje data do nebo z archivu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor + -](#operator_add_-)|Přidá a odečítá `CTimeSpan` objekty.|  
|[+= – operátor-=](#operator_add_eq_-_eq)|Přidá a odečítá `CTimeSpan` objekt do a z tohoto `CTimeSpan`.|  
|[Operator == < atd.](#ctimespan_comparison_operators)|Porovná dvě relativní časové hodnoty.|  
  
## <a name="remarks"></a>Poznámky  
 `CTimeSpan`nemá základní třídu.  
  
 `CTimeSpan`funkce převést sekund různé kombinace dní, hodiny, minuty a sekundy.  
  
 `CTimeSpan` Objekt uložen v **__time64_t –** strukturu, která je 8 bajtů.  
  
 Třídu doprovodné [CTime –](../../atl-mfc-shared/reference/ctime-class.md), představuje absolutní čas.  
  
 `CTime` a `CTimeSpan` třídy nejsou navrženy pro odvození. Protože nejsou k dispozici žádné virtuální funkce velikost obou `CTime` a `CTimeSpan` objekty je přesně 8 bajtů. Většina členské funkce jsou vložené.  
  
 Další informace o používání `CTimeSpan`, najdete v článcích [datum a čas](../../atl-mfc-shared/date-and-time.md), a [Správa času](../../c-runtime-library/time-management.md) v *referenční dokumentace běhové knihovny*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atltime.h  
  
##  <a name="ctimespan_comparison_operators"></a>Operátory porovnání CTimeSpan  
 Operátory porovnání.  
  
```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
  
 Objekt k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tyto operátory porovnání dvě relativní časové hodnoty. Vracejí **true** Pokud je podmínka vyhodnocena jako true; jinak hodnota **false**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]  
  
##  <a name="ctimespan"></a>CTimeSpan::CTimeSpan  
 Vytvoří `CTimeSpan` objekty různými způsoby.  
  
```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(  
 LONG lDays,
 int nHours,
 int nMins,
 int nSecs) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *timeSpanSrc*  
 A `CTimeSpan` objekt, který již existuje.  
  
 `time`  
 A **__time64_t –** čas hodnotu, která je počet sekund v časové rozpětí.  
  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 Dny, hodiny minuty a sekundy, v uvedeném pořadí.  
  
### <a name="remarks"></a>Poznámky  
 Všechny tyto konstruktory vytvořte novou `CTimeSpan` objekt inicializován s relativní okamžik. Každý konstruktor je popsán dále:  
  
- **CTimeSpan ();**  Vytvoří Neinicializovaný `CTimeSpan` objektu.  
  
- **CTimeSpan (const CTimeSpan &);**  Vytvoří `CTimeSpan` objekt z jiné `CTimeSpan` hodnotu.  
  
- **CTimeSpan __time64_t (–);**  Vytvoří `CTimeSpan` objektu z **__time64_t –** typu.  
  
- **CTimeSpan (DLOUHO**, **int, int, int);** Vytvoří `CTimeSpan` objekt z komponenty s jednotlivé komponenty omezené na následující oblasti:  
  
    |Součást|Rozsah|  
    |---------------|-----------|  
    |`lDays`|0-25 000 (přibližně)|  
    |`nHours`|0-23|  
    |`nMins`|0-59|  
    |`nSecs`|0-59|  
  
 Všimněte si, že ladicí verzi knihovny Microsoft Foundation Class vyhodnotí, pokud jeden nebo více součástí času dne je mimo rozsah. Je vaší povinností ověřte argumenty před voláním.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]  
  
##  <a name="format"></a>CTimeSpan::Format  
 Generuje formátovaný řetězec, který odpovídá tomuto `CTimeSpan`.  
  
```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pFormat`, `pszFormat`  
 Formátování řetězce podobně jako `printf` formátování řetězce. Formátování kódy, před sebou procento ( `%`) přihlásit, se nahrazují odpovídající `CTimeSpan` součásti. Dalšími znaky v řetězci formátování se zkopírují na vrácený řetězec beze změny. Hodnota a význam formátování kódy pro **formát** jsou uvedeny níže:  
  
- **%D** celkový počet dní v tomto`CTimeSpan`  
  
- **%H** čas do aktuálního dne  
  
- **%M** minut do aktuální hodiny  
  
- **%S** sekund do aktuální minuty  
  
- **%%**Znak procenta  
  
 `nID`  
 ID řetězec, který identifikuje tento formát.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` objekt, který obsahuje formátovaný čas.  
  
### <a name="remarks"></a>Poznámky  
 Ladicí verze knihovny zkontroluje formátování kódy a vyhodnotí, pokud kód není v seznamu výš.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]  
  
##  <a name="getdays"></a>CTimeSpan::GetDays  
 Vrátí hodnotu, která představuje počet dnů dokončení v tomto `CTimeSpan`.  
  
```
LONGLONG GetDays() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet dní, dokončení 24 hodin v časové rozpětí. Tato hodnota může být záporná, pokud je záporná. časové rozpětí.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že letní čas může způsobit `GetDays` potenciálně překvapivé výsledek. Například pokud letního času je ve skutečnosti **GetDays** hlásí počet dní mezi duben 1 a 1 může jako 29, není 30, protože jeden den v dubnu bude zkráceno o hodinu a proto nepočítá jako celý den.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]  
  
##  <a name="gethours"></a>CTimeSpan::GetHours  
 Vrátí hodnotu, která představuje počet hodin, do aktuálního dne (až 23 -23).  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet hodin, do aktuálního dne. Rozsah je od -23 až 23.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]  
  
##  <a name="getminutes"></a>CTimeSpan::GetMinutes  
 Vrátí hodnotu, která představuje počet minut do aktuální hodiny (-59 do 59).  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet minut do aktuální hodiny. Rozsah je od -59 do 59.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetHours](#gethours).  
  
##  <a name="getseconds"></a>CTimeSpan::GetSeconds  
 Vrátí hodnotu, která představuje počet sekund do aktuální minuty (-59 do 59).  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet sekund do aktuální minuty. Rozsah je od -59 do 59.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetHours](#gethours).  
  
##  <a name="gettimespan"></a>CTimeSpan::GetTimeSpan  
 Vrátí hodnotu `CTimeSpan` objektu.  
  
```
__ time64_t GetTimeSpan() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktuální hodnota `CTimeSpan` objektu.  
  
##  <a name="gettotalhours"></a>CTimeSpan::GetTotalHours  
 Vrátí hodnotu, která představuje celkový počet hodin dokončení v tomto `CTimeSpan`.  
  
```
LONGLONG GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí celkový počet hodin dokončení v tomto `CTimeSpan`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]  
  
##  <a name="gettotalminutes"></a>CTimeSpan::GetTotalMinutes  
 Vrátí hodnotu, která představuje celkový počet minut dokončení v tomto `CTimeSpan`.  
  
```
LONGLONG GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí celkový počet minut na dokončení v tomto `CTimeSpan`.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetTotalHours](#gettotalhours).  
  
##  <a name="gettotalseconds"></a>CTimeSpan::GetTotalSeconds  
 Vrátí hodnotu, která představuje celkový počet sekund dokončení v tomto `CTimeSpan`.  
  
```
LONGLONG GetTotalSeconds() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí celkový počet sekund dokončení v tomto `CTimeSpan`.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetTotalHours](#gettotalhours).  
  
##  <a name="operator_add_-"></a>CTimeSpan::operator +, -  
 Přidá a odečítá `CTimeSpan` objekty.  
  
```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 Hodnota k přidání do `CTimeSpan` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CTimeSpan` objekt reprezentující výsledek operace.  
  
### <a name="remarks"></a>Poznámky  
 Tyto dva operátory umožňují sčítání a odečítání `CTimeSpan` objektů do a od sebe navzájem.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>CTimeSpan::operator +=-=  
 Přidá a odečítá `CTimeSpan` objekt do a z tohoto `CTimeSpan`.  
  
```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 Hodnota k přidání do `CTimeSpan` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktualizovaný `CTimeSpan` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tyto operátory umožňují sčítání a odečítání `CTimeSpan` objekt do a z tohoto `CTimeSpan`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]  
  
##  <a name="serialize64"></a>CTimeSpan::Serialize64  
  
> [!NOTE]
>  Tato metoda je k dispozici v projektech MFC pouze.  
  
 Serializuje data přidružená k členské proměnné do nebo z archivu.  
  
```
CArchive& Serialize64(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 `ar`  
 `CArchive` Objekt, který chcete aktualizovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktualizovaný `CArchive` objektu.  
  
## <a name="see-also"></a>Viz také  
 [asctime –, _wasctime –](../../c-runtime-library/reference/asctime-wasctime.md)   
 [_ftime – _ftime32 –, _ftime64 –](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime – _gmtime32 –, _gmtime64 –](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [místní čas, _localtime32 –, _localtime64 –](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [STRFTIME –, wcsftime –, _strftime_l –, _wcsftime_l –](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [čas, _time32 –, _time64 –](../../c-runtime-library/reference/time-time32-time64.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)


