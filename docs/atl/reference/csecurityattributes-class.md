---
title: Třída CSecurityAttributes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03bda174fb85fa6857e22b851b93bcf1b3192716
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357503"
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
  
##  <a name="csecurityattributes"></a>  CSecurityAttributes::CSecurityAttributes  
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
  
##  <a name="set"></a>  CSecurityAttributes::Set  
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
