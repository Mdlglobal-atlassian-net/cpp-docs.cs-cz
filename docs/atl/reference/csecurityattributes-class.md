---
title: "Třída CSecurityAttributes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
dev_langs:
- C++
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 918f90c9f04736eb2328d989e21b7b9997edab86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes – třída
Tato třída je dynamické obálku pro strukturu atributy zabezpečení.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSecurityAttributes::Set](#set)|Volat tuto metodu a nastavit atributy `CSecurityAttributes` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 **SECURITY_ATTRIBUTES** struktury [popisovač zabezpečení](http://msdn.microsoft.com/library/windows/desktop/aa379561) použit pro vytvoření objektu a určuje, jestli je zděditelné popisovač načíst tak, že zadáte tuto strukturu.  
  
 Úvod do model řízení přístupu v systému Windows, najdete v části [řízení přístupu](http://msdn.microsoft.com/library/windows/desktop/aa374860) ve Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `SECURITY_ATTRIBUTES`  
  
 `CSecurityAttributes`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h  
  
##  <a name="csecurityattributes"></a>CSecurityAttributes::CSecurityAttributes  
 Konstruktor  
  
```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSecurityDescriptor`  
 Odkaz na popisovač zabezpečení.  
  
 `bInheritsHandle`  
 Určuje, jestli je vrácená popisovač zdědí při vytvoření nového procesu. Pokud je tento člen pravdivá, zdědí nový proces popisovač.  
  
##  <a name="set"></a>CSecurityAttributes::Set  
 Volat tuto metodu a nastavit atributy `CSecurityAttributes` objektu.  
  
```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSecurityDescriptor`  
 Odkaz na popisovač zabezpečení.  
  
 `bInheritHandle`  
 Určuje, jestli je vrácená popisovač zdědí při vytvoření nového procesu. Pokud je tento člen pravdivá, zdědí nový proces popisovač.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se používá konstruktorem k chybě při inicializaci `CSecurityAttributes` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka zabezpečení](../../visual-cpp-samples.md)   
 [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [Popisovač zabezpečení](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
