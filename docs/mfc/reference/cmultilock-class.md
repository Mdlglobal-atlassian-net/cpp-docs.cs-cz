---
title: "Třída CMultiLock | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc3c391c624351b2835e1ec497d78bc191eb1fe7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmultilock-class"></a>CMultiLock – třída
Představuje mechanismus řízení přístupu používá při řízení přístupu k prostředkům v programu s více vlákny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMultiLock  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMultiLock::CMultiLock](#cmultilock)|Vytvoří `CMultiLock` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMultiLock::IsLocked](#islocked)|Určuje, jestli není uzamčen na konkrétní synchronizační objekt v poli.|  
|[CMultiLock::Lock](#lock)|Čeká na pole objektů synchronizace.|  
|[CMultiLock::Unlock](#unlock)|Uvolní všechny objekty ve vlastnictví synchronizace.|  
  
## <a name="remarks"></a>Poznámky  
 `CMultiLock`nemá základní třídu.  
  
 Chcete-li používat synchronizační třídy [prohlížení](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), a [CEvent](../../mfc/reference/cevent-class.md), můžete vytvořit buď **CMultiLock** nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) objekt, který má čekat na a verzí objekt synchronizace. Použít **CMultiLock** když existuje více objektů, které můžete použít v určitou dobu. Použití `CSingleLock` když potřebujete jenom čekat na jeden objekt v čase.  
  
 Použít **CMultiLock** objektu, nejprve vytvořit pole objektů synchronizace, které chcete čekat na. Pak zavolejte **CMultiLock** konstruktoru objektu uvnitř členské funkce ve třídě řízené prostředků. Potom zavolejte [zámku](#lock) – členská funkce k určení, zda je prostředek k dispozici (signalizovala). Pokud jeden, pokračujte se zbývajícími – členská funkce. Pokud je k dispozici žádný prostředek, počkejte zadanou dobu pro prostředek k uvolnění nebo vrátí hodnotu neúspěch. Po dokončení použít prostředku buď volání [odemčení](#unlock) fungovat, pokud **CMultiLock** objektu je znovu použít, nebo povolíte **CMultiLock** objekt, který má být zničený.  
  
 **CMultiLock** objekty jsou velmi užitečné, když vlákno má velký počet `CEvent` objekty, které může reagovat. Vytvoření pole obsahující všechny `CEvent` ukazatelů a volání `Lock`. To způsobí, že vlákno počkat, dokud jedna z událostí signalizace.  
  
 Další informace o tom, jak používat **CMultiLock** objekty, najdete v článku [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CMultiLock`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmt.h  
  
##  <a name="cmultilock"></a>CMultiLock::CMultiLock  
 Vytvoří **CMultiLock** objektu.  
  
```  
CMultiLock(
    CSyncObject* ppObjects [ ],  
    DWORD dwCount,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `ppObjects`  
 Ukazatelé na objekty synchronizace, které chcete být čekali pole. Nemůže být **NULL**.  
  
 `dwCount`  
 Počet objektů v `ppObjects`. Musí být větší než 0.  
  
 `bInitialLock`  
 Určuje, jestli na začátku pokusí o přístup k zadané objekty.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána po vytvoření pole objektů synchronizace se čekali. Obvykle je volána v rámci vlákno, které musí čekat na některý z objektů synchronizace k dispozici.  
  
##  <a name="islocked"></a>CMultiLock::IsLocked  
 Určuje, zda je zadaný objekt nonsignaled (není k dispozici).  
  
```  
BOOL IsLocked(DWORD dwItem);
```  
  
### <a name="parameters"></a>Parametry  
 *dwItem*  
 Index v poli objekty odpovídající objektu, jejichž stav je která je dotazována.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zadaný objekt je uzamčené; jinak 0.  
  
##  <a name="lock"></a>CMultiLock::Lock  
 Volání této funkce můžete získat přístup k jedné nebo více prostředků řízené objekty synchronizace zadané **CMultiLock** konstruktor.  
  
```  
DWORD Lock(
    DWORD dwTimeOut = INFINITE,  
    BOOL bWaitForAll = TRUE,  
    DWORD dwWakeMask = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *dwTimeOut*  
 Určuje dobu čekání na synchronizační objekt, který má být k dispozici (signalizovala). Pokud **NEKONEČNÉ**, `Lock` budou čekat na objekt signalizace před vrácením.  
  
 `bWaitForAll`  
 Určuje, zda všechny objekty čekali musí stát signál ve stejnou dobu před vrácením. Pokud **FALSE**, `Lock` bude vracet signalizace některého z objektů čekali.  
  
 `dwWakeMask`  
 Určuje další podmínky, které jsou povoleny na zrušení čekání. Úplný seznam dostupných možností pro tento parametr, najdete v části [MsgWaitForMultipleObjects](http://msdn.microsoft.com/library/windows/desktop/ms684242) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud `Lock` nezdaří, vrátí hodnotu - 1. V případě úspěchu vrátí jednu z následujících hodnot:  
  
-   Mezi **WAIT_OBJECT_0** a **WAIT_OBJECT_0** + (počet objektů - 1)  
  
     Pokud `bWaitForAll` je **TRUE**, všechny objekty jsou signalizace (k dispozici). Pokud `bWaitForAll` je **FALSE**, návratová hodnota - **WAIT_OBJECT_0** je index v poli objektů objektu, který signalizace (k dispozici).  
  
- **WAIT_OBJECT_0** + (počet objektů)  
  
     Událost zadaný v `dwWakeMask` je k dispozici ve vstupní frontě vlákna.  
  
-   Mezi **WAIT_ABANDONED_0** a **WAIT_ABANDONED_0** + (počet objektů - 1)  
  
     Pokud `bWaitForAll` je **TRUE**, jsou všechny objekty signál a alespoň jeden z objektů je objekt mutex opuštěného. Pokud `bWaitForAll` je **FALSE**, návratová hodnota - **WAIT_ABANDONED_0** je index v poli objektů opuštěného mutex objektu, která by uspokojila čekání.  
  
- **WAIT_TIMEOUT**  
  
     Časový limit zadaný v *dwTimeOut* platnost bez čekání úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bWaitForAll` je **TRUE**, `Lock` úspěšně vrátí také všechny objekty synchronizace stát signalizovala současně. Pokud `bWaitForAll` je **FALSE**, `Lock` vrátí, jakmile bude signál, jeden nebo více objektů synchronizace.  
  
 Pokud `Lock` nemůže vrátit okamžitě, bude čekat pro více než číslo zadané v milisekundách, po kterou *dwTimeOut* parametr před vrácením. Pokud *dwTimeOut* je **NEKONEČNÉ**, `Lock` nevrátí, dokud se získávají přístup k objektu nebo podmínku zadaný v `dwWakeMask` byla splněna. Jinak Pokud `Lock` byl nelze získat objekt synchronizace, vrátí úspěšně; Pokud ne, vrátí chybu.  
  
##  <a name="unlock"></a>CMultiLock::Unlock  
 Uvolní objekt synchronizace vlastníkem `CMultiLock`.  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lCount`  
 Spočítá počet odkaz k uvolnění. Musí být větší než 0. Pokud počet objektu, který má být vyšší než její maximální by způsobilo určenou dobu, není-li změnit počet a funkce vrátí hodnotu **FALSE**.  
  
 `lPrevCount`  
 Odkazuje na proměnnou, která bude přijímat předchozí počet pro objekt synchronizace. Pokud **NULL**, počet předchozího nevrátí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána `CMultiLock`na destruktor.  
  
 První formu `Unlock` pokusí o odemknutí objekt synchronizace spravuje `CMultiLock`. O druhou podobu `Unlock` pokusí o odemknutí `CSemaphore` objekty vlastněné `CMultiLock`. Pokud `CMultiLock` nevlastní žádné uzamčeném `CSemaphore` objektu, funkce vrátí hodnotu **FALSE**, jinak vrátí hodnotu **TRUE**. `lCount`a `lpPrevCount` jsou stejné jako parametry [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). O druhou podobu `Unlock` zřídka platí pro multilock situacích.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



