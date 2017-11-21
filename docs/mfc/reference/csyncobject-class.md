---
title: "Třída CSyncObject | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
dev_langs: C++
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 66d21e3e2a9e530772419a269ea5e95e5daf35e3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="csyncobject-class"></a>CSyncObject – třída
Čistý virtuální třídu, která poskytuje funkce, které jsou společné pro objekty synchronizace v Win32.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSyncObject : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSyncObject::CSyncObject](#csyncobject)|Vytvoří `CSyncObject` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSyncObject::Lock](#lock)|Získáte přístup k objektu synchronizace.|  
|[CSyncObject::Unlock](#unlock)|Získáte přístup k objektu synchronizace.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSyncObject::operator POPISOVAČ](#operator_handle)|Poskytuje přístup k objektu synchronizace.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CSyncObject::m_hObject](#m_hobject)|Popisovač základní objekt synchronizace.|  
  
## <a name="remarks"></a>Poznámky  
 Knihovny Microsoft Foundation Class poskytuje několik třídy odvozené od třídy `CSyncObject`. Jedná se o [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), a [prohlížení](../../mfc/reference/csemaphore-class.md).  
  
 Informace o tom, jak používat objekty synchronizace, najdete v článku [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSyncObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmt.h  
  
##  <a name="csyncobject"></a>CSyncObject::CSyncObject  
 Vytvoří objekt synchronizace se zadaným názvem.  
  
```  
explicit CSyncObject(LPCTSTR pstrName);  
virtual ~CSyncObject();
```  
  
### <a name="parameters"></a>Parametry  
 `pstrName`  
 Název objektu. Pokud **NULL**, *pstrName* bude mít hodnotu null.  
  
##  <a name="lock"></a>CSyncObject::Lock  
 Volání této funkce můžete získat přístup k prostředkům řídí objekt synchronizace.  
  
```  
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `dwTimeout`  
 Určuje dobu v milisekundách pro čekání synchronizace objekt, který má být k dispozici (signalizovala). Pokud **NEKONEČNÉ**, `Lock` budou čekat na objekt signalizace před vrácením.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud objekt synchronizace signalizace, `Lock` úspěšně vrátí a vlákno nyní vlastní objekt. Pokud se objekt synchronizace nonsignaled (není k dispozici), `Lock` synchronizace objekt, který má stát signál, až číslo zadané v milisekundách, po kterou bude čekat *dwTimeOut* parametr. Pokud objekt synchronizace stane signál není ve stanoveném čase, `Lock` vrátí chybu.  
  
##  <a name="m_hobject"></a>CSyncObject::m_hObject  
 Popisovač základní objekt synchronizace.  
  
```  
HANDLE m_hObject;  
```  
  
##  <a name="operator_handle"></a>CSyncObject::operator POPISOVAČ  
 Použít tento operátor. Chcete-li získat popisovač `CSyncObject` objektu.  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu popisovač objektu synchronizace; v opačném **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač můžete přímo volat rozhraní API systému Windows.  
  
##  <a name="unlock"></a>CSyncObject::Unlock  
 Prohlášení o `Unlock` bez parametrů je čistě virtuální funkce a musí být přepsány všechny třídy odvozené od `CSyncObject`.  
  
```  
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,  
    LPLONG lpPrevCount = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lCount`  
 Výchozí implementace používá není.  
  
 `lpPrevCount`  
 Výchozí implementace používá není.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vždy vrátí **TRUE**.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace deklarace s dva parametry vždy vrátí **TRUE**. Tato funkce je volána k uvolnění přístup k objektu synchronizace vlastníkem volající vlákno. Druhý prohlášení je stanoveno synchronizačními objekty, jako je například semaforů, které umožňují přístup více řízené prostředku.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



