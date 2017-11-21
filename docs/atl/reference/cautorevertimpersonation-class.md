---
title: "Třída CAutoRevertImpersonation | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
dev_langs: C++
helpviewer_keywords: CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd1d14e73ecc774a8074f47383345d1accc17dc4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation – třída
Tato třída se vrátí [CAccessToken](../../atl/reference/caccesstoken-class.md) objekty do nonimpersonating stavu, když probíhá mimo rozsah.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAutoRevertImpersonation
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Vytvoří `CAutoRevertImpersonation` objektu|  
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|Odstraní objekt a vrátí token zosobnění přístup.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoRevertImpersonation::Attach](#attach)|Automatizuje zosobnění reverzním systému přístupový token.|  
|[CAutoRevertImpersonation::Detach](#detach)|Zruší reverzním automatické zosobnění.|  
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Načte aktuální tokenu přístupu přidružené k tomuto objektu.|  
  
## <a name="remarks"></a>Poznámky  
 [Přístupový token](http://msdn.microsoft.com/library/windows/desktop/aa374909) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen všem uživatelům přihlášení systému Windows NT nebo Windows 2000. Tyto tokeny přístupu může být reprezentován s `CAccessToken` třídy.  
  
 V některých případech je potřeba zosobnit tokeny přístupu. Tato třída je k dispozici pro potřeby, ale neprovádí zosobnění přístupové tokeny; provedou se jenom automatické reverzním do nonimpersonated stavu. Je to proto, že přístup pomocí tokenu zosobnění lze provést několika různými způsoby.  
  
 Úvod do model řízení přístupu v systému Windows, najdete v části [řízení přístupu](http://msdn.microsoft.com/library/windows/desktop/aa374860) ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h  
  
##  <a name="attach"></a>CAutoRevertImpersonation::Attach  
 Automatizuje zosobnění reverzním systému přístupový token.  
  
```
void Attach(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pAT`  
 Na adresu [CAccessToken](../../atl/reference/caccesstoken-class.md) objekt, který má být automaticky vrátila  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda by měla použít jen v případě [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) objekt byl vytvořen s hodnotou NULL `CAccessToken` ukazatele, nebo pokud [odpojení](#detach) volala dřív. Pro jednoduché případy není nutné k použití této metody.  
  
##  <a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation  
 Vytvoří `CAutoRevertImpersonation` objektu.  
  
```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pAT`  
 Na adresu [CAccessToken](../../atl/reference/caccesstoken-class.md) objekt, který má být automaticky vrátila.  
  
### <a name="remarks"></a>Poznámky  
 Skutečné zosobnění přístupový token musí provést samostatně z a pokud možno před vytvoření `CAutoRevertImpersonation` objektu. Tato zosobnění budou vráceny automaticky při `CAutoRevertImpersonation` opuštění rozsahu.  
  
##  <a name="dtor"></a>CAutoRevertImpersonation:: ~ CAutoRevertImpersonation  
 Odstraní objekt a vrátí token zosobnění přístup.  
  
```
~CAutoRevertImpersonation() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí všechny zosobnění aktuálně platí pro [CAccessToken](../../atl/reference/caccesstoken-class.md) zadaný buď při vytváření nebo přes objekt [připojit](#attach) metoda. Pokud žádné `CAccessToken` je spojená, destruktoru nemá žádný vliv.  
  
##  <a name="detach"></a>CAutoRevertImpersonation::Detach  
 Zruší reverzním automatické zosobnění.  
  
```
const CAccessToken* Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresu dříve přidruženého [CAccessToken](../../atl/reference/caccesstoken-class.md), nebo hodnota NULL, pokud existovaly žádné přidružení.  
  
### <a name="remarks"></a>Poznámky  
 Volání metody **odpojení** brání `CAutoRevertImpersonation` objekt z vrácení platí pro všechny zosobnění aktuálně [CAccessToken](../../atl/reference/caccesstoken-class.md) objekt přidružený k tomuto objektu. `CAutoRevertImpersonation`potom můžete být zničen bez vlivu nebo znovu přidružit do stejného nebo jiného `CAccessToken` pomocí [Attach](#attach).  
  
##  <a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken  
 Načte aktuální tokenu přístupu přidružené k tomuto objektu.  
  
```
const CAccessToken* GetAccessToken() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresu dříve přidruženého [CAccessToken](../../atl/reference/caccesstoken-class.md), nebo hodnota NULL, pokud existovaly žádné přidružení.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato metoda je volána pro účely, které zahrnují reverzním služby zosobnění `CAccessToken` objekt, [odpojení](#detach) metoda by měla být místo toho použít.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka ATLSecurity](../../visual-cpp-samples.md)   
 [Přístupové tokeny](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Přehled třídy](../../atl/atl-class-overview.md)
