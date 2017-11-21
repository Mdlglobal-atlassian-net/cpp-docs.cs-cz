---
title: "Třída CSingleLock | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
dev_langs: C++
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0dd07d79c97a9fb3368d20ee68df2332ba7ce5cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="csinglelock-class"></a>CSingleLock – třída
Představuje mechanismus řízení přístupu používá při řízení přístupu k prostředku v programu s více vlákny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSingleLock  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSingleLock::CSingleLock](#csinglelock)|Vytvoří `CSingleLock` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSingleLock::IsLocked](#islocked)|Určuje, jestli není objekt uzamčen.|  
|[CSingleLock::Lock](#lock)|Čeká na objekt synchronizace.|  
|[CSingleLock::Unlock](#unlock)|Uvolní objekt synchronizace.|  
  
## <a name="remarks"></a>Poznámky  
 `CSingleLock`nemá základní třídu.  
  
 Chcete-li používat synchronizační třídy [prohlížení](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), a [CEvent](../../mfc/reference/cevent-class.md), je nutné vytvořit buď `CSingleLock` nebo [CMultiLock](../../mfc/reference/cmultilock-class.md) objekt, který má čekat na a verzí objekt synchronizace. Použití `CSingleLock` když potřebujete jenom čekat na jeden objekt v čase. Použít **CMultiLock** když existuje více objektů, které můžete použít v určitou dobu.  
  
 Použít `CSingleLock` objektu, volání jeho konstruktoru uvnitř členské funkce ve třídě řízené prostředků. Potom zavolejte [islocked –](#islocked) – členská funkce k určení, zda je prostředek k dispozici. Pokud se jedná, pokračujte se zbývajícími – členská funkce. Pokud prostředek není k dispozici, počkejte zadanou dobu pro daný prostředek k uvolnění nebo vrátí hodnotu neúspěch. Po dokončení použít prostředku buď volání [odemčení](#unlock) fungovat, pokud `CSingleLock` objektu je znovu použít, nebo povolíte `CSingleLock` objekt, který má být zničený.  
  
 `CSingleLock`objekty vyžadují přítomnost objekt odvozené od [CSyncObject](../../mfc/reference/csyncobject-class.md). Je to obvykle datový člen třídy řízené prostředků. Další informace o tom, jak používat `CSingleLock` objekty, najdete v článku [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CSingleLock`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmt.h  
  
##  <a name="csinglelock"></a>CSingleLock::CSingleLock  
 Vytvoří `CSingleLock` objektu.  
  
```  
explicit CSingleLock(
    CSyncObject* pObject,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `pObject`  
 Odkazuje na objekt synchronizace nelze přistupovat. Nemůže být **NULL**.  
  
 `bInitialLock`  
 Určuje, jestli na začátku pokusí o přístup k zadaného objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je obecně volána z v k přístupu členská funkce řízené prostředku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]  
  
##  <a name="islocked"></a>CSingleLock::IsLocked  
 Určuje, pokud objekt přidružený `CSingleLock` objekt je nonsignaled (není k dispozici).  
  
```  
BOOL IsLocked();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud není objekt uzamčen; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]  
  
##  <a name="lock"></a>CSingleLock::Lock  
 Volání této funkce můžete získat přístup k prostředkům řídí synchronizace objekt zadaný do `CSingleLock` konstruktor.  
  
```  
BOOL Lock(DWORD dwTimeOut = INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 *dwTimeOut*  
 Určuje dobu čekání na synchronizační objekt, který má být k dispozici (signalizovala). Pokud **NEKONEČNÉ**, `Lock` budou čekat na objekt signalizace před vrácením.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud objekt synchronizace signalizace, `Lock` úspěšně vrátí a vlákno nyní vlastní objekt. Pokud se objekt synchronizace nonsignaled (není k dispozici), `Lock` synchronizace objekt, který má stát signál, až číslo zadané v milisekundách, po kterou bude čekat *dwTimeOut* parametr. Pokud objekt synchronizace stane signál není ve stanoveném čase, `Lock` vrátí chybu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
##  <a name="unlock"></a>CSingleLock::Unlock  
 Uvolní objekt synchronizace vlastníkem `CSingleLock`.  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lCount`  
 Počet přístupů k uvolnění. Musí být větší než 0. Pokud počet objektu, který má být vyšší než její maximální by způsobilo určenou dobu, není-li změnit počet a funkce vrátí hodnotu **FALSE**.  
  
 `lPrevCount`  
 Odkazuje na proměnnou, která bude přijímat předchozí počet objekt synchronizace. Pokud **NULL**, počet předchozího nevrátí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána `CSingleLock`na destruktor.  
  
 Pokud potřebujete více než jeden přístup počet semafor verzi, použijte o druhou podobu `Unlock` a zadat počet přístupů k uvolnění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CMultiLock – třída](../../mfc/reference/cmultilock-class.md)
