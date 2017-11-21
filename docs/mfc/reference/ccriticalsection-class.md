---
title: "Třída CCriticalSection | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
dev_langs: C++
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 351541763039abb4095785d562ee9ab22b30b74a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccriticalsection-class"></a>CCriticalSection – třída
Reprezentuje "kritické oddíl" – na synchronizační objekt, který umožňuje jedno vlákno najednou k přístupu k prostředku nebo části kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCriticalSection : public CSyncObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CCriticalSection::CCriticalSection](#ccriticalsection)|Vytvoří `CCriticalSection` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CCriticalSection::Lock](#lock)|Použijte k získání přístupu k `CCriticalSection` objektu.|  
|[CCriticalSection::Unlock](#unlock)|Verze `CCriticalSection` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CCriticalSection::operator CRITICAL_SECTION *](#operator_critical_section_star)|Načte ukazatel na interní **CRITICAL_SECTION** objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CCriticalSection::m_sect](#m_sect)|A **CRITICAL_SECTION** objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Kritické oddíly jsou užitečné, když může být povoleno pouze jedno vlákno najednou upravovat data nebo jiný řízené prostředek. Například přidání uzlů do odkazovaného seznamu je proces, který pouze má být povoleno jedno vlákno najednou. Pomocí `CCriticalSection` objektu k řízení odkazovaného seznamu pouze jedno vlákno najednou můžete získat přístup k seznamu.  
  
> [!NOTE]
>  Funkce `CCriticalSection` třída poskytuje skutečné Win32 **CRITICAL_SECTION** objektu.  
  
 Kritické oddíly se používají místo mutex – třídy (viz [CMutex](../../mfc/reference/cmutex-class.md)) Pokud rychlost je klíčová a prostředek se nepoužijí přes hranice procesu.  
  
 Existují dvě metody pro použití `CCriticalSection` objektu: samostatné a vložené v třídě.  
  
-   Samostatné metodu použít samostatný `CCriticalSection` objektu, vytvořit `CCriticalSection` objektu, když je to potřeba. Po úspěšné vrátit z konstruktoru, explicitně zamknout objekt s volání [zámku](#lock). Volání [odemčení](#unlock) po dokončení přístup k části důležité. Tato metoda při přesnější někomu čtení vašeho zdrojového kódu, je více náchylné k chybám jako nezapomeňte při zamykání a odemykání kritická sekce před a za přístup.  
  
     Více vhodnější metodou je použití [CSingleLock](../../mfc/reference/csinglelock-class.md) třídy. Je také `Lock` a `Unlock` metoda, ale nemusíte si dělat starosti o odemknutí prostředku, pokud dojde k výjimce.  
  
-   Vložené metoda třídu můžete také sdílet s více vlákny přidáním `CCriticalSection`– typ datový člen třídy a uzamčení datového člena v případě potřeby.  
  
 Další informace o používání `CCriticalSection` objekty, najdete v článku [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CCriticalSection`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmt.h  
  
##  <a name="ccriticalsection"></a>CCriticalSection::CCriticalSection  
 Vytvoří `CCriticalSection` objektu.  
  
```  
CCriticalSection();
```  
  
### <a name="remarks"></a>Poznámky  
 Přístup k nebo verzi `CCriticalSection` objektu, vytvoření [CSingleLock](../../mfc/reference/csinglelock-class.md) objekt a volání jeho [zámku](../../mfc/reference/csinglelock-class.md#lock) a [odemčení](../../mfc/reference/csinglelock-class.md#unlock) členské funkce. Pokud `CCriticalSection` objekt se používá samostatné, volejte jeho [odemčení](#unlock) – členská funkce pro uvolnění.  
  
 Pokud se nezdaří přidělit požadované systémové paměti, paměti výjimky konstruktoru (typu [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) automaticky vyvolá výjimku.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CCriticalSection::Lock](#lock).  
  
##  <a name="lock"></a>CCriticalSection::Lock  
 Volání této funkce člen k získání přístupu k objektu kritická sekce.  
  
```  
BOOL Lock();  
BOOL Lock(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>Parametry  
 `dwTimeout`  
 `Lock`ignoruje hodnotě tohoto parametru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `Lock`je blokování volání, která nevrátí, dokud nebude objekt kritická sekce signalizace (k dispozici).  
  
 Pokud jsou nutné vypršel počká, můžete použít [CMutex](../../mfc/reference/cmutex-class.md) objektu místo `CCriticalSection` objektu.  
  
 Pokud `Lock` nepodaří přidělit potřebné systémové paměti, výjimka paměti (typu [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) automaticky vyvolá výjimku.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje způsob vnořené kritická sekce řízením přístupu ke sdíleným prostředkům (statické `_strShared` objektu) pomocí sdílenou `CCriticalSection` objektu. `SomeMethod` Funkce ukazuje aktualizace sdíleného prostředku bezpečným způsobem.  
  
 [!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]  
  
##  <a name="m_sect"></a>CCriticalSection::m_sect  
 Obsahuje kritická sekce objekt, který je používán všechny `CCriticalSection` metody.  
  
```  
CRITICAL_SECTION m_sect;  
```  
  
##  <a name="operator_critical_section_star"></a>CCriticalSection::operator CRITICAL_SECTION *  
 Načte **CRITICAL_SECTION** objektu.  
  
```  
operator CRITICAL_SECTION*();
```   
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce načíst ukazatel na interní **CRITICAL_SECTION** objektu.  
  
##  <a name="unlock"></a>CCriticalSection::Unlock  
 Verze `CCriticalSection` objekt pro použití jiné vlákno.  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `CCriticalSection` vlákno se vlastníkem objektu, a verze byla úspěšná, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CCriticalSection` používá samostatné, `Unlock` musí být volána hned po dokončení použití prostředků řízené kritická sekce. Pokud [CSingleLock](../../mfc/reference/csinglelock-class.md) objekt se používá, `CCriticalSection::Unlock` bude volána objektem zámku `Unlock` – členská funkce.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CCriticalSection::Lock](#lock).  
  
## <a name="see-also"></a>Viz také  
 [CSyncObject – třída](../../mfc/reference/csyncobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CMutex – třída](../../mfc/reference/cmutex-class.md)
