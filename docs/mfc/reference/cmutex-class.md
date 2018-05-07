---
title: Třída CMutex | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50d2d68aedaf1d5560c39971e9dd5f74b4492ac6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmutex-class"></a>CMutex – třída
Představuje "mutex" – na synchronizační objekt, který umožňuje jedno vlákno vzájemně se vylučuje přístupu k prostředku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMutex : public CSyncObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMutex::CMutex](#cmutex)|Vytvoří `CMutex` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Mutex – třídy jsou užitečné, když může být povoleno pouze jedno vlákno najednou upravovat data nebo jiný řízené prostředek. Například přidání uzlů do odkazovaného seznamu je proces, který pouze má být povoleno jedno vlákno najednou. Pomocí `CMutex` objektu k řízení odkazovaného seznamu pouze jedno vlákno najednou můžete získat přístup k seznamu.  
  
 Použít `CMutex` objektu, vytvořit `CMutex` objektu, když je to potřeba. Zadejte název mutex, chcete čekat na a že vaše aplikace by měl původně jeho vlastníkem. Mutex můžete poté přistoupit, když se vrátí konstruktoru. Volání [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) po dokončení přístup k řízenému prostředku.  
  
 Alternativní metoda pro používání `CMutex` objektů je přidání proměnné typu `CMutex` jako datový člen třídy chcete ovládacího prvku. Při vytváření objektu řízené volání konstruktoru `CMutex` zadání Pokud mutex původně vlastní, název mutex (Pokud se použije přes hranice procesu) a požadovaného atributů zabezpečení – datový člen.  
  
 Pro přístup k prostředkům řídí `CMutex` objekty tímto způsobem, nejprve vytvořte proměnnou buď typu [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo typ [CMultiLock](../../mfc/reference/cmultilock-class.md) ve vašem prostředku přístup – členská funkce. Potom zavolejte zámek objektu `Lock` – členská funkce (například [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). V tomto okamžiku vašeho vlákna budou buď získat přístup k prostředku, počkat na prostředek, který uvolnit a získat přístup nebo počkejte prostředek k uvolnění a vypršení časového limitu, nejsou-li získat přístup k prostředku. V každém případě prostředku přistupovalo způsobem bezpečné pro přístup z více vláken. K uvolnění prostředku, použijte objekt zámků `Unlock` – členská funkce (například [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), nebo Povolit zámek objektu tak, aby spadal mimo rozsah.  
  
 Další informace o používání `CMutex` objekty, najdete v článku [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmt.h  
  
##  <a name="cmutex"></a>  CMutex::CMutex  
 Konstrukce a pojmenované nebo nepojmenované `CMutex` objektu.  
  
```  
CMutex(
    BOOL bInitiallyOwn = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `bInitiallyOwn`  
 Určuje při vytváření vlákna `CMutex` objekt původně má přístup k prostředkům řídí mutex.  
  
 `lpszName`  
 Název `CMutex` objektu. Pokud existuje jiný objekt mutex se stejným názvem, `lpszName` musí zadat, pokud objekt se použije přes hranice procesu. Pokud **NULL**, bude mutex nepojmenované. Pokud název odpovídá existující objekt mutex, konstruktoru vytvoří novou `CMutex` objekt, který odkazuje na objekt mutex s tímto názvem. Pokud název odpovídá existující objekt synchronizace, který není mutex, konstrukce se nezdaří.  
  
 `lpsaAttribute`  
 Atributy zabezpečení pro objekt mutex. Úplný popis tuto strukturu, najdete v části [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Přístup k nebo verzi `CMutex` objektu, vytvoření [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) objekt a volání jeho [zámku](../../mfc/reference/csinglelock-class.md#lock) a [odemčení](../../mfc/reference/csinglelock-class.md#unlock) Členské funkce. Pokud `CMutex` objekt se používá samostatné, volejte jeho `Unlock` – členská funkce pro uvolnění.  
  
> [!IMPORTANT]
>  Po vytvoření `CMutex` objektu, použijte [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) zajistit, že mutex ještě neexistovaly. Pokud objekt mutex neočekávaně neexistuje, může to znamenat podvodný proces obsazení a může být hodláte použít mutex závadně. V takovém případě je zavřít popisovač a pokračovat, jako kdyby došlo k chybě při vytváření objektu doporučeného postupu zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [CSyncObject – třída](../../mfc/reference/csyncobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



