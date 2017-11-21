---
title: "Třída CEvent | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
dev_langs: C++
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7a44b005738103b91fd435bdc88f5fef9a1888a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cevent-class"></a>CEvent – třída
Představuje událost, která je na synchronizační objekt, který umožňuje jedno vlákno oznámit jiné, který došlo k události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CEvent : public CSyncObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CEvent::CEvent](#cevent)|Vytvoří `CEvent` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CEvent::PulseEvent](#pulseevent)|Nastaví událost, která má k dispozici (signalizovala), uvolní čekajících vláken a nastaví událost není k dispozici (nonsignaled).|  
|[CEvent::ResetEvent](#resetevent)|Nastaví událost není k dispozici (nonsignaled).|  
|[CEvent::SetEvent](#setevent)|Nastaví událost na k dispozici (signalizovaného) a uvolní všechny čekajících vláken.|  
|[CEvent::Unlock](#unlock)|Uvolní objekt události.|  
  
## <a name="remarks"></a>Poznámky  
 Události jsou užitečné, když vlákno musí vědět, kdy k provedení úkolu. Například podproces, který kopíruje data do archivu dat musí být upozorněni, když je k dispozici nová data. Pomocí `CEvent` objekt, který chcete upozornit vlákno kopie, pokud je k dispozici nová data vlákno co nejdříve provedení úkolu.  
  
 `CEvent`objekty mají dva typy: ruční a automatická.  
  
 Automatické `CEvent` objekt automaticky obnoví stav signalizace (není k dispozici), po vydání alespoň jedno vlákno. Ve výchozím nastavení `CEvent` objekt je automatické, pokud předáte `TRUE` pro `bManualReset` parametru během vytváření.  
  
 Ruční `CEvent` objekt zůstane ve stavu, která nastavuje [SetEvent](#setevent) nebo [ResetEvent](#resetevent) dokud další funkce je volána. Chcete-li vytvořit ruční `CEvent` objektu, předejte `TRUE` pro `bManualReset` parametru během vytváření.  
  
 Použít `CEvent` objektu, vytvořit `CEvent` objektu, pokud je to požadováno. Zadejte název události, kterou chcete čekat na a také určit, že vaše aplikace by měl původně jejím vlastníkem. Máte přístup událostí, když se vrátí konstruktoru. Volání [SetEvent](#setevent) na signál (zpřístupnění) událost objekt a potom volání [odemčení](#unlock) po dokončení přístup k řízenému prostředku.  
  
 Alternativní metoda pro používání `CEvent` objektů je přidání proměnné typu `CEvent` jako datový člen třídy chcete ovládacího prvku. Při vytváření objektu řízené volání konstruktoru `CEvent` – datový člen a určete, jestli původně signalizace události a také specifythe typ objektu událostí, který má, název události (Pokud se použije v procesu hranice) a chcete atributy zabezpečení.  
  
 Pro přístup k prostředkům řídí `CEvent` objektu tímto způsobem, nejprve vytvořte proměnnou buď typu [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo typ [CMultiLock](../../mfc/reference/cmultilock-class.md) v metodě přístup k prostředku. Potom zavolejte `Lock` metoda zámek objektu (například [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). Váš přístup z více vláken v tuto chvíli se buď získat přístup k prostředku, počkejte prostředek, který uvolnit a získat přístup nebo počkejte prostředek k uvolnění, vypršení časového limitu a nepodaří získat přístup k prostředku. V každém případě prostředku přistupovalo způsobem bezpečné pro přístup z více vláken. K uvolnění prostředku, volání `SetEvent` signál objekt události, a potom pomocí `Unlock` metoda zámek objektu (například [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)), nebo nechte zámek objektu dostala mimo rozsah.  
  
 Další informace o tom, jak používat `CEvent` objekty, najdete v části [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmt.h  
  
##  <a name="cevent"></a>CEvent::CEvent  
 Konstrukce a pojmenované nebo nepojmenované `CEvent` objektu.  
  
```  
CEvent(
    BOOL bInitiallyOwn = FALSE,  
    BOOL bManualReset = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `bInitiallyOwn`  
 Pokud **TRUE**, vlákno pro **CMultilock** nebo `CSingleLock` objektu je povoleno. Jinak musí počkat všechna vlákna, kteří požadují přístup k prostředku.  
  
 *bManualReset*  
 Pokud **TRUE**, určuje, že objekt události je ruční událost, jinak události objektu je automatické událost.  
  
 `lpszName`  
 Název `CEvent` objektu. Je nutné zadat Pokud objektu se použije přes hranice procesu. Pokud název odpovídá existující událost, konstruktoru vytvoří novou `CEvent` objekt, který odkazuje na události s tímto názvem. Pokud název odpovídá existující objekt synchronizace, který není událost, konstrukce se nezdaří. Pokud **NULL**, název bude mít hodnotu null.  
  
 `lpsaAttribute`  
 Atributy zabezpečení pro objekt události. Úplný popis tuto strukturu, najdete v části [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Přístup k nebo verzi `CEvent` objektu, vytvoření [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) objekt a volání jeho [zámku](../../mfc/reference/csinglelock-class.md#lock) a [odemčení](../../mfc/reference/csinglelock-class.md#unlock) Členské funkce.  
  
 Chcete-li změnit stav `CEvent` objekt, který chcete signalizace (vláken nemusí čekat), volání [SetEvent](#setevent) nebo [PulseEvent](#pulseevent). K nastavení stavu `CEvent` objekt, který chcete nonsignaled (vláken musí počkat), volání [ResetEvent](#resetevent).  
  
> [!IMPORTANT]
>  Po vytvoření `CEvent` objektu, použijte [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) zajistit, že mutex ještě neexistuje. Pokud objekt mutex neočekávaně neexistuje, může to znamenat podvodný proces obsazení a může být hodláte použít mutex závadně. V takovém případě je zavřít popisovač a pokračovat, jako kdyby došlo k chybě při vytváření objektu doporučeného postupu zabezpečení.  
  
##  <a name="pulseevent"></a>CEvent::PulseEvent  
 Nastaví stav události na signál (k dispozici), uvolní všechny čekajících vláken a jeho nonsignaled (není k dispozici) automaticky obnoví.  
  
```  
BOOL PulseEvent();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je událost ruční, jsou vydávány všechna vlákna čekání, události je nastaven na nonsignaled a `PulseEvent` vrátí. Pokud je událost automatické, vydání jedním vláknem, události je nastaven na nonsignaled a `PulseEvent` vrátí.  
  
 Pokud nejsou žádná vlákna čekají, nebo nejsou žádná vlákna, se uvolní okamžitě, `PulseEvent` nastaví stav události nonsignaled a vrátí.  
  
 `PulseEvent`používá základní Win32 `PulseEvent` funkce, které lze na okamžik odebrat ze stavu čekání pomocí postupu asynchronní volání režimu jádra. Proto `PulseEvent` nespolehlivé a by se nemělo používat nové aplikace. Další informace najdete v tématu [funkce PulseEvent](http://msdn.microsoft.com/library/windows/desktop/ms684914).  
  
##  <a name="resetevent"></a>CEvent::ResetEvent  
 Nastaví stav události nonsignaled dokud, explicitně nastavit na signalizovaného pomocí [SetEvent](#setevent) – členská funkce.  
  
```  
BOOL ResetEvent();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 To způsobí, že všechna vlákna chtějí získat přístup k této události čekání.  
  
 Tato funkce člen není používán automatické události.  
  
##  <a name="setevent"></a>CEvent::SetEvent  
 Nastaví stav události na signál, vydání žádné podprocesy čekání.  
  
```  
BOOL SetEvent();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci bylo úspěšné, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato událost je ruční, události zůstane signalizovaného až [ResetEvent](#resetevent) je volána. V takovém případě můžete uvolnit více než jedno vlákno. Pokud je automatické události, zůstane událost signalizovaného, dokud vydání jedním vláknem. Systém bude nonsignaled pak nastaven stav události. Pokud nejsou žádná vlákna čekají, zůstane stav signalizovaného, dokud vydání jedno vlákno.  
  
##  <a name="unlock"></a>CEvent::Unlock  
 Uvolní objekt události.  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud objekt události a události ve vlastnictví vlákno je automatické událost; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je volána službou vláken, které aktuálně vlastní automatické událost pro uvolnění po se provádí, pokud jejich objekt zámku se znovu použije. Pokud se objekt zámku se znovu použít, bude tato funkce volána podle destruktoru zámek objektu.  
  
## <a name="see-also"></a>Viz také  
 [CSyncObject – třída](../../mfc/reference/csyncobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)

