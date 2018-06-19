---
title: Třída IPersistStreamInitImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a51dd5e198a86b7bb17a6182c1edb098f23a8e47
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360453"
---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl – třída
Tato třída implementuje **IUnknown** a poskytuje výchozí implementaci třídy [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class ATL_NO_VTABLE IPersistStreamInitImpl 
   : public IPersistStreamInit
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IPersistStreamInitImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Načte CLSID objektu.|  
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Získá velikost datového proudu potřebné k uložení dat objektu. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicializuje nově vytvořený objekt.|  
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Kontroluje, zda dat objektu se změnil od posledního uložení.|  
|[IPersistStreamInitImpl::Load](#load)|Načte vlastnosti objektu z určeného proudu.|  
|[IPersistStreamInitImpl::Save](#save)|Vlastnosti objektu se uloží do zadaného datového proudu.|  
  
## <a name="remarks"></a>Poznámky  
 [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní, které umožňuje klienta tak, aby žádosti, objektu načítá a ukládá jeho trvalých dat do jednoho datového proudu. Třída `IPersistStreamInitImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPersistStreamInit`  
  
 `IPersistStreamInitImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getclassid"></a>  IPersistStreamInitImpl::GetClassID  
 Načte CLSID objektu.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) ve Windows SDK.  
  
##  <a name="getsizemax"></a>  IPersistStreamInitImpl::GetSizeMax  
 Získá velikost datového proudu potřebné k uložení dat objektu.  
  
```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPersistStreamInit::GetSizeMax](http://msdn.microsoft.com/library/windows/desktop/ms687287) ve Windows SDK.  
  
##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew  
 Inicializuje nově vytvořený objekt.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPersistStreamInit::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms690234) ve Windows SDK.  
  
##  <a name="isdirty"></a>  IPersistStreamInitImpl::IsDirty  
 Kontroluje, zda dat objektu se změnil od posledního uložení.  
  
```
STDMETHOD(IsDirty)();
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPersistStreamInit::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms680092) ve Windows SDK.  
  
##  <a name="load"></a>  IPersistStreamInitImpl::Load  
 Načte vlastnosti objektu z určeného proudu.  
  
```
STDMETHOD(Load)(LPSTREAM pStm);
```  
  
### <a name="remarks"></a>Poznámky  
 ATL používá mapa vlastností objektu k načtení těchto informací.  
  
 V tématu [IPersistStreamInit::Load](http://msdn.microsoft.com/library/windows/desktop/ms680730) ve Windows SDK.  
  
##  <a name="save"></a>  IPersistStreamInitImpl::Save  
 Vlastnosti objektu se uloží do zadaného datového proudu.  
  
```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```  
  
### <a name="remarks"></a>Poznámky  
 ATL používá k ukládání těchto informací mapa vlastností objektu.  
  
 V tématu [IPersistStreamInit::Save](http://msdn.microsoft.com/library/windows/desktop/ms694439) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Úložiště a datové proudy](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Přehled třídy](../../atl/atl-class-overview.md)
