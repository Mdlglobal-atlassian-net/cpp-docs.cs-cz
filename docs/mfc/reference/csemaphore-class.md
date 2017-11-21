---
title: "Třída prohlížení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
dev_langs: C++
helpviewer_keywords: CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0184d013b0a36aeb77bebbba9f6e4ecef47b7f85
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="csemaphore-class"></a>Prohlížení – třída
Objekt třídy `CSemaphore` představuje "semafor" – na synchronizační objekt, který umožňuje omezený počet vláken v jedné nebo více procesech pro přístup Maintains počet vláken, na které se právě používají zadaný prostředek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSemaphore : public CSyncObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSemaphore::CSemaphore](#csemaphore)|Vytvoří `CSemaphore` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Semaforů jsou užitečné při řízení přístupu k sdílený prostředek, který podporuje pouze omezený počet uživatelů. Aktuální počet `CSemaphore` objektu je počet další uživatele povolena. Pokud je počet hodnota nula, všechny pokusí použít prostředek řídí **prohlížení** objekt bude vložen do systému fronty a počkejte, dokud se buď vypršení časového limitu nebo roste počet větší než 0. Maximální počet uživatelů, kteří mohou přístup řízené prostředku v jednom okamžiku se stanoví během vytváření `CSemaphore` objektu.  
  
 Použít **prohlížení** objektu, vytvořit `CSemaphore` objektu, když je to potřeba. Zadejte název semafor, chcete čekat na a že vaše aplikace by měl původně jeho vlastníkem. Semafor můžete přistoupit po návratu konstruktoru. Volání [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) po dokončení přístup k řízenému prostředku.  
  
 Alternativní metoda pro používání `CSemaphore` objektů je přidání proměnné typu `CSemaphore` jako datový člen třídy chcete ovládacího prvku. Při vytváření objektu řízené volání konstruktoru `CSemaphore` zadání počáteční – datový člen přístup počet, počet maximální připojení, název semafor (Pokud se použije přes hranice procesu) a potřeby atributů zabezpečení.  
  
 Pro přístup k prostředkům řídí `CSemaphore` objekty tímto způsobem, nejprve vytvořte proměnnou buď typu [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo typ [CMultiLock](../../mfc/reference/cmultilock-class.md) ve vašem prostředku přístup – členská funkce. Potom zavolejte zámek objektu `Lock` – členská funkce (například [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). V tomto okamžiku vašeho vlákna budou buď získat přístup k prostředku, počkat na prostředek, který uvolnit a získat přístup nebo počkejte prostředek k uvolnění a vypršení časového limitu, nejsou-li získat přístup k prostředku. V každém případě prostředku přistupovalo způsobem bezpečné pro přístup z více vláken. K uvolnění prostředku, použijte objekt zámků `Unlock` – členská funkce (například [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), nebo Povolit zámek objektu tak, aby spadal mimo rozsah.  
  
 Alternativně můžete vytvořit **prohlížení** objektu samostatné a k němu přístup explicitně před pokusem o přístup k řízené prostředku. Tato metoda při přesnější někomu čtení vašeho zdrojového kódu, je více náchylné k chybám.  
  
 Další informace o tom, jak používat **prohlížení** objekty, najdete v článku [Multithreading: jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CSemaphore`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmt.h  
  
##  <a name="csemaphore"></a>CSemaphore::CSemaphore  
 Konstrukce a pojmenované nebo nepojmenované `CSemaphore` objektu.  
  
```  
CSemaphore(
    LONG lInitialCount = 1,  
    LONG lMaxCount = 1,  
    LPCTSTR pstrName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lInitialCount*  
 Počet počáteční využití pro semafor. Musí být větší než nebo rovna 0 a menší než nebo rovno `lMaxCount`.  
  
 `lMaxCount`  
 Počet maximální využití pro semafor. Musí být větší než 0.  
  
 `pstrName`  
 Název semaforu. Je nutné zadat Pokud semaforu budou mít přístup přes hranice procesu. Pokud `NULL`, bude objekt nepojmenované. Pokud název odpovídá existující semafor, konstruktoru vytvoří novou `CSemaphore` objekt, který odkazuje na semafor s tímto názvem. Pokud název odpovídá existující objekt synchronizace, který není semafor, konstrukce se nezdaří.  
  
 *lpsaAttributes*  
 Atributy zabezpečení pro objekt semafor. Úplný popis tuto strukturu, najdete v části [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Přístup k nebo verzi `CSemaphore` objektu, vytvoření [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) objekt a volání jeho [zámku](../../mfc/reference/csinglelock-class.md#lock) a [odemčení](../../mfc/reference/csinglelock-class.md#unlock) Členské funkce.  
  
> [!IMPORTANT]
>  Po vytvoření `CSemaphore` objektu, použijte [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) zajistit, že mutex ještě neexistovaly. Pokud objekt mutex neočekávaně neexistuje, může to znamenat podvodný proces obsazení a může být hodláte použít mutex závadně. V takovém případě je zavřít popisovač a pokračovat, jako kdyby došlo k chybě při vytváření objektu doporučeného postupu zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [CSyncObject – třída](../../mfc/reference/csyncobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



