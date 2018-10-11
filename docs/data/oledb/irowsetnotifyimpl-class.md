---
title: IRowsetNotifyImpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ade96e5d73d86519a067d632a4e05250d1264cf
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082303"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl – třída

Implementuje a zaregistruje [IRowsetNotify](/previous-versions/windows/desktop/ms712959) na spotřebitele (označované také jako "jímka") tak, aby se zpracování oznámení.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  

## <a name="requirements"></a>Požadavky  

**Záhlaví:** také atldbcli.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Onfieldchange –](#onfieldchange)|Upozorní příjemce všechny změny hodnoty sloupce.|  
|[OnRowChange](#onrowchange)|Upozorní příjemce změny první řádek nebo sady změn, které má vliv na celý řádek.|  
|[OnRowsetChange](#onrowsetchange)|Oznámí uživateli všechny změny, které mají vliv celá sada řádků.|  
  
## <a name="remarks"></a>Poznámky  

Zobrazit [příjem oznámení](../../data/oledb/receiving-notifications.md) o implementaci rozhraní bod připojení pro příjemce.  
  
`IRowsetNotifyImpl` poskytuje implementaci pro fiktivní `IRowsetNotify`, s prázdné funkce pro `IRowsetNotify` metody [onfieldchange –](/previous-versions/windows/desktop/ms715961), [onrowchange –](/previous-versions/windows/desktop/ms722694), a [onrowsetchange –](/previous-versions/windows/desktop/ms722669). Pokud je zděděn z této třídy při implementaci `IRowsetNotify` rozhraní, můžete implementovat pouze metody, které potřebujete. Také budete muset poskytnout prázdná implementace pro jiné metody sami.  

## <a name="onfieldchange"></a> IRowsetNotifyImpl::OnFieldChange

Upozorní příjemce všechny změny hodnoty sloupce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(OnFieldChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ HROW /* hRow */,  
/* [in] */ DBORDINAL /* cColumns */,  
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961) pro popisy parametrů.  
  
### <a name="return-value"></a>Návratová hodnota  

Zobrazit [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961) pro vrácení hodnoty popisy.  
  
### <a name="remarks"></a>Poznámky  

Tato metoda zabalí [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961) metody. Viz popis v této metodě v OLE DB programátora odkaz podrobnosti.  

## <a name="onrowchange"></a> IRowsetNotifyImpl::OnRowChange

Upozorní příjemce změny první řádek nebo sady změn, které má vliv na celý řádek.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(OnRowChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBCOUNTITEM /* cRows */,  
/* [size_is][in] */ const HROW /* rghRows*/ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694) pro popisy parametrů.  
  
### <a name="return-value"></a>Návratová hodnota  

Zobrazit [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694) pro vrácení hodnoty popisy.  
  
### <a name="remarks"></a>Poznámky  

Tato metoda zabalí [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694) metody. Viz popis v této metodě v OLE DB programátora odkaz podrobnosti. 

## <a name="onrowsetchange"></a> IRowsetNotifyImpl::OnRowsetChange

Oznámí uživateli všechny změny, které mají vliv celá sada řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(OnRowsetChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669) pro popisy parametrů.  
  
### <a name="return-value"></a>Návratová hodnota  

Zobrazit [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669) pro vrácení hodnoty popisy.  
  
### <a name="remarks"></a>Poznámky  

Tato metoda zabalí [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669) metody. Viz popis v této metodě v OLE DB programátora odkaz podrobnosti.
  
## <a name="see-also"></a>Viz také  

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959)   
[IRowsetNotifyCP – třída](../../data/oledb/irowsetnotifycp-class.md)