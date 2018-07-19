---
title: CMultiLock – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a098f275ec0c7b553d7ac192d7b588ffa6dcfa1b
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849870"
---
# <a name="cmultilock-class"></a>CMultiLock – třída
Představuje mechanismus řízení přístupu, který se používá při řízení přístupu k prostředkům ve vícevláknovém programu.  
  
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
|[CMultiLock::IsLocked](#islocked)|Určuje, když se konkrétní synchronizační objekt v poli změnit.|  
|[CMultiLock::Lock](#lock)|Čeká se na pole synchronizace objektů.|  
|[CMultiLock::Unlock](#unlock)|Uvolní všechny objekty vlastněné synchronizace.|  
  
## <a name="remarks"></a>Poznámky  
 `CMultiLock` nemá základní třídu.  
  
 Chcete-li použít synchronizační třídy [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), a [CEvent](../../mfc/reference/cevent-class.md), můžete vytvořit buď `CMultiLock` nebo [CSingleLock](../../mfc/reference/csinglelock-class.md)objektu pro čekání na a uvolnění objektu synchronizace. Použít `CMultiLock` pokud existuje více objektů, které můžete použít v určitou dobu. Použití `CSingleLock` kdy je potřeba jenom čekat na jeden objekt v čase.  
  
 Použití `CMultiLock` objektu, musíte nejprve vytvořit pole, které chcete čekat na synchronizaci objektů. Pak zavolejte `CMultiLock` konstruktoru objektu uvnitř členské funkce ve třídě řízené prostředků. Zavolejte [Zámek](#lock) členskou funkci k určení, jestli je prostředek k dispozici (signalizován). Pokud je, pokračujte zbývajícími členskou funkci. Pokud je k dispozici žádný prostředek, počkejte určenou dobu pro prostředek uvolnit nebo vrátí hodnotu neúspěch. Po dokončení použití prostředku se buď zavolat [odemknout](#unlock) fungovat, pokud `CMultiLock` je znovu použít, nebo povolíte `CMultiLock` objekt, který se má zničit.  
  
 `CMultiLock` objekty jsou nejužitečnější tehdy, pokud vlákno obsahuje velký počet `CEvent` objekty, které může reagovat. Vytvořit pole obsahující všechny `CEvent` ukazatele a volání `Lock`. To způsobí, že vlákno počkat, až některou událost je signalizována.  
  
 Další informace o tom, jak používat `CMultiLock` objekty, najdete v článku [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CMultiLock`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmt.h  
  
##  <a name="cmultilock"></a>  CMultiLock::CMultiLock  
 Vytvoří `CMultiLock` objektu.  
  
```  
CMultiLock(
    CSyncObject* ppObjects [ ],  
    DWORD dwCount,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *ppObjects*  
 Pole ukazatelů na objekty synchronizace, které chcete čekat. Nemůže mít hodnotu NULL.  
  
 *dwCount*  
 Počet objektů v *ppObjects*. Musí být větší než 0.  
  
 *bInitialLock*  
 Určuje, zda počáteční pokus o přístup k libovolné zadané objekty.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána po vytvoření pole synchronizace objektů čekat. Obvykle je volat z vlákna, který musíte počkat, pro jeden z objektů synchronizace k dispozici.  
  
##  <a name="islocked"></a>  CMultiLock::IsLocked  
 Určuje, zda je zadaný objekt nonsignaled (není k dispozici).  
  
```  
BOOL IsLocked(DWORD dwItem);
```  
  
### <a name="parameters"></a>Parametry  
 *dwItem*  
 Index v poli objektů odpovídající objekt, jehož stav je dotazována.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je zadaný objekt uzamčen; jinak 0.  
  
##  <a name="lock"></a>  CMultiLock::Lock  
 Voláním této funkce získáte přístup k jednomu nebo více prostředků, které řídí zadaný pro synchronizaci objektů `CMultiLock` konstruktoru.  
  
```  
DWORD Lock(
    DWORD dwTimeOut = INFINITE,  
    BOOL bWaitForAll = TRUE,  
    DWORD dwWakeMask = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *dwTimeOut*  
 Určuje dobu čekání na synchronizační objekt k dispozici (signalizován). Pokud je NEKONEČNÉ, `Lock` budou čekat na objekt je signál, před vrácením.  
  
 *bWaitForAll*  
 Určuje, zda musí být signalizovány čekalo se všechny objekty ve stejnou dobu před vrácením. Pokud má hodnotu FALSE, `Lock` vrátí při signalizován některý z objektů čekat.  
  
 *dwWakeMask*  
 Určuje další podmínky, které jsou povoleny pro přerušení čekání. Úplný seznam dostupných možností pro tento parametr, naleznete v tématu [MsgWaitForMultipleObjects](http://msdn.microsoft.com/library/windows/desktop/ms684242) v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud `Lock` selže, vrátí - 1. V případě úspěchu vrátí jednu z následujících hodnot:  
  
-   WAIT_OBJECT_0 a WAIT_OBJECT_0 + (počet objektů,-1)  
  
     Pokud *bWaitForAll* má hodnotu TRUE, všechny objekty jsou signalizován (k dispozici). Pokud *bWaitForAll* má hodnotu FALSE, návratová hodnota – WAIT_OBJECT_0 je index v poli objektů objektu, který je signalizována (k dispozici).  
  
- WAIT_OBJECT_0 + (počet objektů)  
  
     Události podle *dwWakeMask* je k dispozici ve vstupní frontě vlákna.  
  
-   WAIT_ABANDONED_0 a WAIT_ABANDONED_0 + (počet objektů,-1)  
  
     Pokud *bWaitForAll* hodnotu TRUE, jsou všechny objekty signalizován, a nejméně jeden z objektů je objekt mutex opuštěné. Pokud *bWaitForAll* má hodnotu FALSE, návratová hodnota – WAIT_ABANDONED_0 je index v poli objektů objektu opuštěné vzájemně vyloučený přístup, který splnil čekání.  
  
- WAIT_TIMEOUT  
  
     V zadaném časovém intervalu *dwTimeOut* bez čekání následující po vypršení platnosti.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bWaitForAll* má hodnotu TRUE, `Lock` úspěšně vrátí ihned poté, co všechny objekty synchronizace signálování současně. Pokud *bWaitForAll* má hodnotu FALSE, `Lock` vrátí ihned poté, co se stane signalizován jeden nebo více objektů synchronizace.  
  
 Pokud `Lock` není možné výsledky okamžitě, počká na více než číslo zadané v milisekundách *dwTimeOut* parametr před vrácením. Pokud *dwTimeOut* je NEKONEČNÉ, `Lock` nebude vracet, dokud získali přístup k objektu nebo podmínku podle *dwWakeMask* byla splněna. Jinak, pokud `Lock` byl schopen získat objekt synchronizace, vrátí úspěšně; Pokud ne, vrátí chybu.  
  
##  <a name="unlock"></a>  CMultiLock::Unlock  
 Uvolní objekt synchronizace vlastněné `CMultiLock`.  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lCount*  
 K uvolnění se počítá počet odkaz. Musí být větší než 0. Pokud zadané by způsobila objektu počet překročí maximální, hodnota tohoto čítače se nemění a funkce vrátí FALSE.  
  
 *lPrevCount*  
 Odkazuje na proměnnou, která zobrazí počet předchozího pro objekt synchronizace. Pokud má hodnotu NULL, nevrátí se předchozího počtu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud funkce byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána `CMultiLock`jeho destruktor.  
  
 První formulář `Unlock` pokusí o odemknutí synchronizace objektem spravovaným `CMultiLock`. Tedy o druhou podobu `Unlock` pokusí o odemknutí `CSemaphore` objekty vlastněné `CMultiLock`. Pokud `CMultiLock` nevlastní žádné uzamčené `CSemaphore` objektu, funkce vrátí FALSE; v opačném případě vrátí hodnotu TRUE. *lCount* a *lpPrevCount* jsou stejné jako parametry [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). Tedy o druhou podobu `Unlock` zřídka lze použít na multilock situacích.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



