---
title: Csecurityattributes – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 47b0058cba19ac804c2d996052e9a5ec2df68bc5
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208945"
---
# <a name="csecurityattributes-class"></a>Csecurityattributes – třída
Tato třída představuje dynamického zajišťování obálku pro strukturu atributy zabezpečení.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
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
|[CSecurityAttributes::Set](#set)|Volejte tuto metodu za účelem nastavení atributů `CSecurityAttributes` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `SECURITY_ATTRIBUTES` Struktura obsahuje [popisovače zabezpečení](/windows/desktop/api/winnt/ns-winnt-_security_descriptor) používají k vytvoření objektu a určuje, zda je popisovač načíst tak, že zadáte tuto strukturu odvoditelný.  
  
 Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.  
  
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
 *rSecurityDescriptor*  
 Odkaz na popisovač zabezpečení.  
  
 *bInheritsHandle*  
 Určuje, zda Vrácený popisovač se dědí, když se vytvoří nový proces. Pokud je tento člen má hodnotu true, nový proces zdědí popisovač.  
  
##  <a name="set"></a>  CSecurityAttributes::Set  
 Volejte tuto metodu za účelem nastavení atributů `CSecurityAttributes` objektu.  
  
```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *rSecurityDescriptor*  
 Odkaz na popisovač zabezpečení.  
  
 *bInheritHandle*  
 Určuje, zda Vrácený popisovač se dědí, když se vytvoří nový proces. Pokud je tento člen má hodnotu true, nový proces zdědí popisovač.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda používá konstruktor k inicializaci `CSecurityAttributes` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka zabezpečení](../../visual-cpp-samples.md)   
 [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [Popisovač zabezpečení](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)   
 [Přehled tříd](../../atl/atl-class-overview.md)   
 [Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
